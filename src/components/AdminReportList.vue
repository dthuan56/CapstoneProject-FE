<template>
  <admin-data-table
    v-bind:columnDefs="columnDefs"
    v-bind:data="data"
    v-bind:paging="paging"
    v-bind:url="url"
  >
  </admin-data-table>
</template>

<script>
import AdminDataTable from "@/components/AdminDataTable.vue";
import axios from "axios";
export default {
  name: "AdminUserList",
  data() {
    return {
      columnDefs: null,
      data: null,
      paging: null,
      url: null,
    };
  },
  components: {
    AdminDataTable,
  },
  beforeMount() {
    let that = this;
    this.columnDefs = [
      {
        header: "STT",
        field: "id",
      },
      {
        header: "Ngày gửi",
        field: "reportedDate",
        isDate:true
      },
      {
        header: "Tên truyện",
        field: "book",
        book:true
      },
      {
        header: "Người gửi",
        field: "userSender",
        userSender:true
      },
       {
        header: "Nội dung",
        field: "reportContent",
      },
      {
        header: "Tình trạng",
        field: "statusId",
        statusId:true
      },
      {
        header: "Chi tiết",
        display: true,
        displayTT: "<button class='btn btn-primary'>Chi tiết</button>",
        action: function edit(row) {
          that.$router.push({ name: "AdminReportView" });
          that.$store.commit("setBookId", row.id);
        },
      },
      {
        header: "Phản hồi",
        isstatusIdRP: true,
        field: "statusId",
        fieldTrue: "",
        fieldFalse: "<button class='btn btn-primary'>Phản hồi</button>",
        action: function approved(row) {
          that.$router.push({ name: "AdminReportResponse" });
          that.$store.commit("setBookId", row.id);
        },
      },
    ];
    this.paging = {
      page: 0,
      pageSize: 10,
      sortField: "id",
      sortOrder: "des",
      searchKeyword:"",
      issearchKeyword:true
    };
    this.url = "admin/reportListAdmin";
  },
};
</script>

<style>
.search-form {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    margin-bottom: 2rem;
}

.form-search-field {
    width: 20%;
    height: 3rem;
    border-radius: 3rem;
    border: none;
    padding-right: 5rem;
    padding-left: 2rem;
    background-color: #e0e0e0;
    vertical-align: baseline;
}

.form-search-button {
    position: absolute;
    right: 2rem;
    border: none;
    background-color: transparent;
    height: 3rem;
    width: 4rem;
}
</style>