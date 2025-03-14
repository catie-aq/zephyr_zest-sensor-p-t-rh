# Zest_Sensor_P-T-RH

Zest_Sensor_P-T-RH board support for Zephyr OS.

## Usage

This board enables the following components:

- [OMRON 2SMPB-02E](https://components.omron.com/us-en/products/sensors/2SMPB-02B) digital barometric pressure sensor
- [AMS AS621x](https://ams.com/as621x) temperature sensor
- [TE-Connectivity HTU21D(F)](https://www.te.com/fr/product-CAT-HSC0004.html) relative humidity sensor

:bulb: Theses drivers should also be added to your workspace:

- [OMRON 2SMPB-02E driver](https://github.com/catie-aq/zephyr_omron-2smpb-02e) for Zephyr OS
- [AMS AS621X driver](https://github.com/catie-aq/zephyr_ams-as621x) for Zephyr OS
- [TE Connectivity HTU21D(F) driver](https://github.com/catie-aq/zephyr_te-connectivity-htu21d) for Zephyr OS

:pushpin: This shield defines:

- the pressure sensor alias: `o2smpb-02e` to `o2smpb_02e_zest_sensor_p_t_rh_<X>`
- the temperature sensor alias: `ams621x` to `ams621x_zest_sensor_p_t_rh_<X>`
- the humidity sensor alias: `htu21d` to `htu21d_zest_sensor_p_t_rh_<X>`
- the 1-wire sensor alias: `w1` to `w1_zest_sensor_p_t_rh_<X>`

:triangular_ruler: To use this shield:

- Update your device tree by adding the `ZEST_SENSOR_P_T_RH(port)` macro to the `app.overlay` file.\
  Replace `port` with the number of the Zest_Core port to which the shield is connected, e.g.:

  ```c
  ZEST_SENSOR_P_T_RH(1) /* Zest_Sensor_P-T-RH connected to Zest_Core first port */
  ```

- Activate support for the shield by adding `--shield zest_sensor_p-t-rh` to the west command.

## Advanced Usage

This shield can be hardware-modified to suit your application.

In that case, use instead the alternate variant of the shield:

- Update your device tree by adding the `ZEST_SENSOR_P_T_RH_ALT(port, w1)` macro to the `app.overlay` file, with:
  - `port`: number of the Zest_Core port to which the shield is connected,
  - `w1`: 1w sensor pin
- Activate support for the shield by adding `--shield zest_sensor_p-t-rh_alt` to the west command.

## 1-Wire

A 1-Wire sensor may be connected to the J4 connector, see below for an example on how to enable an external DS18B20 temperature sensor:

```dts
&ds18b20_zest_sensor_p_t_rh_<X> {
	status = "okay";
};
```

Then, use official Zephyr OS [DS18B20 1-Wire Temperature Sensor example](https://github.com/zephyrproject-rtos/zephyr/tree/main/samples/sensor/ds18b20).

> [!NOTE]
> Replace `<X>` with the 6TRON port number.
