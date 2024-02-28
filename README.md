# Zest_Sensor_P-T-RH

Zest_Sensor_P-T-RH board for Zephyr OS.

## 1-Wire
Example for 1-Wire temperature sensor DS18B20.

```dts
&w1 {
	ds18b20 {
		compatible = "maxim,ds18b20";
		family-code = <0x28>;
		resolution = <12>;
		status = "okay";
	};
};
```
