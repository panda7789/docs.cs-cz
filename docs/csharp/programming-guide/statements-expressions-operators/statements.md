---
title: Příkazy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 68f7f799ebbfe52c99820083eb22761c79f66483
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339524"
---
# <a name="statements-c-programming-guide"></a>Příkazy (Průvodce programováním v C#)
Akce, které program trvá jsou vyjádřeny v příkazech. Běžné akce zahrnují deklarace proměnné, přiřazení hodnoty, volání metod ve smyčce přes kolekce a vytvoření větve na jeden nebo jiný blok kódu, v závislosti na dané podmínce. Pořadí, ve kterém jsou příkazy prováděna v programu se nazývá tok řízení toku spouštění. Tok řízení se může lišit při každém spuštění programu, v závislosti na tom, jak se program reaguje na vstup obdrží za běhu.  
  
 Příkaz může obsahovat jeden řádek kódu, který končí středníkem nebo řadu jeden řádek příkazy v bloku. Blok příkazu ohraničeno {} závorky a může obsahovat vnořené bloky. Následující kód ukazuje dva příklady příkazů jeden řádek a zároveň se zablokují Víceřádkový příkaz:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Typy příkazů  
 Následující tabulka uvádí různé typy příkazů v C# a jejich přidružené klíčová slova, s odkazy na témata, které obsahují další informace:  
  
|Kategorie|Klíčová slova jazyka C# / poznámky|  
|--------------|---------------------------|  
|Deklarační příkazy|Příkaz deklarace zavádí novou proměnnou nebo konstanta. Deklarace proměnné můžete volitelně přiřadit hodnotu proměnné. V deklaraci konstantní se vyžaduje přiřazení.<br /><br /> [!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|Příkazy výrazu|Příkazy výrazu, které vypočítat hodnotu musí uložit hodnotu proměnné.<br /><br /> [!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Příkazy výběru](../../../csharp/language-reference/keywords/selection-statements.md)|Příkazy výběru umožňují větvení do jiné části kódu, v závislosti na jeden nebo více zadaných podmínek. Další informace naleznete v následujících tématech:<br /><br /> [Pokud](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [přepínač](../../../csharp/language-reference/keywords/switch.md), [případu](../../../csharp/language-reference/keywords/switch.md)|  
|[Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)|Příkazy iterace umožňují procházení kolekce jako pole nebo proveďte stejnou sadu příkazů opakovaně, dokud nebude splněna zadaná podmínka. Další informace naleznete v následujících tématech:<br /><br /> [proveďte](../../../csharp/language-reference/keywords/do.md), [pro](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [v](../../../csharp/language-reference/keywords/foreach-in.md), [při](../../../csharp/language-reference/keywords/while.md)|  
|[Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)|Jump – příkazy přenos řízení na jinou část kódu. Další informace naleznete v následujících tématech:<br /><br /> [rozdělení](../../../csharp/language-reference/keywords/break.md), [pokračovat](../../../csharp/language-reference/keywords/continue.md), [výchozí](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Příkazy zpracování výjimek](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Příkazy zpracování výjimek umožňují elegantně zotavit z výjimečných podmínek, ke kterým dochází za běhu. Další informace naleznete v následujících tématech:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch –](../../../csharp/language-reference/keywords/try-catch.md), [try-finally –](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally –](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Zaškrtnuto a nezaškrtnuto příkazy umožňují určit, zda číselné operace mohou způsobit přetečení při výsledek je uložen v proměnné, která je příliš malá, aby udržení výslednou hodnotu. Další informace najdete v tématu [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) a [nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` – Příkaz|Pokud označíte metodu s [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor, můžete použít [await](../../../csharp/language-reference/keywords/await.md) operátor v metodě. Při řízení dosáhnou `await` výrazu v asynchronní metody řízení vrátí volajícímu a průběh v metodě je pozastaveno, dokud dokončení awaited úlohy. Po dokončení úlohy provádění může pokračovat v metodě.<br /><br /> Jednoduchý příklad, najdete v části "Asynchronní metody" [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` – Příkaz|Iterátor provede vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý element, jeden v čase. Když `yield return` příkaz je dosaženo, uloží je aktuální umístění v kódu. Při iteraci volání při příštím spuštění restartování z tohoto umístění.<br /><br /> Další informace najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).|  
|`fixed` – Příkaz|Příkazu pevnou zabrání uvolňování přemístění mobilní proměnné. Další informace najdete v tématu [pevné](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` – Příkaz|Příkaz Zámek umožňuje omezit přístup k bloky kódu pouze jedno vlákno najednou. Další informace najdete v tématu [zámku](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Příkaz s popiskem|Můžete poskytnout příkaz štítek a potom pomocí [goto](../../../csharp/language-reference/keywords/goto.md) – klíčové slovo chcete přejít na příkaz s popiskem. (Podívejte se na příklad na následujícím řádku.)|  
|Prázdný příkaz|Prázdný příkaz se skládá z jedné středníkem. To se nic nestane. a lze použít v místech, kde příkazu je požadováno, ale není nutné provádět žádnou akci. Následující příklady ukazují dva používá pro prázdný příkaz:<br /><br /> [!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## <a name="embedded-statements"></a>Vložené – příkazy  
 Některé příkazy, včetně [provést](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), [pro](../../../csharp/language-reference/keywords/for.md), a [foreach](../../../csharp/language-reference/keywords/foreach-in.md), mají embedded příkaz, který následuje, je vždy. Tato vložená příkaz může být jediný příkaz nebo více příkazů ohraničená {} hranaté závorce v bloku příkazu. Ani jeden řádek vložený příkazy můžou být uzavřená v {} závorky, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Vložené příkazu, který není uzavřený v {} závorky nemůže být deklarace příkaz nebo příkaz s popiskem. To je ukázáno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Příkaz embedded PUT v bloku postup řešení chyby:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>Vnořené bloky  
 Příkaz bloky mohou být použity, jak je znázorněno v následujícím kódu:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Nedostupný – příkazy  
 Pokud kompilátor zjistí, že tok řízení nikdy dosáhnout konkrétní příkaz za žádných okolností, bude ho vytvořit upozornění CS0162, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>Související oddíly  
  
-   [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Výrazy](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
