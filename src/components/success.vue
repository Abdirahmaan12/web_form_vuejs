<template>
  <div class="success">
    <h1>Mahadsanid!</h1>
    <p>Form-kaaga waa la helay. Waanu kula soo xiriiri doonaa insha Allah.</p>
    <button class="success-link" @click="$emit('reset')">Ku laabo Homepage</button>
  </div>
</template>

<script>
export default {}
</script>

<style>
.success {
  max-width: 400px;
  margin: 100px auto 0 auto;
  background: #fff;
  box-shadow: 0 6px 32px rgba(0,0,0,0.09);
  border-radius: 16px;
  text-align: center;
  padding: 40px 30px 32px 30px;
  font-family: 'Segoe UI', Avenir, Arial, sans-serif;
  position: relative;
  animation: popIn 0.6s cubic-bezier(0.61, 1, 0.88, 1);
}
@keyframes popIn {
  0% { transform: scale(0.8); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}
.success h1 {
  color: #0faf87;
  margin-bottom: 16px;
  font-size: 2.2em;
  font-weight: bold;
  letter-spacing: 1px;
}
.success p {
  color: #444;
  font-size: 1.1em;
  margin-bottom: 28px;
}
.success-link {
  display: inline-block;
  padding: 11px 30px;
  border-radius: 30px;
  background: #0faf87;
  color: #fff;
  font-weight: bold;
  font-size: 1.1em;
  text-decoration: none;
  box-shadow: 0 2px 12px rgba(15, 175, 135, 0.08);
  transition: background 0.2s, transform 0.13s;
  border: none;
  cursor: pointer;
}
.success-link:hover, .success-link:focus {
  background: #09916e;
  transform: translateY(-2px) scale(1.03);
}
</style>
