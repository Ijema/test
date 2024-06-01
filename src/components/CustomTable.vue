<template>
    <h2>Activity Report</h2>
    <div class="report-summary">
      <div>
        <img :src="ReportIcon1" alt="" />
        <p class="report-summary-report-number"><b>0</b></p>
      </div>
      <div>
        <img :src="ReportIcon2" alt="" />
        <p class="report-summary-report-number"><b>0</b></p>
      </div>
      <div>
        <img :src="ReportIcon3" alt="" />
        <p class="report-summary-report-number"><b>0</b></p>
      </div>
      <div>
        <img :src="ReportIcon4" alt="" />
        <p class="report-summary-report-number"><b>0</b></p>
      </div>
    </div>
  
    <div class="search">
        <div>
            <n-dropdown trigger="hover" placement="bottom-start" :options="options" @select="handleSelect" :show-arrow="true" width="480%">

            <n-button class="dropdown-button" style="width: 350%;">Select the activity
            <img :src="Arrow" alt="" :class="show === true ? 'n-button-flip-arrow' : ''" />
            </n-button>

        </n-dropdown>
      </div>
      <div class="search-search-date">
        <div>
          <n-date-picker v-model:value="timestamp" type="date" />
        </div>
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 20 20" width="30px" height="20px">
          <g fill="none">
            <path d="M12.146 3.146a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1 0 .708l-3 3a.5.5 0 0 1-.708-.708L14.293 7H4.5a.5.5 0 0 1 0-1h9.793l-2.147-2.146a.5.5 0 0 1 0-.708zm-4.292 7a.5.5 0 0 1 0 .708L5.707 13H15.5a.5.5 0 0 1 0 1H5.707l2.147 2.146a.5.5 0 0 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 0 1 .708 0z" fill="currentColor"></path>
          </g>
        </svg>
        <div>
          <n-date-picker v-model:value="timestamp" type="date" />
        </div>
      </div>
    </div>
  
    <n-space vertical :size="12">
      <n-data-table
        :bordered="false"
        :single-line="false"
        :columns="columns"
        :data="data"
        :pagination="pagination"
        @update:sorter="handleSorterChange"
        :header-cell-style="{ backgroundColor: 'blueviolet', color: 'white' }"
      />
    </n-space>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { useMessage } from 'naive-ui';
  import { NDataTable, NSpace, NDropdown, NButton, NDatePicker } from 'naive-ui';
  import ReportIcon1 from '../assets/ReportIcon1.svg';
  import ReportIcon2 from '../assets/ReportIcon2.svg';
  import ReportIcon3 from '../assets/ReportIcon3.svg';
  import ReportIcon4 from '../assets/ReportIcon4.svg';
  import Arrow from '../assets/ArrowIcon.svg'


  const show = ref(false)
  
  const createColumns = () => [
    {
      title: 'Faculty',
      key: 'faculty',
      sorter: 'default',
      sortOrder: null,
    },
    {
      title: 'Number of Department',
      key: 'numOfDept',
      sorter: (rowA, rowB) => rowA.numOfDept - rowB.numOfDept,
      sortOrder: null,
    },
    {
      title: 'Number of Uploaded Courses',
      key: 'numOfUploadedCourses',
      sorter: (rowA, rowB) => rowA.numOfUploadedCourses - rowB.numOfUploadedCourses,
      sortOrder: null,
    },
    {
      title: 'Number of Profiled Courses',
      key: 'numOfProfiledCourses',
      sorter: (rowA, rowB) => rowA.numOfProfiledCourses - rowB.numOfProfiledCourses,
      sortOrder: null,
    },
  ];
  
  const createData = () => [
    { key: 0, faculty: 'Applied Biochemistry', numOfDept: 38, numOfUploadedCourses: 10, numOfProfiledCourses: 11 },
    { key: 1, faculty: 'Chemical Engineering', numOfDept: 42, numOfUploadedCourses: 30, numOfProfiledCourses: 22 },
    { key: 2, faculty: 'Pure and Industrial Chemistry', numOfDept: 36, numOfUploadedCourses: 15, numOfProfiledCourses: 12 },
    { key: 3, faculty: 'Statistics', numOfDept: 32, numOfUploadedCourses: 25, numOfProfiledCourses: 34 },
  ];
  
  const data = ref(createData());
  const pagination = ref({ pageSize: 5 });
  const columns = ref(createColumns());
  
  const options = [
    {
      label: 'Course Allocations',
      key: 'Course Allocations',
    }
   
  ];
  
  const message = useMessage();
  
  const handleSelect = (key) => {
    message.info(String(key));
  };
  
  const timestamp = ref(118313526e4);
  </script>
  
  <style scoped lang="scss">
.template {
  width: 993px;
  height: 465px;
  top: 176px;
  left: 312px;
  gap: 25px;
  opacity: 0px;
}

.n-data-table th {
  background: #925FE2;
  color: white;
}

.report-summary {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.report-summary div {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

.report-summary-report-number {
  margin-top: -8px;
  padding-bottom: 10px;
  font-size: 25px;
}

.n-button {
  width: auto;
  gap: 0px;
  text-align: left;

  & img{
    width: 15px;
    height: 15px;
    margin-left: 50px;
  }
  &-flip-arrow{
    transform: rotate(180deg);
  }
}

.search {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;

  &-search-date {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  @media (max-width: 1280px){
    .n-button{
        width: 200% !important;
    }
    .n-dropdown{
        width: 100% !important;
        background-color: red;
    }
  }
  @media (max-width: 1180px){
    .n-button{
        width: 150% !important;
    }
    .n-dropdown{
        width: 100% !important;
        background-color: red;
    }
  }
  @media (max-width: 1100px){
    .n-button{
        width: 115% !important;
    }
    .n-dropdown{
        width: 100% !important;
        background-color: red;
    }
  }
}
</style>