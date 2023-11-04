<template>
	<button
		:type="type"
		:name="name"
		:aria-label="name"
		:class="textButton.button"
		:disabled="disabled"
		@click.self.prevent.stop="$emit('setClickOnTheButton')"
		@keydown.self.prevent.stop="$emit('setClickOnTheButton')"
	>
		{{ text }}
	</button>
</template>

<script lang="ts" setup>
withDefaults(
	defineProps<{
		readonly type?: 'button' | 'submit' | 'reset',
		readonly disabled?: boolean,
		readonly text?: string,
		readonly name?: string,
		readonly fontFamily?: string,
		readonly fontSize?: string,
		readonly fontWeight?: number | string,
		readonly color?: string,
		readonly colorHover?: string,
		readonly colorDisabled?: string,
		readonly backgroundColor?: string,
		readonly backgroundColorHover?: string,
		readonly backgroundColorDisabled?: string,
		readonly borderRadius?: string,
		readonly borderWidth?: string,
		readonly borderStyle?: string,
		readonly borderColor?: string,
		readonly borderColorHover?: string,
		readonly borderColorDisabled?: string,
		readonly paddingBlock?: string,
		readonly paddingInline?: string,
		readonly width?: string,
		readonly height?: string,
	}>(),
	{
		type: 'button',
		disabled: false,
		text: 'Отправить',
		name: 'button',
		fontFamily: 'Source Sans Pro',
		fontSize: '16px',
		fontWeight: 400,
		color: 'hsla(0, 0%, 100%, 1)',
		colorHover: 'hsla(0, 0%, 100%, 1)',
		colorDisabled: 'hsla(0, 0%, 100%, 1)',
		backgroundColor: 'hsla(223, 100%, 60%, 1)',
		backgroundColorHover: 'hsla(223, 64%, 45%, 1)',
		backgroundColorDisabled: 'hsla(223, 100%, 60%, 0.9)',
		borderRadius: '8px',
		borderWidth: '2px',
		borderStyle: 'solid',
		borderColor: 'hsla(223, 100%, 60%, 1)',
		borderColorHover: 'hsla(223, 64%, 45%, 1)',
		borderColorDisabled: 'hsla(223, 100%, 60%, 0.9)',
		paddingBlock: '10px',
		paddingInline: '14px',
		width: 'max-content',
		height: 'max-content',
	}
);
</script>

<style lang="css" module="textButton">
.button {
	display: flex;
	align-items: center;
	justify-content: center;
	box-sizing: border-box;
	-webkit-tap-highlight-color: transparent;
	cursor: pointer;
	transition-duration: 0.15s;
	padding: v-bind(paddingBlock) v-bind(paddingInline);
	height: v-bind(height);
	width: v-bind(width);
	border: v-bind(borderWidth) v-bind(borderStyle) v-bind(borderColor);
	border-radius: v-bind(borderRadius);
	background-color: v-bind(backgroundColor);
	color: v-bind(color);
	font-family: v-bind(fontFamily), -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
	font-size: v-bind(fontSize);
	line-height: v-bind(fontSize);
	font-weight: v-bind(fontWeight);
}

.button, .button:active, button:focus {
	outline: none;
}

.button:disabled {
	color: v-bind(colorDisabled);
	background-color: v-bind(backgroundColorDisabled);
	border-color: v-bind(borderColorDisabled);
}

@media (hover: hover) and (pointer: fine) {
	.button:hover {
		color: v-bind(colorHover);
		background-color: v-bind(backgroundColorHover);
		border-color: v-bind(borderColorHover);
	}
}
</style>
