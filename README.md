# Zest_Sensor_P-T-RH

Zest_Sensor_P-T-RH board support for Zephyr OS.

## Usage

This board enables the following components:

- [OMRON 2SMPB-02E](https://components.omron.com/us-en/products/sensors/2SMPB-02B) digital barometric pressure sensor.
- [AMS AS621x](https://ams.com/as621x) temperature sensor.
- [TE-Connectivity HTU21D(F)](https://www.te.com/fr/product-CAT-HSC0004.html) relative humidity sensor.

:bulb: These drivers should also be added to your workspace:

- [OMRON 2SMPB-02E driver](https://github.com/catie-aq/zephyr_omron-2smpb-02e).
- [AMS AS621X driver](https://github.com/catie-aq/zephyr_ams-as621x).
- [TE Connectivity HTU21D(F) driver](https://github.com/catie-aq/zephyr_te-connectivity-htu21d).

:pushpin: This shield defines:

- The pressure sensor device: `o2smpb_02e_zest_sensor_p_t_rh_<port>`.
- The temperature sensor device: `ams621x_zest_sensor_p_t_rh_<port>`.
- The humidity sensor device: `htu21d_zest_sensor_p_t_rh_<port>`.
- The 1-wire sensor bus: `w1_zest_sensor_p_t_rh_<port>`.

:triangular_ruler: To use this shield:

- Update your device tree by adding the `ZEST_SENSOR_P_T_RH(port)` macro to the `app.overlay` file.\
  Replace `port` with the number of the Zest_Core port to which the shield is connected, e.g.:

  ```dts
  ZEST_SENSOR_P_T_RH(1) /* Zest_Sensor_P-T-RH connected to Zest_Core first port */
  ```

- Activate support for the shield by adding `--shield zest_sensor_p-t-rh` to the west command.

## Advanced Usage

This shield can be hardware-modified to suit your application.

In that case, use instead the alternate variant of the shield:

- Update your device tree by adding the `ZEST_SENSOR_P_T_RH_ALT(port, w1)` macro to the `app.overlay` file, with:
  - `port`: number of the Zest_Core port to which the shield is connected,
  - `w1`: 1-Wire sensor pin.
- Activate support for the shield by adding `--shield zest_sensor_p-t-rh_alt` to the west command.

## 1-Wire

An external DS18B20 1-Wire sensor may be connected to the J4 connector. Update your device tree by adding the `status = "okay";` parameter to the `ds18b20_zest_sensor_p_t_rh_<port>` in the `app.overlay` file.\
  Replace `port` with the number of the Zest_Core port to which the shield is connected, e.g.:

```dts
/* DS18B20 1-Wire connected on the Zest_Sensor_P-T-RH on the Zest_Core first port */
&ds18b20_zest_sensor_p_t_rh_1 {
  status = "okay";
};
```

Then, use official Zephyr OS [DS18B20 1-Wire Temperature Sensor example](https://github.com/zephyrproject-rtos/zephyr/tree/main/samples/sensor/ds18b20).
