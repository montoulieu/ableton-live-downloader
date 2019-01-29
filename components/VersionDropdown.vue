<template>
  <div class="form-group mr-5 mb-2">
    <label for="inputVersion" class="mr-3 text-uppercase font-weight-bold">Version</label>
    <select id="inputVersion" class="form-control">
      <option selected>Choose...</option>
      <option v-for="version in versions" :key="version.id">{{ version }}</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      versions: [
        '10.0.6',
        '10.0.5',
        '10.0.4',
        '10.0.3',
        '10.0.2',
        '10.0.1',
        '10.0',
        '9.7.7',
        '9.7.6',
        '9.7.5',
        '9.7.4',
        '9.7.3',
        '9.7.2',
        '9.7.1',
        '9.7',
        '9.6.2',
        '9.6.1',
        '9.6',
        '9.5',
        '9.2.3',
        '9.2.2',
        '9.2.1',
        '9.2',
        '9.1.10',
        '9.1.9',
        '9.1.8',
        '9.1.7',
        '9.1.6',
        '9.1.5',
        '9.1.4',
        '9.1.3',
        '9.1.2',
        '9.1',
        '9.0.6',
        '9.0.5',
        '9.0.4',
        '9.0.3',
        '9.0.2',
        '9.0.1',
      ]
    }
  }
}
</script>
