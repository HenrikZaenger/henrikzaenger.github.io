<script lang="ts">
	let { format, input } = $props();

	let value = $derived(toInt(format, input) ?? 0);
	let valueBin = $derived(toBinaryBytePadded(value) ?? '');
	let valueHex = $derived(toHexBytePadded(value) ?? '');

    function toInt(format: string, input: number | string): number {
        if (input === undefined || input === null || input === '') return 0;

        const str = String(input);

        switch (format) {
            case "hex":
                return Number("0x" + str) || 0;
            case "dec":
                return Number(str) || 0;
            case "bin":
                return Number("0b" + str) || 0;
            default:
                return 0;
        }
    }

	function toBinaryBytePadded(num: number): string {
        let bin = num.toString(2);
        let paddedLength = Math.ceil(bin.length / 8) * 8;
        bin = bin.padStart(paddedLength, '0');
        return bin.match(/.{1,8}/g)?.join(' ') ?? '';
    }

	function toHexBytePadded(num: number): string {
        let hex = num.toString(16).toUpperCase();
        let paddedLength = Math.ceil(hex.length / 2) * 2;
        hex = hex.padStart(paddedLength, '0');
        return hex.match(/.{1,2}/g)?.join(' ') ?? '';
    }
</script>

<p>Binary: 0b{valueBin}</p>
<p>Decimal: {value}</p>
<p>Hexadecimal: 0x{valueHex}</p>