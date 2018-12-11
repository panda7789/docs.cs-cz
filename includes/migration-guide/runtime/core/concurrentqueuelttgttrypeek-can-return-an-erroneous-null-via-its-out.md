### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. Metodě TryPeek může vrátit chybné null prostřednictvím jeho výstupní parametr

|   |   |
|---|---|
|Podrobnosti|V některých scénářích s více procesy <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> může vrátit hodnotu true, ale vyplnit výstupní parametr s hodnotou null (místo hodnoty správné, nahlédnout).|
|Doporučení|Tento problém je vyřešen v rozhraní .NET Framework 4.5.1. Upgrade na tento rámec se vyřešit problém.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

