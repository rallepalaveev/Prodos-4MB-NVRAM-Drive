# Prodos-4MB-NVRAM-Drive
A card with 4MB NVRAM for Apple ][ compatible computers which is a ProDOS compliant R/W device. This is a project based on my Prodos 512kB NVRAM drive which is intended to work with 8 NVRAM chips 39SF040 and compatible. The NVRAM is organized in 2048 banks of 2kB each, numbered #000 to #7FF. Banks are selected by writing #00 - #FF into $C0N0 and 0-7 into #C0N1, where N = 8 + [slot number]. When writing to $C0Nx at the same time the NVRAM chips are also enabled. When a bank is selected, its content is seen in the address space $C800-$CFFF. To de-enable the NVRAM drive a write must be performed to address $CFFF or reset executed. If a user program is accessing the card, it is important that at the end a write is performed to $CFFF so that the card is deactivated and does not conflict with other hardware, which is using the same address space. The bootloader is programmed in the highest 256 bytes of the last chip. The boot loader is always available at addresses $CM00-$CMFF, where M = [slot number]. The bootloader can also be seen at addresses $CF00-$CFFF of bank #7FF. The image contains a ProDOS volume which is loaded by the boot loader. Additional firmware resides in ProDOS Block $01. The card requires the presence of 64kB AUX memory, otherwise will be read only. Recommended installation is in Slot 7. The boot loader has functionality that it captures the boot sequence of the computer and loads ProDOS.

As of version 5.0 a design change was implemented - a write RAM buffer was added onboard to avoid using the system memory for buffering writes. This required a firmware update, which was also optimized to be now only 512 bytes large and fits completely in block 0001. The minimum firmware version is 42. A sencond PLD is used to combine the functions of the 'LS133 and 'LS138.

Version 5.2 is the same as 5.0, except that all small chips are hidden under the big DIP memory chips.

Copyright (c) 2024 Ralle Palaveev All rights reserved.

Redistribution and use in source, binary, and manufactured forms, with or without modification, are permitted provided that the following conditions are met:
1. Redistributions of source code and design files must retain the above copyright notice, this list of conditions and the following disclaimer.
2. Redistributions in binary or manufactured form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
3. All advertising materials mentioning features or use of this software or hardware must display the following acknowledgement: This product includes software and hardware developed by Ralle Palaveev.
4. Neither the name of Ralle Palaveev nor the names of its contributors may be used to endorse or promote products derived from this software or hardware without specific prior written permission.

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
