---
title: Příkazy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: d50b50bb291d0d087015ea5bd075ae90ced66ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711932"
---
# <a name="statements-c-programming-guide"></a>Příkazy (Průvodce programováním v C#)

Akce, které program provede, jsou vyjádřeny v příkazech. Běžné akce zahrnují deklarování proměnných, přiřazování hodnot, volání metod, opakování kolekcí a větvení do jednoho nebo jiného bloku kódu v závislosti na dané podmínce. Pořadí, ve kterém jsou příkazy provedeny v programu se nazývá tok řízení nebo toku provádění. Tok řízení se může lišit při každém spuštění programu v závislosti na tom, jak program reaguje na vstup, který obdrží za běhu.

Příkaz se může skládat z jednoho řádku kódu, který končí středníkem, nebo z řady jednořádkových příkazů v bloku. Blok příkazu je {} uzavřen v závorkách a může obsahovat vnořené bloky. Následující kód ukazuje dva příklady jednořádkových příkazů a víceřádkový blok příkazu:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Typy výpisů

V následující tabulce jsou uvedeny různé typy příkazů v systému C# a jejich přidružená klíčová slova s odkazy na témata, která obsahují další informace:

|Kategorie|C# klíčová slova / poznámky|
|--------------|---------------------------|
|[Prohlášení](#declaration-statements)|Prohlášení prohlášení zavádí novou proměnnou nebo konstantu. Deklarace proměnné může volitelně přiřadit hodnotu proměnné. V konstantní deklaraci je požadováno přiřazení.|
|[Příkazy výrazu](expressions.md)|Příkazy výrazu, které počítají hodnotu, musí hodnotu uložit do proměnné. Další informace naleznete v [tématu Expression Statements](#expression-statements).|
|Příkazy výběru|Příkazy výběru umožňují větvení do různých částí kódu v závislosti na jedné nebo více zadaných podmínkách. Další informace najdete v následujících tématech: <ul><li>[Pokud](../../language-reference/keywords/if-else.md)</li><li>[Jiného](../../language-reference/keywords/if-else.md)</li><li>[Přepnout](../../language-reference/keywords/switch.md)</li><li>[Případě](../../language-reference/keywords/switch.md)</li></ul>|
|Příkazy iterace|Iterace příkazy umožňují procházet kolekce, jako jsou pole nebo provádět stejnou sadu příkazů opakovaně, dokud není splněna zadaná podmínka. Další informace najdete v následujících tématech: <ul><li>[dělat](../../language-reference/keywords/do.md)</li><li>[Pro](../../language-reference/keywords/for.md)</li><li>[Foreach](../../language-reference/keywords/foreach-in.md)</li><li>[In](../../language-reference/keywords/foreach-in.md)</li><li>[Zatímco](../../language-reference/keywords/while.md)</li></ul>|
|Jump – příkazy|Přeskočit příkazy převést řízení do jiné části kódu. Další informace najdete v následujících tématech: <ul><li>[Přestávce](../../language-reference/keywords/break.md)</li><li>[continue](../../language-reference/keywords/continue.md)</li><li>[Výchozí](../../language-reference/keywords/switch.md)</li><li>[Goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Příkazy zpracování výjimek|Příkazy zpracování výjimek umožňují řádně zotavit z výjimečných podmínek, ke kterým dochází v době běhu. Další informace najdete v následujících tématech: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Zaškrtnuto a nezaškrtnuto](../../language-reference/keywords/checked-and-unchecked.md)|Zaškrtnuté a nezaškrtnuté příkazy umožňují určit, zda mají číselné operace povoleno způsobit přetečení, pokud je výsledek uložen v proměnné, která je příliš malá pro uložení výsledné hodnoty. Další informace naleznete v [tématu zaškrtnuté](../../language-reference/keywords/checked.md) a [nezaškrtnuté](../../language-reference/keywords/unchecked.md).|
|Prohlášení `await`|Pokud označíte metodu s [asynchronním](../../language-reference/keywords/async.md) modifikátorem, můžete použít operátor [await](../../language-reference/operators/await.md) v metodě. Když ovládací prvek `await` dosáhne výrazu v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh metody je pozastaven, dokud nebude dokončena očekávaná úloha. Po dokončení úlohy může spuštění pokračovat v metodě.<br /><br /> Jednoduchý příklad naleznete v části Metody asynchronních metod [.](../classes-and-structs/methods.md) Další informace naleznete [v tématu Asynchronní programování s async a await](../concepts/async/index.md).|
|Prohlášení `yield return`|Iterátor provádí vlastní iteraci přes kolekci, jako je například seznam nebo pole. Iterátor používá yield [return](../../language-reference/keywords/yield.md) prohlášení vrátit každý prvek jeden po druhém. Po `yield return` dosažení příkazu je zapamatováno aktuální umístění v kódu. Spuštění je restartován z tohoto umístění při restartování iterátoru při příštím volání.<br /><br /> Další informace naleznete v tématu [Iterators](../concepts/iterators.md).|
|Prohlášení `fixed`|Příkaz fixed zabraňuje systému uvolňování paměti v přemístění pohyblivé proměnné. Další informace naleznete v [tématu pevné](../../language-reference/keywords/fixed-statement.md).|
|Prohlášení `lock`|Příkaz lock umožňuje omezit přístup k blokům kódu pouze na jedno vlákno najednou. Další informace naleznete v tématu [lock](../../language-reference/keywords/lock-statement.md).|
|Příkazy s popiskem|Příkaz můžete dát popisek a potom pomocí klíčového slova [goto](../../language-reference/keywords/goto.md) přejít na označený příkaz. (Viz příklad v následujícím řádku.)|
|[Prázdný příkaz](#the-empty-statement)|Prázdný příkaz se skládá z jednoho středníku. Neprovádí žádnou akci a lze jej použít v místech, kde je vyžadován příkaz, ale není třeba provádět žádnou akci.|

## <a name="declaration-statements"></a>Prohlášení

Následující kód ukazuje příklady deklarací proměnných s počátečním přiřazením a bez něj a konstantní deklarace s potřebnou inicializací.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Příkazy výrazu

Následující kód ukazuje příklady příkazů výrazu, včetně přiřazení, vytváření objektů s přiřazením a vyvolání metody.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Prázdný příkaz

Následující příklady ukazují dvě použití pro prázdný příkaz:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Vložené příkazy

Některé příkazy, včetně [do](../../language-reference/keywords/do.md), [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md), a [foreach](../../language-reference/keywords/foreach-in.md), mají vždy vložený příkaz, který je následuje. Tento vložený příkaz může být buď jeden příkaz {} nebo více příkazů uzavřených závorky v bloku příkazu. Dokonce i jednořádkové vložené příkazy mohou být uzavřeny v {} závorkách, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Vložený příkaz, který není {} uzavřen v závorkách, nemůže být příkazem deklarace nebo příkazem s popiskem. To je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Vložený příkaz vložte do bloku, abyste chybu opravili:

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>Vnořené bloky příkazu

Bloky výkazu mohou být vnořeny, jak je znázorněno v následujícím kódu:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Nedostupných výkazů

Pokud kompilátor zjistí, že tok řízení nemůže nikdy dosáhnout konkrétní hovado za žádných okolností, vytvoří upozornění CS0162, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Příkazy](~/_csharplang/spec/statements.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Klíčová slova](../../language-reference/keywords/statement-keywords.md)  
- [Výrazy](expressions.md)  
