<template>
  <div class="review-card">
    <div class="review-content">
      Graphic Design, Motion Design, Print Design, UX/UI. Graphic Design, Motion Design, Print Design, UX/UI and more<br><br>
      Graphic Design, Motion Design, Print Design, UX/UI and more
    </div>
    <div class="review-footer">
      <span class="review-author">Anton Proskurin</span>
      <span class="review-avatar"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ReviewCard',
};
</script>

<style scoped>
.review-card {
  width: 360px;
  height: 360px;
  background: #FDFDFD;
  box-shadow: 3px 8px 27px rgba(171, 111, 97, 0.20);
  border-radius: 20px;
  padding: 46px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  gap: 10px;
}
.review-content {
  font-size: 1rem;
  color: var(--color-text);
  flex: 1 1 auto;
}
.review-footer {
  display: flex;
  align-items: center;
  gap: 8px;
}
.review-author {
  font-size: 1rem;
  color: var(--color-text);
}
.review-avatar {
  width: 15px;
  height: 15px;
  background: #313131;
  border-radius: 9999px;
  display: inline-block;
}
</style> 