<template>
    <UDashboardGroup unit="rem">
        <!-- <div class="min-h-screen grid">
        <slot></slot>
    </div> -->
        <slot />
        <div class="fixed -bottom-15 left-0 w-full z-0 pointer-events-none opacity-40">
            <svg class="w-full h-auto min-h-[300px]" viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg"
                preserveAspectRatio="none">
                <defs>
                    <!-- ONE PERFECTLY LOOPING WAVE -->
                    <path id="wave" d="
                        M0 200
                        C 240 160, 480 240, 720 200
                        C 960 160, 1200 240, 1440 200
                        L 1440 320
                        L 0 320
                        Z
                    " />
                </defs>

                <!-- FAR -->
                <g fill="#00bcff" fill-opacity="0.25">
                    <use href="#wave" x="0" />
                    <use href="#wave" x="1440" />
                    <animateTransform attributeName="transform" type="translate" from="0 0" to="-1440 0" dur="5s"
                        repeatCount="indefinite" />
                </g>

                <!-- MID -->
                <g fill="#00bcff" fill-opacity="0.25">
                    <use href="#wave" x="0" y="-20" />
                    <use href="#wave" x="1440" y="-20" />
                    <animateTransform attributeName="transform" type="translate" from="0 0" to="-1440 0" dur="10s"
                        repeatCount="indefinite" />
                </g>

                <!-- FRONT -->
                <g fill="#00bcff" fill-opacity="0.25">
                    <use href="#wave" x="0" y="-40" />
                    <use href="#wave" x="1440" y="-40" />
                    <animateTransform attributeName="transform" type="translate" from="0 0" to="-1440 0" dur="60s"
                        repeatCount="indefinite" />
                </g>
            </svg>

        </div>
    </UDashboardGroup>
</template>