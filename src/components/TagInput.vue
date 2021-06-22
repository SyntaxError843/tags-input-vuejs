<template>

<div class="text-2xl text-gray-700 font-semibold my-2">Tag Input</div>
<div class="flex flex-wrap items-center border rounded p-2">
    <div class="flex flex-wrap m-1.5">
        <div v-for="(tag, index) in state.tags" :key="tag" class="flex content-between items-center py-1.5 px-2.5 m-1 bg-gray-200 rounded-md text-sm text-gray-800">
            <span class="mr-1.5 text-xs font-bold cursor-pointer" @click='removeTag(index)'>x</span>
            {{ tag }}
        </div>
    </div>
    <div class="flex-grow">
        <input class="w-full border-none outline-none bg-transparent leading-6" type="text" placeholder="Enter a Tag" @keydown='addTag' />
    </div>
</div>

</template>

<script>

import { reactive } from 'vue';

export default {
    
    setup() {

        /**
         * Set up state with initial values
         */
        const state = reactive({

            'tags': [ 'Hello', 'World', 'This is my first vue project', ':D' ],

        });

        /**
         * Function to add tags to state
         * 
         * @param object     keyDown event
         */
        const addTag = e => {

            /**
             * Get trimmed input
             */
            const tag = e.target.value.trim();

            /**
             * Check if there is text before doing anything
             */
            if ( tag.length !== 0 ) {

                /**
                 * Check if key code is Comma, Enter or Tab
                 */
                if ( e.code === 'Comma' || e.code === 'Enter' || e.code === 'Tab' ) {

                    e.preventDefault();

                    /**
                     * Add new tag to state
                     */
                    state.tags = [ ...state.tags, tag ];

                    /**
                     * Clear text field
                     */
                    e.target.value = '';

                }

            } else {

                /**
                 * Do not allow commas or spaces at the beginning
                 */
                if ( e.code === 'Comma' || e.code === 'Space' ) e.preventDefault();

                /**
                 * Delete last tag if key code is backspace
                 */
                if ( e.code === 'Backspace' ) removeTag( state.tags.length - 1 );

            }

        }

        /**
         * Function to remove tags from state
         * 
         * @param integer     tag index in state array
         */
        const removeTag = indexToRemove => {

            /**
             * Check if there are any tags to remove
             */
            if ( state.tags.length > 0 ) {

                state.tags = [ ...state.tags.slice( 0, indexToRemove ), ...state.tags.slice( indexToRemove + 1 ) ];

            }
            

        }

        return {
            state,
            addTag,
            removeTag,
        }

    },

}

</script>

<style scoped>

</style>