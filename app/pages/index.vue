<template>
    <UDashboardPanel>
        <template #header>
            <UDashboardNavbar :ui="{ title: 'flex-col items-start justify-center gap-0' }">
                <template #title>
                    Mindanao State University
                    <div class="font-normal text-sm text-dimmed">
                        Tawi-Tawi Campus
                    </div>
                </template>
                <template #leading>
                    <UColorModeImage light="/img/msu-logo.png" dark="/img/msu-logo.png" :width="50" :height="50" />
                </template>

                <template #right>
                    
                    <UDropdownMenu :items="items" :ui="{
                        content: 'w-48'
                    }">
                        <UAvatar src="https://github.com/benjamincanac.png" size="lg" />
                        <template #color-mode-trailing>
                            <UColorModeSwitch />
                        </template>
                    </UDropdownMenu>
                </template>
            </UDashboardNavbar>
        </template>
        <template #body>
            <UPageSection title="Coastal Monitoring Center"
                description="Comprehensive dashboard suite for research data management, environmental monitoring, and community extension services">
                <div class="w-full grid grid-cols-2 content-start gap-8">
                    <UCard v-for="module in [
                        { title: 'Coastal Monitoring System', description: 'Real-time environmental data visualization and alerts', icon: 'i-lucide-radio-tower' },
                        { title: 'Fisheries & Oceanography Data Management', description: 'Experimental research data management and analysis', icon: 'i-lucide-fish' },
                        { title: 'Research Information Management', description: 'Research outputs, metrics, and researcher databases', icon: 'i-lucide-flask-conical' },
                        { title: 'Extension Services Management', description: 'Community extension programs and impact tracking', icon: 'i-lucide-anchor' }
                    ]">
                        <UPageFeature orientation="vertical" :title="module.title" :description="module.description">
                            <template #leading>
                                <UAvatar size="3xl" :icon="module.icon" class="rounded-none squircle" :ui="{
                                    root: 'bg-primary-100 dark:bg-primary-600/20',
                                    icon: 'text-primary-500',
                                }" />
                            </template>
                        </UPageFeature>
                        <UButton block size="lg" class="mt-4"
                            :to="`/modules/${module.title.toLowerCase().replace(/ & /g, '-').replace(/ /g, '-')}`">
                            Explore
                        </UButton>
                    </UCard>
                </div>
            </UPageSection>
            <UPageSection title="Project Tracking"
                description="Monitor research project progress, milestones, and budget utilization">
                <div class="w-full grid grid-cols-1 content-start gap-4">
                    <UCard v-for="project in [
                        { title: 'Marine Ecosystem Restoration Project', code: 'P003', status: 'On Track', date: '2024-05-01', lead: 'Dr. Sarah Johnson • Marine Biology' },
                        { title: 'Climate Impact on Fish Migration Patterns', code: 'P002', status: 'On Track', date: '2024-06-15', lead: 'Dr. Michael Chen • Oceanography' },
                        { title: 'Sustainable Aquaculture Technology Development', code: 'P001', status: 'On Track', date: '2024-07-10', lead: 'Dr. Emily Rodriguez • Fisheries Technology' }
                    ]">
                        <div class="flex justify-between items-center">
                            <div class="flex items-center gap-2">
                                <div class="font-semibold text-highlighted">{{ project.title }}</div>
                                <UBadge color="neutral" variant="outline" class="rounded-full">{{ project.code }}</UBadge>
                            </div>
                            <UBadge :label="project.status" color="lime" variant="soft" class="rounded-full" />
                        </div>
                        <div class="text-sm text-muted">
                            Lead: {{ project.lead }}
                        </div>
                        <!-- <template #trailing>
                            <div class="text-sm text-dimmed">
                                {{ new Date(project.date).toLocaleDateString() }}
                            </div>
                        </template> -->
                    </UCard>
                </div> 
            </UPageSection>
        </template>
    </UDashboardPanel>
</template>

<script setup lang="ts">
const items = ref([
    [
        {
            label: 'Profile',
            icon: 'i-lucide-user'
        },
        {
            label: 'Settings',
            icon: 'i-lucide-settings'
        },
        {
            label: 'Color Mode',
            icon: 'i-lucide-monitor',
            slot: 'color-mode' as const
        }
    ],
    [
        {
            label: 'Logout',
            icon: 'i-lucide-log-out'
        }
    ]
])
</script>