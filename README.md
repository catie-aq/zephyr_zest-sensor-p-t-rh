# Zest_Sensor_P-T-RH

Zest_Sensor_P-T-RH board support for Zephyr OS.
## Usage
This board enables the following sensors:
- [AMS AS621x](https://ams.com/as621x) temperature sensor
- [TE-Connectivity HTU21D(F)](https://www.te.com/fr/product-CAT-HSC0004.html) relative humidity sensor

:bulb: Sensors' drivers should also be added to your workspace:
- [TE Connectivity HTU21D(F) driver for Zephyr RTOS](https://github.com/catie-aq/zephyr_te-connectivity-htu21d)
- [AMS AS621X driver for Zephyr OS](https://github.com/catie-aq/zephyr_ams-as621x)

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
