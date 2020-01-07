---
title: Příkazy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 8cac8144516666690715ff4e0bdc526c365765f5
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635103"
---
# <a name="statements-c-programming-guide"></a>Příkazy (Průvodce programováním v C#)

Akce, které program přijímá, jsou vyjádřeny v příkazech. Mezi běžné akce patří deklarace proměnných, přiřazování hodnot, volání metod, smyčky přes kolekce a větvení do jednoho nebo jiného bloku kódu v závislosti na dané podmínce. Pořadí, ve kterém se příkazy spouštějí v programu, se nazývá tok řízení nebo tok provádění. Tok řízení se může při každém spuštění programu lišit v závislosti na tom, jak program reaguje na vstup, který obdrží v době běhu.

Příkaz se může skládat z jediného řádku kódu, který končí středníkem, nebo řadou jednoduchých příkazů v bloku. Blok příkazu je uzavřený v {} závorkách a může obsahovat vnořené bloky. Následující kód ukazuje dva příklady jednoduchých řádků a blok víceřádkových příkazů:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Typy příkazů

V následující tabulce jsou uvedeny různé typy příkazů v C# a jejich přidružená klíčová slova s odkazy na témata, která obsahují další informace:

|Kategorie|C#Klíčová slova a poznámky|
|--------------|---------------------------|
|[Příkazy deklarace](#declaration-statements)|Příkaz deklarace zavádí novou proměnnou nebo konstantu. Deklarace proměnné může volitelně přiřadit hodnotu proměnné. V deklaraci konstanty je vyžadováno přiřazení.|
|[Příkazy výrazu](expressions.md)|Příkazy výrazů, které počítají hodnotu, musí ukládat hodnotu v proměnné. Další informace naleznete v tématu [Expression Statements](#expression-statements).|
|Příkazy výběru|Příkazy výběru umožňují vytvořit větev do různých oddílů kódu v závislosti na jedné nebo více zadaných podmínkách. Další informace naleznete v následujících tématech: <ul><li>[if](../../language-reference/keywords/if-else.md)</li><li>[else](../../language-reference/keywords/if-else.md)</li><li>[switch](../../language-reference/keywords/switch.md)</li><li>[case](../../language-reference/keywords/switch.md)</li></ul>|
|Příkazy iterace|Příkazy iterace umožňují cyklicky procházet kolekcemi, jako jsou pole, nebo provádět stejnou sadu příkazů opakovaně, dokud není splněna zadaná podmínka. Další informace naleznete v následujících tématech: <ul><li>[do](../../language-reference/keywords/do.md)</li><li>[for](../../language-reference/keywords/for.md)</li><li>[foreach](../../language-reference/keywords/foreach-in.md)</li><li>[in](../../language-reference/keywords/foreach-in.md)</li><li>[while](../../language-reference/keywords/while.md)</li></ul>|
|Jump – příkazy|Příkazy skoku přenášejí řízení na jiný oddíl kódu. Další informace naleznete v následujících tématech: <ul><li>[break](../../language-reference/keywords/break.md)</li><li>[continue](../../language-reference/keywords/continue.md)</li><li>[default](../../language-reference/keywords/switch.md)</li><li>[goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Příkazy zpracování výjimek|Příkazy zpracování výjimek umožňují bezproblémové obnovení z mimořádných podmínek, ke kterým dojde v době běhu. Další informace naleznete v následujících tématech: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Zaškrtnuto a nezaškrtnuto](../../language-reference/keywords/checked-and-unchecked.md)|Zaškrtnuté a nezaškrtnuté příkazy umožňují určit, jestli numerické operace můžou způsobit přetečení, pokud je výsledek uložený v proměnné, která je moc malá pro uložení výsledné hodnoty. Další informace naleznete v tématu [checked](../../language-reference/keywords/checked.md) a [unchecked](../../language-reference/keywords/unchecked.md).|
|Příkaz `await`|Pokud označíte metodu pomocí modifikátoru [Async](../../language-reference/keywords/async.md) , můžete použít operátor [await](../../language-reference/operators/await.md) v metodě. Když ovládací prvek dosáhne `await` výrazu v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh v metodě je pozastaven až do dokončení očekávané úlohy. Po dokončení úlohy může provádění pokračovat v metodě.<br /><br /> Jednoduchý příklad naleznete v části [metody](../classes-and-structs/methods.md)"asynchronní metody". Další informace naleznete v tématu [asynchronní programování s Async a await](../concepts/async/index.md).|
|Příkaz `yield return`|Iterátor provádí vlastní iteraci v kolekci, jako je například seznam nebo pole. Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého elementu v jednom okamžiku. Když je dosaženo příkazu `yield return`, aktuální umístění v kódu je zapamatovatelné. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.<br /><br /> Další informace najdete v tématu [iterátory](../concepts/iterators.md).|
|Příkaz `fixed`|Příkaz fixed brání systému uvolňování paměti v přemístění pohyblivé proměnné. Další informace naleznete v tématu [fixed](../../language-reference/keywords/fixed-statement.md).|
|Příkaz `lock`|Příkaz lock umožňuje omezit přístup k blokům kódu pouze na jedno vlákno v jednom okamžiku. Další informace najdete v tématu [Lock](../../language-reference/keywords/lock-statement.md).|
|Příkazy s popiskem|Příkazu můžete předat popisek a potom pomocí klíčového slova [goto](../../language-reference/keywords/goto.md) přejít na příkaz s popiskem. (Podívejte se na příklad v následujícím řádku.)|
|[Prázdný příkaz](#the-empty-statement)|Prázdný příkaz se skládá z jednoho středníku. Nedělá nic a lze ho použít na místech, kde je vyžadován příkaz, ale není nutné provádět žádnou akci.|

## <a name="declaration-statements"></a>Příkazy deklarace

Následující kód ukazuje příklady deklarací proměnných s a bez počátečního přiřazení a konstantní deklarace s nezbytnou inicializací.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Příkazy výrazu

Následující kód ukazuje příklady příkazů výrazu, včetně přiřazení, vytvoření objektu s přiřazením a volání metody.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Prázdný příkaz

Následující příklady znázorňují dva způsoby použití prázdného příkazu:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Vložené příkazy

Některé příkazy, včetně [do](../../language-reference/keywords/do.md), [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md)a [foreach](../../language-reference/keywords/foreach-in.md), vždy mají vložený příkaz, který je následován. Tento vložený příkaz může být buď jeden příkaz, nebo více příkazů, které jsou uzavřeny {} závorkami v bloku příkazu. I vložené příkazy s jedním řádkem mohou být uzavřeny do závorek {}, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Vložený příkaz, který není uzavřen v závorkách {}, nemůže být příkaz deklarace ani příkaz s popiskem. To je ukázáno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Chcete-li opravit chybu, vložte vložený příkaz do bloku.

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>Vnořené bloky příkazů

Bloky příkazu mohou být vnořené, jak je znázorněno v následujícím kódu:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Nedosažitelné příkazy

Pokud kompilátor určí, že tok řízení nemůže nikdy dosáhnout konkrétního příkazu za žádných okolností, vytvoří upozornění CS0162, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkazy](~/_csharplang/spec/statements.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Klíčová slova příkazu](../../language-reference/keywords/statement-keywords.md)  
- [Výrazy](expressions.md)  
