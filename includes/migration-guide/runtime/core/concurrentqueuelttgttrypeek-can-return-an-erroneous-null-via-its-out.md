### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. TryPeek může vrátit chybné null přes jeho výstupní parametr

|   |   |
|---|---|
|Podrobnosti|V některých scénářích Vícevláknová <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> vrátila hodnotu true, ale naplnit výstupní parametr s hodnotou null (namísto hodnoty správný, provedla).|
|Návrh|Tento problém vyřešen v rozhraní .NET Framework 4.5.1. Upgrade na dané platformy, se tento problém vyřešit.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

