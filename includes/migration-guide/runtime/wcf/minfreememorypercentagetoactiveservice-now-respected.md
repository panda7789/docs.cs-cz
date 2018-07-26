### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Nyní je dodržena MinFreeMemoryPercentageToActiveService

|   |   |
|---|---|
|Podrobnosti|Toto nastavení vytváří minimální velikost paměti, které musí být k dispozici na serveru, před aktivací služby WCF. Slouží k zabránění <xref:System.OutOfMemoryException?displayProperty=name> výjimky. Toto nastavení v rozhraní .NET Framework 4.5, nemělo žádný vliv. V rozhraní .NET Framework 4.5.1 nezaznamenáme nastavení.|
|Návrh|Pokud volné paměti dostupné na webovém serveru je nižší než procento definované v nastavení konfigurace, dojde k výjimce. Některé služby WCF, které úspěšně spuštěny a byl spuštěn v prostředí omezené paměti teď může selhat.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|

