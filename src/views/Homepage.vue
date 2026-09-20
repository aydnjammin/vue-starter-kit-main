<template>
    <div class="app">
        <!-- Container holding the image and overlay -->
        <div class="banner-container">
            <!-- Background Image -->
            <img src="@/assets/images/page.jpeg" alt="Page image" class="banner-img" />

            <!-- Profile Overlay -->
            <div class="profile">
                <p class="about-me-text">about me</p>
                <div class="grp-btn">
                    <el-button type="primary" plain @click="showPopup = true">what would you like to know?</el-button>
                    <el-button type="primary" @click="handleNextPage()">lets go!</el-button>
                </div>
            </div>
        </div>
       
        <Base-Popup 
            :visible="showPopup"
            title="curious huh?"
            message="click the other button ---->"
            @close-popup="closePopup"
        />
    </div>
</template>

<script>
export default {
    name: "Dashboard",
    components: {},
    data() {
        return {
            showPopup: false,
        };
    },
    methods: {
        closePopup() {
            this.showPopup = false;
        },
        handleNextPage() {
            this.$router.push({ path: '/next-page' });
        }
    },
};
</script>

<style lang="scss" scoped>
.banner-container {
    position: relative;
    width: 100%;
    max-width: 900px;
    margin: 0 auto;

    .banner-img {
        width: 100%;
        height: auto;
        display: block;
        border-radius: 8px;
    }

    .profile {
        position: absolute;
        top: 50%;
        right: 100px;
        transform: translateY(-50%);
        padding: 20px;
        background-color: rgba(0, 0, 0, 0);
        border-radius: 8px;

        .about-me-text {
            color: #ffffff; 
            font-size: 1.5rem;
            font-weight: bold;
            margin-top: 0;
            margin-bottom: 12px;
        }

        .grp-btn {
            display: flex;
            gap: 10px;
        }
    }
}

/* ============================================================
   MOBILE RESPONSIVE STYLES (Tablet & Mobile devices <= 768px)
   ============================================================ */
@media (max-width: 768px) {
    .banner-container {
        /* On mobile, remove absolute overlay so content doesn't overflow */
        display: flex;
        flex-direction: column;

        .profile {
            position: static; /* Takes profile out of absolute positioning */
            transform: none;
            width: 100%;
            padding: 16px 0;
            text-align: center;

            .about-me-text {
                color: #303133; /* Changes white text to dark so it's readable off the image */
                font-size: 1.25rem;
            }

            .grp-btn {
                flex-direction: column; /* Stacks buttons vertically on narrow screens */
                width: 100%;

                .el-button {
                    width: 100%; /* Full width buttons for mobile touch targets */
                    margin-left: 0; /* Clears default Element UI button margins */
                }
            }
        }
    }
}
</style>