<template>
    <UDashboardGroup>
        <UDashboardSidebar resizable collapsible>
            <template #header="{ collapsed }">
                <AppLogo v-if="!collapsed" class="h-5 w-auto shrink-0" />
                <UIcon v-else name="i-simple-icons-nuxtdotjs" class="size-5 text-primary mx-auto" />
            </template>
            <template #default="{ collapsed }">
                <UNavigationMenu :collapsed="collapsed" :items="items[0]" orientation="vertical" tooltip
          popover />
                <UNavigationMenu :collapsed="collapsed" :items="items[1]" orientation="vertical" tooltip class="mt-auto" />
            </template>
        </UDashboardSidebar>
        <UDashboardPanel>
            <UDashboardNavbar title="Dashboard">
                <template #leading>
                    <UDashboardSidebarCollapse />
                </template>
                <template #trailing>
                    <!-- <UBadge label="4" variant="subtle" /> -->
                </template>
                <template #right>
                    <UColorModeButton />
                    <UButton
                        :avatar="{
                            src: 'https://github.com/benjamincanac.png',
                            size: 'lg'
                        }"
                        color="neutral"
                        variant="ghost"
                    />
                </template>
            </UDashboardNavbar>
        </UDashboardPanel>
    </UDashboardGroup>
</template>
<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items: NavigationMenuItem[][] = [[{
    label: 'Home',
    icon: 'i-lucide-house',
    active: true
}, {
    label: 'Inbox',
    icon: 'i-lucide-inbox',
    badge: '4'
}, {
    label: 'Contacts',
    icon: 'i-lucide-users'
}, {
    label: 'Settings',
    icon: 'i-lucide-settings',
    defaultOpen: true,
    children: [{
        label: 'General'
    }, {
        label: 'Members'
    }, {
        label: 'Notifications'
    }]
}], [{
    label: 'Feedback',
    icon: 'i-lucide-message-circle',
    to: 'https://github.com/nuxt-ui-templates/dashboard',
    target: '_blank'
}, {
    label: 'Help & Support',
    icon: 'i-lucide-info',
    to: 'https://github.com/nuxt/ui',
    target: '_blank'
}]]
</script>