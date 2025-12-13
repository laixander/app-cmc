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
                <div class="w-full grid grid-cols-2 content-start gap-8">
                    <UCard v-for="project in [
                        { title: 'Marine Ecosystem Restoration Project', code: 'P003', status: 'On Track', days: 87, progress: 75, utilization: 72, spent: '1.8M', budget: '2.5M', date: '2026-05-01', lead: 'Dr. Sarah Johnson • Marine Biology' },
                        { title: 'Climate Impact on Fish Migration Patterns', code: 'P002', status: 'On Track', days: 158, progress: 45, utilization: 50, spent: '0.9M', budget: '1.8M', date: '2026-06-15', lead: 'Dr. Michael Chen • Oceanography' },
                        { title: 'Sustainable Aquaculture Technology Development', code: 'P001', status: 'Delayed', days: 5, progress: 90, utilization: 84, spent: '2.7M', budget: '3.2M', date: '2026-07-10', lead: 'Dr. Emily Rodriguez • Fisheries Technology' }
                    ]" :ui="{
                        footer: 'flex justify-between items-center'
                    }">
                        <div class="flex justify-between items-center">
                            <div class="flex items-center gap-2">
                                <div class="font-semibold text-highlighted">{{ project.title }}</div>
                                <UBadge color="neutral" variant="outline" class="rounded-full">{{ project.code }}</UBadge>
                            </div>
                            <UBadge 
                                :label="project.status" 
                                :color="{
                                    'On Track': 'green' as const,
                                    'Delayed': 'amber' as const,
                                    'At Risk': 'red' as const,
                                    'Completed': 'sky' as const,
                                    'On Hold': 'gray' as const
                                }[project.status] || 'gray'"
                                variant="soft" 
                                class="rounded-full" 
                            />
                        </div>
                        <div class="text-sm text-muted">
                            Lead: {{ project.lead }}
                        </div>
                        <div class="grid grid-cols-1 gap-6 mt-4">
                            <UFormField :hint="`${project.progress}% completed`" class="w-full">
                                <template #label>
                                    <UIcon name="i-lucide-chart-no-axes-column" class="mr-1" />
                                    Overall Progress
                                </template>
                                <UProgress 
                                    :model-value="project.progress" 
                                    :color="{
                                        'On Track': 'green' as const,
                                        'Delayed': 'amber' as const,
                                        'At Risk': 'red' as const,
                                        'Completed': 'sky' as const,
                                        'On Hold': 'gray' as const
                                    }[project.status] || 'gray'" 
                                />
                            </UFormField>
                            <UFormField :hint="`${project.utilization}%`" :help="`₱${project.spent}/₱${project.budget} of budget allocated`" class="w-full">
                                <template #label>
                                    <UIcon name="i-lucide-philippine-peso" class="mr-1" />
                                    Budget Utilization
                                </template>
                                <UProgress 
                                    :model-value="project.utilization"
                                />
                            </UFormField>
                        </div>
                        <template #footer>
                            <div class="flex items-center gap-2">
                                <UIcon name="i-lucide-calendar" />
                                <span class="font-semibold text-sm">{{ project.days }} days left</span>
                            </div>
                            <div class="text-sm text-muted">
                                Deadline: {{ new Date(project.date).toLocaleDateString() }}
                            </div>
                        </template>
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