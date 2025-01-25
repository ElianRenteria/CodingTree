<script>
  // Import components or define any props if needed
  import Navbar from '$lib/components/Navbar.svelte';
  import 'iconify-icon';
  // Sample navigation links
  const links = [
    { href: '/', text: 'Home', icon: 'mdi:home' },
    { href: '/java', text: 'Java', icon: 'mdi:language-java' },
    { href: '/pygame', text: 'Pygame', icon: 'mdi:gamepad-variant' },
    { href: '/python', text: 'Python', icon: 'mdi:language-python' },
    { href: '/signin', text: 'Sign In', icon: 'mdi:login' }
  ];
</script>

<!-- Include the Navbar -->
<Navbar {links} />

<!-- Ensure <slot /> is included to render child pages -->
<slot />

<style lang="scss">@import '../styles/style.scss';</style>
