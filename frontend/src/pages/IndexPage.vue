<template>
  <q-page class="q-pa-md">
    <!-- ... ส่วนเนื้อหาหน้าเดโมเดิม ... -->

    <q-card class="q-mt-md shadow-2">
      <q-card-section class="bg-primary text-white">
        <div class="text-h6">Docker Quick Reference</div>
        <div class="text-subtitle2">คำสั่ง Docker และ Docker Compose ที่ใช้บ่อยในโปรเจกต์</div>
      </q-card-section>

      <q-separator />

      <q-list bordered separator>
        <q-item v-for="(item, index) in dockerCommands" :key="index" class="q-py-md">
          <q-item-section>
            <q-item-label class="text-subtitle1 text-weight-bold">
              <code>{{ item.command }}</code>
            </q-item-label>
            <q-item-label caption class="text-body2 text-grey-8 q-mt-xs">
              {{ item.description }}
            </q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-card>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const dockerCommands = ref([
  {
    command: 'docker compose up -d --build',
    description:
      'ใช้เมื่อต้องการสร้าง (build) image ใหม่ตาม Dockerfile หรือ compose ล่าสุด และรัน container แบบ background (-d) เหมาะหลังแก้โค้ดหรือปรับคอนฟิก'
  },
  {
    command: 'docker compose ps',
    description:
      'ใช้ตรวจสอบสถานะของ service และ container ที่รันอยู่ภายใต้ Docker Compose รวมถึงพอร์ตที่แมปไว้ เช่น พอร์ต 8080 ของ frontend'
  },
  {
    command: 'docker compose config',
    description:
      'ใช้ตรวจสอบและแสดงค่าคอนฟิกสุดท้ายของไฟล์ compose หลังรวมค่าและแก้พาธ context/env แล้ว เพื่อเช็กว่าไม่มีจุดผิดพลาดก่อนสั่งรัน'
  },
  {
    command: 'docker compose down',
    description:
      'ใช้หยุดและลบ container รวมถึง network ที่สร้างโดย Docker Compose เมื่อต้องการปิดสภาพแวดล้อมทดสอบหรือเคลียร์เครื่อง'
  },
  {
    command: 'docker compose logs -f frontend',
    description:
      'ใช้ดู log แบบเรียลไทม์ของบริการ frontend เพื่อตรวจสอบการทำงานหรือหาสาเหตุเมื่อ container ทำงานผิดปกติ'
  }
])
</script>
