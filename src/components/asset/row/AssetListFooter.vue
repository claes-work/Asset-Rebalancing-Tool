<template>
  <div class="asset-footer">
    <p>Gesamtsumme</p>
    <div class="wrapper">
      <span>20.000,00 €</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AssetListFooter'
}
</script>

<style scoped>
  .asset-footer {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 60px;
    background-color: var(--tertiary-background-color);
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 25px;
  }

  p, span {
    color: var(--primary-text-color);
    font-weight: 600;
    font-size: 18px;
  }
</style>