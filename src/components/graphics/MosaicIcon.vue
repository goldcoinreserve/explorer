<template>
	<svg xmlns="http://www.w3.org/2000/svg" version="1.0" width="20.000000pt" height="20.000000pt" viewBox="0 0 500.000000 500.000000" preserveAspectRatio="xMidYMid meet" fill="#ec2227">

		<g transform="translate(0.000000,500.000000) scale(0.100000,-0.100000)" fill="#ec2227" stroke="none">
			<path d="M1718 4732 c-422 -114 -764 -210 -760 -213 4 -4 352 -99 775 -212 l767 -205 768 205 c422 113 770 208 774 212 6 5 -1538 424 -1552 420 -3 0 -350 -94 -772 -207z" />
			<path d="M721 4278 c30 -57 893 -1495 904 -1506 10 -11 75 91 349 545 318 527 335 558 314 565 -44 14 -1561 418 -1570 418 -5 0 -3 -10 3 -22z" />
			<path d="M3485 4090 c-423 -114 -789 -213 -812 -219 l-43 -12 0 -1154 c0 -635 2 -1155 3 -1155 2 0 23 33 47 73 24 39 394 655 823 1367 428 712 781 1298 784 1303 2 4 -4 6 -14 6 -10 -1 -364 -95 -788 -209z" />
			<path d="M2348 3420 c-9 -14 -288 -477 -621 -1030 -332 -553 -697 -1160 -811 -1349 -114 -189 -206 -345 -204 -346 5 -4 1642 436 1651 444 4 4 6 524 5 1157 -3 1078 -4 1147 -20 1124z" />
			<path d="M3028 1683 c-185 -307 -335 -560 -333 -561 6 -6 1590 -430 1593 -427 4 3 -903 1524 -917 1538 -4 4 -158 -244 -343 -550z" />
			<path d="M1805 709 c-363 -98 -704 -190 -759 -205 -58 -16 -93 -30 -85 -34 8 -4 357 -99 776 -210 l763 -203 737 196 c872 233 816 217 811 223 -10 9 -1534 414 -1557 413 -14 -1 -323 -82 -686 -180z" />
		</g>
	</svg>
</template>

<script>
import GraphicComponent from './GraphicComponent.vue';

export default {
	extends: GraphicComponent,

	props: {
		width: {
			type: Number,
			default: 261.333
		},

		height: {
			type: Number,
			default: 131.313
		},

		mosaic: {
			type: Object,
			default: () => ({
				mosaicId: '',
				aliasName: ''
			})
		},

		mosaicId: {
			type: String
		},

		aliasName: {
			type: String
		},

		hideCaption: {
			type: Boolean,
			default: false
		}
	},

	computed: {
		title() {
			return this.getTranslation('mosaic') + ': ' + ((this.aliasName || this.mosaic.aliasName) || (this.mosaicId || this.mosaic.mosaicId));
		},

		iconColor() {
			return this.getIconColorFromHex(this.mosaicId || this.mosaic.mosaicId);
		},

		truncatedMosaicId() {
			return this.truncString(this.mosaicId || this.mosaic.mosaicId);
		},

		truncatedMosaicName() {
			const aliasName = this.aliasName || this.mosaic.aliasName;
			const mosaicId = this.mosaicId || this.mosaic.mosaicId;

			if (aliasName)
				return this.truncString(aliasName, 5);
			return this.truncString(mosaicId);
		},

		viewBox() {
			return this.hideCaption
				? '115 0 16 105'
				: '0 0 261.333 131.313';
			// 0 0 116 105
		}
	}
};
</script>

<style lang="scss" scoped>
.connector {
    cursor: pointer;
}

.connector-body {
    font-size: 18px;
    font-weight: bold;
}

.mosaic-text {
    font-size: 18px;
    font-weight: bold;
    fill: var(--secondary);
}
</style>
