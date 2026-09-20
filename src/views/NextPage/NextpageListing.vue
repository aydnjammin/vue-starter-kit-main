<<template>
    <div class="app">
        <div class="buttons">
            <el-button type="primary" plain @click="handleGoBack()">time travel</el-button>
            <el-button type="primary" @click="handleNextPage">go to next page</el-button>
        </div>

        <el-card class="about-card">
            <div class="profile-header">
                <el-avatar :size="60" :src="avatar"></el-avatar>
                <div>
                    <h2>for me to know</h2>
                    <p class="subtitle">trainer trying to upskill</p>
                </div>
            </div>

            <el-divider></el-divider>

            <p>doing this to learn new things and gain more skills</p>

            <h3>skills</h3>
            <div class="contact">
                <el-tag type="primary">email: ca.nurzahid@gmail.com</el-tag>
                <el-tag type="success">canva</el-tag>
                <el-tag type="warning">a bit of java</el-tag>
                <el-tag type="info">presentation skills</el-tag>
            </div>
        </el-card>
    </div>
</template>

<script>
import avatar from "@/assets/images/pfp.jpeg"
export default {
    name: "NextPageListing",
    components: {},
    data() {
        return {
            avatar,
        };
    },
    methods: {
        handleNextPage() {
            this.$router.push({ path: '/next-page/details' });
        },
        handleGoBack() {
            this.$router.back(-1);
        }
    },
};
</script>

<style scoped>
.app {
    padding: 20px;
}

.buttons {
    margin-bottom: 20px;
}

.about-card {
    max-width: 600px;
}

.profile-header {
    display: flex;
    align-items: center;
    gap: 16px;
}

.profile-header h2 {
    margin: 0;
}

.subtitle {
    margin: 4px 0 0 0;
    color: #769ae1;
}

.skills {
    display: flex;
    gap: 8px;
}
</style>