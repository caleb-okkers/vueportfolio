<template >
    <div class="timeline">
  <div class="timeline-container left">
    <div class="content">
      <h2>Education</h2>
      <p>Details about your education.</p>
    </div>
  </div>
  <div class="timeline-container right">
    <div class="content">
      <h2>Work Experience</h2>
      <p>Details about your work experience.</p>
    </div>
  </div>
  <div class="timeline-container left">
    <div class="content">
      <h2>Education</h2>
      <p>Details about another education experience.</p>
    </div>
  </div>
  <div class="timeline-container right">
    <div class="content">
      <h2>Work Experience</h2>
      <p>Details about another work experience.</p>
    </div>
  </div>
</div>
</template>
<script>
export default {
    name: "ResumeSection"
}
</script>
<style scoped>
.timeline {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 0;
}

.timeline::after {
  content: '';
  position: absolute;
  width: 6px;
  background-color: #007bff;
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -3px;
}

.timeline-container {
  padding: 10px 40px;
  position: relative;
  background-color: inherit;
  width: 50%;
}

.timeline-container.left {
  left: 0;
}

.timeline-container.right {
  left: 50%;
}

.timeline-container::after {
  content: ' ';
  position: absolute;
  width: 25px;
  height: 25px;
  right: -17px;
  background-color: white;
  border: 4px solid #007bff;
  top: 15px;
  border-radius: 50%;
  z-index: 1;
}

.timeline-container.right::after {
  left: -16px;
}

.content {
  padding: 20px 30px;
  background-color: white;
  position: relative;
  border-radius: 6px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.timeline-container.left .content {
  left: 0;
}

.timeline-container.right .content {
  left: -100%;
}
</style>