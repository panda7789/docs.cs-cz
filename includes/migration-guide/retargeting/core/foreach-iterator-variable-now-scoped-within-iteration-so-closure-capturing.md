### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Foreach iterator proměnné je nyní vymezeno v rámci iterace, takže zaznamenávání sémantiku uzavření se liší (na 5 C#)

|   |   |
|---|---|
|Podrobnosti|Od verze jazyka C# 5 (Visual Studio 2012), <code>foreach</code> iterační proměnné jsou vymezeny během iterace. To může způsobit přerušení, pokud kód byl dříve závisí na proměnné nesmí být zahrnuti do <code>foreach</code>je ukončení. Tento příznak tuto změnu je, že proměnná iterator předaný delegáta je zpracovaná jako hodnota má v době delegát je vytvořena, nikoli hodnotu, kterou má v době, kdy je vyvolán delegát.|
|Návrh|V ideálním případě by měl kód aktualizovat očekávat nové chování kompilátoru. Pokud sémantiku starý, proměnnou iterator můžete nahradit samostatné proměnnou, která je explicitně umístit mimo obor smyčky.|
|Rozsah|Hlavní|
|Version|4.5|
|Typ|Změna orientace|

