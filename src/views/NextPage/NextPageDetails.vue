<template>
    <div class="app">
        <!-- Navigation Header -->
        <div class="header">
            <el-button type="primary" plain @click="handleGoBack()">Go Back</el-button>
            <h2>get to know me</h2>
        </div>

        <div class="details-container">
            <!-- Hobbies Section -->
            <el-card class="section-card">
                <template #header>
                    <div class="card-title">
                        <span>My Hobbies</span>
                    </div>
                </template>
                <div class="hobbies-list">
                    <el-tag 
                        v-for="hobby in hobbies" 
                        :key="hobby" 
                        type="success" 
                        effect="light"
                        size="medium"
                    >
                        {{ hobby }}
                    </el-tag>
                </div>
            </el-card>

            <!-- Achievements Section -->
            <el-card class="section-card">
                <template #header>
                    <div class="card-title">
                        <span>Achievements</span>
                    </div>
                </template>
                <el-timeline>
                    <el-timeline-item
                        v-for="(achievement, index) in achievements"
                        :key="index"
                        :timestamp="achievement.year"
                        type="primary"
                    >
                        <h4>{{ achievement.title }}</h4>
                        <p>{{ achievement.description }}</p>
                    </el-timeline-item>
                </el-timeline>
            </el-card>
        </div>
    </div>
</template>

<script>
export default {
    name: "NextPageDetails",
    components: {},
    data() {
        return {
            // Hobbies list
            hobbies: [
                "watching formula 1 races",
                "playing the bass guitar",
                "building lego sets",
                "watching movies"
            ],
            // Achievements list
            achievements: [
                {
                    year:"2026",
                    title: "my first job",
                    description: "started my first job @ AHAM asset management as a learning executive."
                },
                {
                    year:"2025",
                    title:" got my first car"

                },
                {
                    year: "2025",
                    title: "snouts and stripes",
                    description: "student led organization for tapir conservation"
                },
                {
                    year: "2024",
                    title: "eco champions awards",
                    description: "competed against 30 teams for a conservation project, and was selected as the top 10 teams"
                },
                {
                    year: "2024",
                    title: "dean's list",
                    description: "achieved dean's list"
                }
            ]
        };
    },
    methods: {
        handleGoBack() {
            this.$router.back(-1);
        }
    },
};
</script>

<style lang="scss" scoped>
.app {
    padding: 24px;
    max-width: 800px;
    margin: 0 auto;
}

.header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 24px;

    h2 {
        margin: 0;
        color: #2c3e50;
    }
}

.details-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.section-card {
    border-radius: 8px;

    .card-title {
        font-weight: bold;
        font-size: 1.1rem;
    }
}

.hobbies-list {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
}

.el-timeline {
    padding-left: 10px;

    h4 {
        margin: 0 0 4px 0;
        color: #303133;
    }

    p {
        margin: 0;
        color: #606266;
        font-size: 0.9rem;
    }
}
</style>