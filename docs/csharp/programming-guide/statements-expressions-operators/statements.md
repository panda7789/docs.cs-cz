---
title: Příkazy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 12c4561e9e2c2a9e3a211351b70fd83b8ca7bccd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640846"
---
# <a name="statements-c-programming-guide"></a>Příkazy (Průvodce programováním v C#)
Akce, které přijímá programu jsou vyjádřeny v příkazech. Běžné akce zahrnují deklarování proměnných, přiřazování hodnot, volání metod ve smyčce přes kolekce a vytváření větví do jednoho nebo jiného bloku kódu, v závislosti na danou podmínku. Pořadí, ve kterém jsou spouštěny příkazy v programu v jazyce se nazývá tok řízení toku provádění. Tok řízení se může lišit při každém spuštění programu, v závislosti na tom, jak program reaguje na vstup, že bude dostávat v době běhu.  
  
 Příkaz se může skládat z jediný řádek kódu, který končí středníkem nebo řady jedním řádkem příkazy v bloku. Blok příkazů, který je uzavřen v {} složené závorky a může obsahovat vnořené bloky. Následující kód ukazuje dva příklady příkazů jedním řádkem a blok příkazů více řádky:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Typy příkazů  
 V následující tabulce jsou uvedeny různé typy příkazů v C# a jejich související klíčová slova, s odkazy na témata, které obsahují další informace:  
  
|Kategorie|Klíčová slova jazyka C# / poznámky|  
|--------------|---------------------------|  
|[Příkazy deklarace](#declaration-statements)|Příkazu deklarace zavádí novou proměnnou nebo konstantu. Deklarace proměnné volitelně přiřadit hodnotu k proměnné. V deklaraci konstanty se vyžaduje přiřazení.|  
|[Příkazy výrazů](expressions.md)|Příkazy výrazů, které vypočítá hodnotu uložit hodnotu do proměnné. Další informace najdete v tématu [příkazy výrazů](#expression-statements).|  
|[Příkazy výběru](../../../csharp/language-reference/keywords/selection-statements.md)|Příkazy výběru umožňují větve na různé části kódu, v závislosti na jeden nebo více zadaných podmínek. Další informace naleznete v následujících tématech:<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [switch](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)|Příkazy iterace vám umožní projít kolekce například pole nebo opakovaně provádět stejnou sadu příkazů, dokud je zadaná podmínka splněna. Další informace naleznete v následujících tématech:<br /><br /> [proveďte](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [v](../../../csharp/language-reference/keywords/foreach-in.md), [při](../../../csharp/language-reference/keywords/while.md)|  
|[Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)|Přenos řízení příkazy přejděte na jinou část kódu. Další informace naleznete v následujících tématech:<br /><br /> [Konec](../../../csharp/language-reference/keywords/break.md), [pokračovat](../../../csharp/language-reference/keywords/continue.md), [výchozí](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Příkazy zpracování výjimek umožňují elegantně zotavit z výjimečných podmínek, ke kterým dochází za běhu. Další informace naleznete v následujících tématech:<br /><br /> [vyvolat](../../../csharp/language-reference/keywords/throw.md), [bloku try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [konstrukce try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Zaškrtnuto a nezaškrtnuto příkazy umožňují určete, jestli jsou číselné operace může způsobit přetečení, pokud výsledek je uložen v proměnné, která je příliš nízká k uložení výslednou hodnotu. Další informace najdete v tématu [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) a [Nekontrolovaná](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` – Příkaz|Pokud určíte metodu s [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor, můžete použít [await](../../../csharp/language-reference/keywords/await.md) operátor v metodě. Když ovládací prvek dosáhne `await` výrazu v asynchronní metodě, ovládací prvek vrátí volajícímu a průběh v metodě je pozastavený, až do dokončení očekávané úlohy. Po dokončení úlohy se provádění může pokračovat v metodě.<br /><br /> Jednoduchý příklad, najdete v části "Asynchronní metody" [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` – Příkaz|Iterátor provádí vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield return](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit vždy jeden prvek v čase. Když `yield return` je dosažen příkaz, se uloží aktuální umístění v kódu. Provádění je restartováno z tohoto umístění, při příštím volání iterátoru.<br /><br /> Další informace najdete v tématu [iterátory](../../../csharp/programming-guide/concepts/iterators.md).|  
|`fixed` – Příkaz|Fixed – příkaz zabraňuje přemístění proměnné přesouvatelný systému uvolňování paměti. Další informace najdete v tématu [oprava](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` – Příkaz|Příkaz lock umožňuje omezit přístup k bloky kódu, který pouze jedno vlákno v čase. Další informace najdete v tématu [Zámek](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Příkaz s popiskem|Můžete poskytnout příkaz popisek a potom použít [goto](../../../csharp/language-reference/keywords/goto.md) – klíčové slovo pro přechod na příkaz s popiskem. (Viz příklad na následujícím řádku.)|  
|[Prázdný příkaz](#the-empty-statement)|Prázdný příkaz se skládá z jedné středník. Nemá žádný účinek a je možné na místech, kde příkaz je povinný, ale potřeba provádět žádnou akci.|  
  
## <a name="declaration-statements"></a>Příkazy deklarace

Následující kód ukazuje příklady deklarace proměnných a nemusíte počátečního přiřazení a deklarace konstanty s inicializací nezbytné.

[!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]

## <a name="expression-statements"></a>Příkazy výrazů

Následující kód ukazuje příklady příkazy výrazů, včetně přiřazení, vytváření objektů přiřazení a volání metody.

[!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]

## <a name="the-empty-statement"></a>Prázdný příkaz

Následující příklady ukazují dvě použití pro prázdný příkaz:

[!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]

## <a name="embedded-statements"></a>Vložené příkazy

 Některé příkazy, včetně [proveďte](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), [pro](../../../csharp/language-reference/keywords/for.md), a [foreach](../../../csharp/language-reference/keywords/foreach-in.md), mají vloženým příkazem, který následuje, je vždy. Tento příkaz vložený může být jeden příkaz nebo více příkazů uzavřených podle {} hranaté závorce v bloku příkazu. Ještě jeden řádek integrovaných prohlášení, můžou být uzavřená v {} hranaté závorky, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Vloženým příkazem, který není uzavřen v {} hranaté závorky nemůže být v příkazu deklarace ani příkaz s popiskem. To je ukázáno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Vloženým příkazem umístěte do bloku, chcete-li vyřešit chybu:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>Vnořené příkazy bloky  
 Blok příkazu mohou být vnořené, jak je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Nedosažitelný příkazy  
 Pokud kompilátor zjistí, že tok řízení můžete nikdy nedorazí konkrétní příkaz za žádných okolností, vygeneruje upozornění CS0162, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>Související oddíly  
  
-   [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Výrazy](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
