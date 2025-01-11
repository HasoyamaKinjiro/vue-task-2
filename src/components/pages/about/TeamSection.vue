<script setup lang="ts">
const teamMembers = [
  {
    name: "Alice Johnson",
    role: "CEO",
    description:
      "Alice is a visionary leader with over 15 years of experience in the industry. She is passionate about driving innovation and fostering a collaborative work environment.",
  },
  {
    name: "Bob Smith",
    role: "CTO",
    description:
      "Bob is a tech enthusiast who specializes in software architecture and emerging technologies. He ensures our systems are robust and scalable.",
  },
  {
    name: "Charlie Brown",
    role: "Designer",
    description:
      "Charlie brings creativity to life through exceptional designs. With a keen eye for detail, he ensures our products are both functional and aesthetically pleasing.",
  },
];
</script>

<template>
  <div class="team-section">
    <ul>
      <li v-for="member in teamMembers" :key="member.name">
        <h3>{{ member.name }}</h3>
        <p><strong>{{ member.role }}</strong></p>
        <p>{{ member.description }}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.team-section {
  text-align: center;
}

.team-section ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.team-section li {
  min-width: 200px;
  width: 100%;
  margin-bottom: 1rem;
  padding: 1rem;
  background: #289a74;
  border: 1px solid #ddd;
  border-radius: 8px;
  color: #dedede;
}

.team-section h3 {
  margin: 0 0 0.5rem;
}

.team-section p {
  margin: 0.5rem 0 0;
}

.team-section p strong {
  font-weight: bold;
}
</style>
