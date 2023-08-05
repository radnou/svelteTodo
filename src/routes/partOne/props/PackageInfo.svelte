<script lang="ts">
    export let name:string;
    export let version:string;
    export let speed:string;
    export let website:string;

    $: href = `https://www.npmjs.com/package/${name}`;

</script>

<p>
    the <code>{name}</code> package is {speed} fast. Download version {version} from <a {href} target="_blank" class="link link-info">npm</a> and <a href={website}>learn more here</a>

</p>