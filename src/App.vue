<script setup>
import { saveAs } from 'file-saver';
import * as XLSX from 'xlsx';
import { ref } from 'vue';

const jsonData = ref([]);

function handleFileUpload(event) {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = (e) => {
      try {
        const json_Data = JSON.parse(e.target.result);
        for (const [key, value] of Object.entries(json_Data)) {
          jsonData.value.push({
            key,
            value,
          });
        }
      }
      catch (error) {
        console.error('Invalid JSON file:', error);
      }
    };
    reader.readAsText(file);
  }
}

function exportToExcel() {
  if (!jsonData.value) {
    alert('No data to export!');
    return;
  }

  const worksheet = XLSX.utils.json_to_sheet(jsonData.value);
  const workbook = XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(workbook, worksheet, 'Sheet1');

  const excelBuffer = XLSX.write(workbook, { bookType: 'xlsx', type: 'array' });
  const blob = new Blob([excelBuffer], { type: 'application/octet-stream' });
  saveAs(blob, 'exported-data.xlsx');
}
</script>

<template>
  <div>
    <input type="file" @change="handleFileUpload">
    <button class="button" @click="exportToExcel">
      Export to Excel
    </button>
    <div v-if="jsonData.length" class="pre-container">
      <pre>{{ jsonData }}</pre>
    </div>
  </div>
</template>
