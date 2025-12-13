<template>
    <UDashboardPanel class="z-50">
        <template #header>
            <UDashboardNavbar :toggle="false" :ui="{ title: 'flex-col items-start justify-center gap-0' }">
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
                    <UColorModeButton />
                    <UserMenu />
                </template>
            </UDashboardNavbar>
        </template>
        <template #body>
            <UPageSection title="Coastal Monitoring Center"
                description="Comprehensive dashboard suite for research data management, environmental monitoring, and community extension services">
                <div class="w-full grid lg:grid-cols-4 content-start gap-8">
                    <UPageCard v-for="module in [
                        { title: 'Coastal Monitoring System', description: 'Real-time environmental data visualization and alerts', icon: 'i-lucide-radio-tower' },
                        { title: 'Fisheries & Oceanography Data Management', description: 'Experimental research data management and analysis', icon: 'i-lucide-fish' },
                        { title: 'Research Information Management', description: 'Research outputs, metrics, and researcher databases', icon: 'i-lucide-flask-conical' },
                        { title: 'Extension Services Management', description: 'Community extension programs and impact tracking', icon: 'i-lucide-anchor' }
                    ]" spotlight spotlight-color="primary" :title="module.title" :description="module.description">
                        <template #leading>
                            <UAvatar size="3xl" :icon="module.icon" class="rounded-none squircle" :ui="{
                                root: 'bg-primary-100 dark:bg-primary-600/20',
                                icon: 'text-primary-500',
                            }" />
                        </template>
                        <template #footer>
                            <UButton block size="lg" class="mt-4"
                                :to="`/modules/${module.title.toLowerCase().replace(/ & /g, '-').replace(/ /g, '-')}`">
                                Explore
                            </UButton>
                        </template>
                    </UPageCard>
                </div>
            </UPageSection>
            <UPageSection title="Project Tracking"
                description="Monitor research project progress, milestones, and budget utilization">
                <div class="w-full grid lg:grid-cols-2 content-start gap-8">
                    <UPageCard v-for="project in [
                        { title: 'Marine Ecosystem Restoration Project', code: 'P003', status: 'On Track', days: 87, progress: 75, utilization: 72, spent: '1.8M', budget: '2.5M', date: 'May 1, 2026', lead: 'Dr. Sarah Johnson', role: 'Marine Biology' },
                        { title: 'Climate Impact on Fish Migration Patterns', code: 'P002', status: 'On Track', days: 158, progress: 45, utilization: 50, spent: '0.9M', budget: '1.8M', date: 'June 15, 2026', lead: 'Dr. Michael Chen', role: 'Oceanography' },
                        { title: 'Sustainable Aquaculture Technology Development', code: 'P001', status: 'Delayed', days: 3, progress: 90, utilization: 84, spent: '2.7M', budget: '3.2M', date: 'July 10, 2025', lead: 'Dr. Emily Rodriguez', role: 'Fisheries Technology' }
                    ]" spotlight spotlight-color="primary">

                        <div>
                            <div class="flex justify-between items-center">
                                <div class="flex items-center gap-2">
                                    <div class="font-semibold text-highlighted">{{ project.title }}</div>
                                    <UBadge color="neutral" variant="outline" class="rounded-full">{{ project.code }}
                                    </UBadge>
                                </div>
                                <UBadge :label="project.status" :icon="{
                                    'On Track': 'i-lucide-check-circle',
                                    'Delayed': 'i-lucide-clock',
                                    'At Risk': 'i-lucide-alert-triangle',
                                    'Completed': 'i-lucide-check',
                                    'On Hold': 'i-lucide-pause-circle'
                                }[project.status]" :color="{
                                    'On Track': 'green',
                                    'Delayed': 'amber',
                                    'At Risk': 'red',
                                    'Completed': 'sky',
                                    'On Hold': 'gray'
                                }[project.status] || 'gray'" variant="soft" class="rounded-full" />
                            </div>
                            <div class="flex items-center text-sm text-muted">
                                <UIcon name="i-lucide-circle-user" class="size-5 mr-2" />{{ project.lead }}
                                <UIcon name="i-lucide-dot" class="size-6" />{{ project.role }}
                            </div>
                        </div>
                        <div class="grid grid-cols-1 gap-8 mt-4">
                            <UFormField :ui="{
                                label: 'flex items-center gap-2'
                            }" :hint="`${project.progress}% completed`" class="w-full">
                                <template #label>
                                    <UIcon name="i-lucide-trending-up" class="size-5" />
                                    Overall Progress
                                </template>
                                <UProgress :model-value="project.progress" :color="{
                                    'On Track': 'green',
                                    'Delayed': 'amber',
                                    'At Risk': 'red',
                                    'Completed': 'sky',
                                    'On Hold': 'gray'
                                }[project.status] || 'gray'" />
                            </UFormField>
                            <UFormField :ui="{
                                label: 'flex items-center gap-2',
                                help: 'flex justify-between items-center text-xs'
                            }" :hint="`${project.utilization}%`" class="w-full">
                                <template #label>
                                    <UIcon name="i-lucide-banknote" class="size-5" />
                                    Budget Utilization
                                </template>
                                <UProgress :model-value="project.utilization" />
                                <template #help>
                                    <span>Spent: ₱{{ project.spent }}</span>
                                    <span>Budget: ₱{{ project.budget }}</span>
                                </template>
                            </UFormField>
                        </div>
                        <USeparator class="mt-4 mb-2" />
                        <div class="flex items-center justify-between">
                            <UBadge icon="i-lucide-clock" variant="soft" class="rounded-full" :color="project.days <= 3 ? 'red'
                                : project.days <= 7 ? 'orange'
                                    : 'gray'
                                ">{{ project.days }} days left</UBadge>
                            <div class="flex items-center gap-2">
                                <!-- <UIcon name="i-lucide-calendar" /> -->
                                <div class="p-1 rounded-full bg-primary/20">
                                    <div class="size-2 rounded-full bg-primary"></div>
                                </div>
                                <span class="text-sm text-muted">Deadline: {{ project.date }}</span>
                                <!-- Deadline: {{ new Date(project.date).toLocaleDateString() }} -->
                            </div>
                        </div>
                    </UPageCard>
                </div>
            </UPageSection>
        </template>
    </UDashboardPanel>
</template>

<script setup lang="ts">
</script>