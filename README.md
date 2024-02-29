# Zest_Sensor_P-T-RH

Zest_Sensor_P-T-RH board support for Zephyr OS.
## Usage
This board enables the following sensors:
- [AMS AS621x](https://ams.com/as621x) temperature sensor
- [TE-Connectivity HTU21D(F)](https://www.te.com/fr/product-CAT-HSC0004.html) relative humidity sensor
- [OMRON 2SMPB-02E](https://components.omron.com/us-en/products/sensors/2SMPB-02B) digital barometric pressure sensor

:bulb: Sensors' drivers should also be added to your workspace:
- [TE Connectivity HTU21D(F) driver for Zephyr RTOS](https://github.com/catie-aq/zephyr_te-connectivity-htu21d)
- [AMS AS621X driver for Zephyr OS](https://github.com/catie-aq/zephyr_ams-as621x)
- [OMRON 2SMPB-02E driver for Zephyr OS](https://github.com/catie-aq/zephyr_omron-2smpb-02e)

## 1-Wire
A 1-Wire sensor may be connected to the J4 connector, see below for an example on how to enable an external DS18B20 temperature sensor:

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

Then, use official Zephyr OS [DS18B20 1-Wire Temperature Sensor example](https://github.com/zephyrproject-rtos/zephyr/tree/main/samples/sensor/ds18b20).
