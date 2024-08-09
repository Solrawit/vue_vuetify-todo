<template>
  <v-app>
    <v-app-bar app color="green-accent-2">
      <v-app-bar-title>Vue Todo</v-app-bar-title>
    </v-app-bar>
    <br>
    <br>
    <br>
    <v-content>
      <v-container>
        <v-card>
          <v-card-text>
            <v-text-field v-model="newText"
            solo label="กรอกข้อความ" append-icon="mdi mdi-plus" @click:append="addItem()">
            </v-text-field>
          </v-card-text>

          <v-list>
            <v-list-item v-for="(item, index) in items" :key="index">
              <v-list-item-action>
                <v-icon>mdi mdi-account-tie-outline</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>{{ item }}</v-list-item-title>
              </v-list-item-content>
              <v-list-item-action>
                <v-btn @click="deleteItem(index)" color="blue">ลบ</v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list>
        </v-card>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  export default {
    name: 'App',
    data: () => ({
      items: ['ไปเที่ยว', 'ดูหนัง', 'ฟังเพลง'],
      newText: ''
    }),
    mounted() {
    document.title = "Vue Todo - My Website"; // เพิ่มบรรทัดนี้เพื่อกำหนด Title
  },
    methods: {
      deleteItem(index) {
        this.items.splice(index,1);
      },
      addItem() {
        this.items.push(this.newText);
        this.newText = '';
      }
    }
  };
</script>
