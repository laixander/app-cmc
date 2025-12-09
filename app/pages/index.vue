<template>
    <div class="p-6 flex justify-center items-center">
        <UCard class="max-w-sm" :ui="{header:'flex justify-between items-center'}">
            <template #header>
                <div class="font-semibold">
                    Simple Application
                </div>
                <UColorModeButton />
            </template>
            <div class="text-sm">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Totam aspernatur consequuntur iste dolor repudiandae accusantium ut molestias impedit provident maxime modi quaerat eum, sapiente qui, omnis vero dignissimos optio voluptas.
            </div>
            <template #footer>
                <UButton label="Continue" size="lg" block to="/dashboard" />
            </template>
        </UCard>
    </div>
</template>