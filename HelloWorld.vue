<template>
<div id="comment_app" class="container">
    <div class="navbar navbar-default">
        <div class="navbar-header">
            <a class="navbar-brand">Comments App</a>
        </div>
        <div class="navbar-collapse collapse">
            <ul class="navbar-right navbar-nav nav">
                <li>
                    <a href="#">{{total_comments}} Comments</a>
                </li>
            </ul>
        </div>
    </div>
    <div>
        <div class="row">
            <!-- form -->
            <form class="col-sm-4 col-sm-offset-4" v-on:submit.prevent='submit'>
                <h3>Create Comments</h3>
                <div class="form-group">
                    <textarea required="required" placeholder="Your comment" v-model='input' class="form-control"></textarea>
                </div>
                <button class="btn btn-info">Create</button>
                <br />
                <br />
                <legend></legend>
            </form>
            <!-- form -->
            <div class="cols-m-12">
                <div class="col-sm-4 col-sm-offset-4">
                    <div v-if='total_comments == 0'>
                        <div class="alert alert-info">
                            No Comments
                        </div>
                    </div>
                    <div class="list-group">
                        <div class="list-group-item" v-for="comment,index in comments">
                            <p><b>Comment: </b> {{comment.comment}}</p>
                            <p>
                                <strong>Total Likes:</strong>
                                {{comment.total_likes}}
                            </p>
                            <p>
                                <button v-on:click='like(index)' class="btn btn-xs btn-info">Like</button>
                            </p>
                            <h5>Replies</h5>
                            <div class="list-group">
                                <div class="list-group-item" v-for='reply,index in comment.replies'>
                                    <p>
                                        <strong>reply:</strong> {{reply.reply}}
                                    </p>
                                </div>
                                <div class="list-group-item" style="padding: 00;">
                                    <form v-on:submit.prevent='addReply(index)'>
                                        <input v-model='reply' placeholder="reply" class="form-control" />
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props: {
        msg: String
    }}
  
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}

.navbar {
    border-radius: 0;
}

.navbar-header {
    float: none;
    width: 200px;
    margin: auto;
    position: absolute;
    left: 0;
    right: 0;
    text-align: center;
    height: 50px;
}

.navbar-brand {
    float: none;
    line-height: 50px;
}
</style>
