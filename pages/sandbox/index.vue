<template>
    <div>
        <h1>SANDBOX FRONTEND 2</h1>
        <div class="form-group">
            <input type="text" id="nama" class="form-control">
            <button class="btn btn-primary" type="submit" style="right:20px;bottom:80px;z-index:999999" @click="addList"> + </button>
            <hr>
            <p>to do list:</p>
            <hr>
            <p>list done:</p>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            list: {}
        }
    }
}
</script>