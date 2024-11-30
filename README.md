UPDI library with hooks for both hardware UART and software bitbanging

To use software bitbanging, implement these functions
 * void UPDI_Set(bool) - set the output level of the pin
 * bool UPDI_Get() - get value from pin
 * void UPDI_LoopDelay() - should be approximately 1/10 of the bit delay
 * void UPDI_BitDelay() - delay 1 bit length
 * void UPDI_HalfBitDelay() - delay 1/2 bit length

To use hardware uart, implement these functions
 * bool UPDI_Read(uint8_t *val) - return whether read was succesful or not, paramter val is the read value
 * bool UPDI_Write(uint8_t *val) - return whether write was succesful or not, paramter val is the value to write
 * bool UPDI_Idle() - if UPDI_BitDelay() is implemented, then this is not required to be implemented. This function should drive the UPDI pin to the inactive/High Z state for a minimum of 12 bits
 * bool UPDI_Break() - if UPDI_BitDelay() and UPDI_Set is implemented, then this is not required to be implemented. This function should drive the UPDI pin to the active low state for a minimum of 12 bits
