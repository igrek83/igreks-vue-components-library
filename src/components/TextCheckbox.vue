<template>
	<component :is="tag" :class="textCheckbox.block">
		<input
			:type="type"
			v-model="model"
			:value="value"
			@input.prevent.stop.self="$emit('changeValueCheckbox', value)"
			:id="id"
			:class="textCheckbox.checkbox"
			:disabled="disabled"
		>
		<label :for="id" :class="textCheckbox.label">{{ text }}</label>
	</component>
</template>

<script lang="ts" setup>
import { computed } from "vue";
const props = withDefaults(
	defineProps<{
		readonly id: number | string,
		readonly value: string | number,
		readonly model: string | number | Array<string | number>,
		readonly type?: 'radio' | 'checkbox',
		readonly text?: string,
		readonly tag?: string,
		readonly disabled?: boolean,
		readonly backgroundColor?: string,
		readonly backgroundColorHover?: string,
		readonly backgroundColorActive?: string,
		readonly backgroundColorDisabled?: string,
		readonly borderRadius?: string,
		readonly width?: string,
		readonly height?: string,
		readonly paddingBlock?: string,
		readonly paddingInline?: string,
		readonly borderWidth?: string,
		readonly borderStyle?: string,
		readonly borderColor?: string,
		readonly borderColorActive?: string,
		readonly borderColorDisabled?: string,
		readonly fontFamily?: string,
		readonly fontSize?: string,
		readonly fontWeight?: number | string,
		readonly color?: string,
		readonly colorActive?: string,
		readonly colorDisabled?: string,
	}>(),
	{
		type: 'radio',
		tag: 'div',
		disabled: false,
		backgroundColor: 'hsla(240, 11%, 96%, 1)',
		backgroundColorActive: 'hsla(0, 0%, 100%, 1)',
		backgroundColorDisabled: 'hsla(0, 0%, 100%, 1)',
		borderRadius: '8px',
		width: 'max-content',
		height: 'max-content',
		paddingBlock: '14px',
		paddingInline: '18px',
		borderWidth: '2px',
		borderStyle: 'solid',
		borderColor: 'hsla(240, 11%, 96%, 1)',
		borderColorActive: 'hsla(223, 100%, 60%, 1)',
		borderColorDisabled: 'hsla(0, 0%, 100%, 1)',
		fontFamily: 'Source Sans Pro',
		fontSize: '16px',
		fontWeight: 400,
		color: 'hsla(0, 0%, 11%, 1)',
		colorActive: 'hsla(0, 0%, 11%, 1)',
		colorDisabled: 'hsla(0, 0%, 11%, 1)',
	}
);

const model = computed({
	get: () => props.model,
	set: () => {}
})
</script>

<style lang="css" module="textCheckbox">
.block {
	display: flex;
}

.checkbox {
	display: none;
}

.label {
	box-sizing: border-box;
	outline: none;
	-webkit-tap-highlight-color: transparent;
	cursor: pointer;
	width: v-bind(width);
	height: v-bind(height);
	padding: v-bind(paddingBlock) v-bind(paddingInline);
	border-radius: v-bind(borderRadius);
	background-color: v-bind(backgroundColor);
	border: v-bind(borderWidth) v-bind(borderStyle) v-bind(borderColor);
	color: v-bind(color);
	font-family: v-bind(fontFamily), -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
	font-size: v-bind(fontSize);
	line-height: v-bind(fontSize);
	font-weight: v-bind(fontWeight);
	transition-duration: 0s;
}

.checkbox:checked + .label {
	color: v-bind(colorActive);
	border-color: v-bind(borderColorActive);
	background-color: v-bind(backgroundColorActive);
}

.checkbox:disabled + .label {
	color: v-bind(colorDisabled);
	border-color: v-bind(borderColorDisabled);
	background-color: v-bind(backgroundColorDisabled);
	pointer-events: none;
}
</style>
