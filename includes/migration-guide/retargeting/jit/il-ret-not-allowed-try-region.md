### <a name="il-ret-not-allowed-in-a-try-region"></a>IL není povoleno v oblasti, opakujte vrácená hodnota:

|   |   |
|---|---|
|Podrobnosti|Na rozdíl od kompilátoru za běhu JIT64 RyuJIT (používá se v rozhraní .NET 4.6) neumožňuje IL vrácená hodnota instrukce v oblasti, opakujte. Vrácení z oblasti zkuste je zakázaná specifikací standardy ECMA-335 a žádné známé spravované kompilátoru vygeneruje taková IL. Kompilátor JIT64 však provede takové IL, pokud je generována pomocí reflexe emitování.|
|Návrh|Vytváří-li aplikaci IL zahrnující ret opcode v oblasti, opakujte, aplikace mohou být zaměřeny na rozhraní .NET 4.5 pomocí staré JIT a zamezit tak toto rozdělení. Alternativně může být aktualizován generovaného IL vrátit po oblasti opakujte.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna orientace|

