<template>
    <section class="outer-container">
        <article class="content-box" role="article" aria-labelledby="content-box-title">
            <p class="section-title" id="content-box-title">EVEN MORE SAVINGS</p>
            <div class="inner-content">
                <p class="advertorial" aria-label="Advertorial">ADVERTORIAL</p>
                <h2 class="headline" aria-label="Headline of the article">Tricks Homeowners Use to Eliminate Bills</h2>
                <p class="description">
                    Surging energy bills, unpredictable weather patterns and dissatisfaction with utility companies have
                    homeowners scrambling...
                </p>
                <a class="read-more" href="https://www.google.com" target="_blank" rel="noopener noreferrer" 
                   @click="handleReadMore" aria-label="Read more about tricks to eliminate bills">
                    READ MORE
                </a>
            </div>
        </article>
    </section>
</template>

<script setup>
const handleReadMore = (event) => {
    event.preventDefault();
    window.open('https://www.google.com', '_blank', 'toolbar=0,location=0,menubar=0,resizable=1');
};
</script>

<style scoped>
.outer-container {
    margin: 0px auto 24px auto;
    width: 40%;
    min-width: 404px;
    min-height: 262px;
    background: transparent;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
}

.content-box {
    width: 100%;
    height: 100%;
    border: 2px solid #A0BC57;
    border-top: none;
    position: relative;
    padding: 20px;
    background: transparent;
    overflow: visible;
}

.content-box::before,
.content-box::after {
    content: "";
    position: absolute;
    top: 0;
    height: 2px;
    background: #A0BC57;
    z-index: 2;
}

.content-box::before {
    left: 0;
    right: 60%;
    margin-right: 80px;
}

.content-box::after {
    right: 0;
    left: 60%;
    margin-left: 80px;
}

.section-title {
    position: absolute;
    top: -20px;
    left: 50%;
    transform: translateX(-50%);
    font-weight: bold;
    font-size: 12px;
    color: #666;
    letter-spacing: 1px;
    z-index: 5;
    background: transparent;
    padding: 0 8px;
    white-space: nowrap;
}

.inner-content {
    background: rgba(255, 255, 255, 0.7);
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.advertorial {
    font-size: 12px;
    font-weight: bold;
    color: #A0BC57;
    margin: 0;
}

.headline {
    font-size: 18px;
    font-weight: bold;
    margin: 0;
    color: #333;
}

.description {
    font-size: 14px;
    color: #555;
    margin: 0;
}

.read-more {
    font-size: 14px;
    font-weight: bold;
    color: #3498db;
    text-decoration: none;
    margin-top: auto;
}

.read-more:hover {
    text-decoration: underline;
}

@media (max-width: 767px) {
    .outer-container {
        width: 90%;
        min-width: unset;
        padding: 10px;
        margin: 16px auto 72px auto;
    }

    .content-box {
        padding: 16px;
    }

    .section-title {
        font-size: 10px;
        top: -14px;
        padding: 0 6px;
    }

    .inner-content {
        padding: 16px;
        gap: 10px;
    }

    .advertorial {
        font-size: 10px;
    }

    .headline {
        font-size: 16px;
    }

    .description {
        font-size: 13px;
    }

    .read-more {
        font-size: 13px;
    }
}
</style>
