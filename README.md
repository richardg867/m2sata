# M.2 SATA Port Reclaimer - Jumperable Version

This is a special version of the card from the [main branch](https://github.com/richardg867/m2sata/tree/jumperable) with jumper links to control polarity of the SATA B lanes. See the main branch's readme for more information. This design is **untested** and may not work as reliably as the main one due to signal integrity implications.

The jumpers, highlighted in red in the images below, can be configured individually for each port. Fill them in with solder bridges or 0Ω 0402 resistors.

## Non-inverting

Same configuration as lane 0 on the main design.

![-|](https://user-images.githubusercontent.com/540874/201233284-233c255e-3132-4f24-9c8b-7e1af9a90d27.png)

## Inverting

Same configuration as lanes 1-3 on the main design.

![|-](https://user-images.githubusercontent.com/540874/201233479-0e5fa054-e3a9-40bb-8ad7-758c3e21b536.png)
