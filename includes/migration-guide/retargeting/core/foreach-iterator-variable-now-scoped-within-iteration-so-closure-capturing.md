### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Iterační proměnná foreach je nyní vymezeno v rámci iterace, tak, aby byly zachytávající sémantiku uzavření jiný (v jazyce C# 5)

|   |   |
|---|---|
|Podrobnosti|Od verze C# 5 (Visual Studio 2012) <code>foreach</code> oborem iterační proměnné v rámci iterace. To může způsobit přerušení, pokud kód byl dříve v závislosti na tom proměnné tak nebudou zahrnuty do <code>foreach</code>na ukončení. Příznak této změny je, že proměnná iterátoru předat delegáta je považován za se vytvoří hodnota má v době delegáta, nikoli hodnotu, kterou má v době, kdy je vyvolán delegát.|
|Návrh|V ideálním případě by měl kód aktualizovat očekávat nové chování kompilátoru. Pokud původní sémantiku, iterační proměnná, lze nahradit zvláštní proměnná, která je explicitně umístěn mimo obor smyčky.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Mění se cílení|

