<script>
  // Import components or define any props if needed
  import Navbar from '$lib/components/Navbar.svelte';

  // Sample navigation links
  const links = [
    { href: '/', text: 'Home' },
    { href: '/about', text: 'About' },
    { href: '/code', text: 'Code' },
    { href: '/signin', text: 'Sign In' }
  ];
</script>

<!-- Include the Navbar -->
<Navbar {links} />

<!-- Ensure <slot /> is included to render child pages -->
<slot />
