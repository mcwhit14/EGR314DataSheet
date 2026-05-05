# Reflection

## Review of Module's Success

Overall, I was able to get my module working and meet the main requirement of integrating the ESP32 with the distance sensor and producing usable data. By the end of the project, the sensor was functioning, and I could verify its readings and behavior in the system. I also successfully designed and assembled a PCB that powered the ESP32 and supported communication with the sensor.

However, not everything was fully optimized. Some components in my original design were either not integrated as well as they could have been or caused issues during testing. Power regulation and stability were a challenge at times, and there were points where I had to work around limitations instead of having a fully clean design. Even though the system worked, there are definitely areas that could be improved in a future revision.

---

## Microcontroller/Module Startup Tip

- Always test your sensor on a breadboard before committing to a PCB  
- Double check ESP32 pin mappings before routing anything  
- Make sure your voltage regulator setup is correct and stable  
- Use simple test code first (like scanning or printing values)  
- Don’t assume the sensor is broken — check wiring and power first  
- Flashing issues are common, so verify boot mode and connections early  
- Keep things simple at the start and build up slowly  
- Add more test points and auxiliary pins than you think you need  

---

## Lessons Learned

One of the biggest things I learned from this project is that getting a system to work is very different from designing it on paper. Even when everything looks correct in the schematic, small issues like wiring, power instability, or pin mismatches can completely stop the system from working. I also learned that debugging hardware takes time and patience, and you have to be systematic instead of guessing.

Power design turned out to be more important than I expected. If the voltage regulator or power distribution is not stable, nothing else will behave correctly. I also realized how important it is to verify each part of the system step by step instead of trying to get everything working at once.

Another major lesson was layout awareness. Things like not routing traces under antennas, keeping signal lines clean, and thinking about physical placement actually matter in real designs. These are details that are easy to ignore at first but become important once you start testing real hardware.

I also learned that you can never have enough test points or extra access to signals. There were multiple times where debugging would have been much easier if I had included more points to probe or additional pins to work with.

Working through this project showed me that iteration is part of the process. The first design is almost never perfect, and improvements come from actually building and testing the system. Overall, this project gave me a much better understanding of how hardware, software, and physical design all come together in a real embedded system.

---

## Recommendations for Future Students

1. Start early and expect debugging to take longer than you think, especially with hardware.  
2. Test every component individually before putting it on your PCB.  
3. Pay close attention to power design and voltage regulation, since it affects everything else.  
4. Add extra test points and accessible pins because they will save you during debugging.  
5. Keep your first design simple and focus on getting it working before trying to optimize or add features.
