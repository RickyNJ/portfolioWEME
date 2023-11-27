<script lang="ts">

     export let imageid: string
    $: imageUrl = "D:\Code\portfolioWEME\src\resources\pictures\weme"+ imageid + ".jpg";
</script>

<div id="img-container">
    <img src={imageUrl} alt="person"/>
</div>

<style>

</style>