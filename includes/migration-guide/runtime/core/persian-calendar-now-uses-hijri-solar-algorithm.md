### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perského kalendáře teď používá algoritmus sluneční hidžra

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> třída používá algoritmus sluneční hidžra. Převádění kalendářní data mezi <xref:System.Globalization.PersianCalendar?displayProperty=name> a ostatních kalendářích, které mohou mít výsledek poněkud liší od verze rozhraní .NET Framework 4.6 pro data starší než 1 800 nebo pozdější než 2023 (gregoriánský). Navíc <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je nyní <code>March 22, 0622</code> místo <code>March 21, 0622</code>.|
|Návrh|Upozorňujeme, že některé data časná a pozdní můžou mírně lišit při použití PersianCalendar v rozhraní .NET Framework 4.6. Navíc při serializaci kalendářní data mezi procesy, které se může spustit na různé verze rozhraní .NET Framework, neukládejte je jako PersianCalendar datum řetězce (protože tyto hodnoty mohou být odlišné).|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

