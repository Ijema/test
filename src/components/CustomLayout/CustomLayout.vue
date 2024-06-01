<template>
  <n-layout has-sider>
    <n-layout-sider bordered>
      <div>
        <!-- <img src="../../assets/book.jpg" alt="" /> -->
      </div>
      <div class="sider-title">
        <div>
          <p>Student Data</p>
        </div>
        <div>
          <p>Activity Report</p>
        </div>
        <div>
          <p>Finance Data</p>
        </div>
        <div>
          <p>Logout</p>
        </div>
      </div>
    </n-layout-sider>
    <n-layout>
      <n-layout-header bordered>
        <div class="header">
          <div class="header-img">
            <!-- <img src="../../assets/book.jpg" alt=""  /> -->
            <div>
            <p><b>Prof John Doe</b></p>
            <p>JD@unizik.edu.ng</p>
            </div>
          </div>
          <div>
            <p>Active Session: <b>2023/2024</b></p>
          </div>
          <div>
            <p>Active Semester: <b>First Semester</b></p>
          </div>
        </div>
      </n-layout-header>
      <n-layout-content content-style="padding: 5px 24px;">
        <slot></slot> <!-- Use slot to render children -->
      </n-layout-content>
      <n-layout-footer bordered>
        Chengfu Road
      </n-layout-footer>
    </n-layout>
  </n-layout>
</template>

<script setup>
import { NLayout, NLayoutSider, NLayoutHeader, NLayoutContent, NLayoutFooter } from 'naive-ui';
import '../CustomLayout/CustomLayout.css';
</script>


