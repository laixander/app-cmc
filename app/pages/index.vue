<template>
    <div class="grid grid-cols-2 gap-8 p-8 max-w-4xl mx-auto">
        <UCard v-for="module in [
            { title: 'Coastal Monitoring System', description: 'Real-time environmental data visualization and alerts' },
            { title: 'Fisheries & Oceanography Data Management', description: 'Experimental research data management and analysis' },
            { title: 'Research Information Management', description: 'Research outputs, metrics, and researcher databases' },
            { title: 'Extension Services Management', description: 'Community extension programs and impact tracking' }
        ]"
        :ui="{header:'flex justify-between items-center'}">
            <template #header>
                <div class="font-semibold">
                    {{module.title}}
                </div>
                <UColorModeButton />
            </template>
            <div class="text-sm">
                {{ module.description }}
            </div>
            <template #footer>
                <UButton label="Continue" size="lg" block to="/dashboard" />
            </template>
        </UCard>
    </div>
</template>