<template>
        <div class="comment-block">       
                <router-link :to="'/books?id=' + comment.book.id">{{comment.book.name}}</router-link>
                
                <!-- <b>{{ comment.user.id }}</b> -->
                <!-- <a href="#" class="novel-name-comment">Ten truyen</a> -->
                <div class="c-comment" v-html="comment.content"></div>
                <!-- <p class="comment-p">Truyen nay hay qua</p> -->
            <div class="name-user-comment">
                <!-- <a href="#">Ten nguoi</a> -->
            <router-link :to="'/account?userId=' + comment.user.id" style="font-size: 12px">{{comment.user.name}}</router-link>
                <!-- <p class="comment-p">{{ moment(new Date(comment.startedDate)).fromNow() }}</p> -->
                <p class="comment-p">{{ moment(comment.startedDate) }}</p>
                <!-- <p class="comment-p">{{comment.startedDate}}</p> -->
                <!-- <p class="comment-p">{{dateTime}}</p> -->
            </div>
        </div>
</template>
<script>
import moment from 'moment';
//    var today = new Date();
//    var date = today.getDate()+'-'+(today.getMonth()+1)+'-'+today.getFullYear();
//    var time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
//    var dateTime = date+' '+time;
    export default {
        name: "CommentInHomeBlock",
        props: ["comment"],
        comments: {
            user: null,
            content: "",
        },
        methods: {
           moment: function (date) {
            return moment(new Date(date)).fromNow();
          }
        },
        computed: {
          format(date) {
            return moment(date).fromNow();
          }
        }
    }
</script>
<style scoped>
.comment-block {
    /* position: relative; */
    margin-bottom: 3px;
    border-bottom: 1px solid #dbded5;
    padding: 10px 15px;
    display: grid;
}
.comment-block a{
    text-overflow: ellipsis;
    overflow: hidden;
    font-weight: bold;
    color: black;
    font-size: 15px;
    display: inline-block;
    white-space: nowrap;
}
.comment-block span{
    padding: 5px 0px;
}
.name-user-comment {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    font-size: 15px;
    
}
.novel-name-comment{
    font-size: 17px;
    font-weight: bold;
}
.comment-p{
    font-size: 10px;
    padding: 3px 5px;
}
.c-comment {
    font-size: 12px;
    margin: 10px 0;
}
</style>