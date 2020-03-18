---
title: Místní funkce – programovací příručka Jazyka C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170232"
---
# <a name="local-functions-c-programming-guide"></a>Místní funkce (Průvodce programováním jazyka C#)

Počínaje c# 7.0, C# podporuje *místní funkce*. Místní funkce jsou soukromé metody typu, které jsou vnořeny v jiném členu. Mohou být volány pouze z jejich obsahující člen. Místní funkce lze deklarovat a volat z:

- Metody, zejména metody iterátoru a asynchronní metody
- Konstruktory
- Přístupové objekty vlastností
- Přistupující přístupové akce
- Anonymní metody
- Výrazy lambda
- Finalizační metody
- Další místní funkce

Místní funkce však nelze deklarovat uvnitř člena s výrazem.

> [!NOTE]
> V některých případech můžete použít výraz lambda k implementaci funkcí podporovaných také místní funkcí. Porovnání naleznete v tématu [Místní funkce ve srovnání s výrazy Lambda](../../local-functions-vs-lambdas.md).

Místní funkce, aby záměr kódu jasné. Každý, kdo čte váš kód, vidí, že metoda není volatelná s výjimkou metody obsahující. Pro týmové projekty také znemožňují jinému vývojáři chybně volat metodu přímo z jiných míst ve třídě nebo struktuře.

## <a name="local-function-syntax"></a>Syntaxe místní funkce

Místní funkce je definována jako vnořená metoda uvnitř obsahujícího člena. Jeho definice má následující syntaxi:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Místní funkce mohou používat [asynchronní](../../language-reference/keywords/async.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.

Všimněte si, že všechny místní proměnné, které jsou definovány v obsahující člen, včetně jeho parametry metody, jsou přístupné v místní funkci.

Na rozdíl od definice metody nemůže definice místní funkce obsahovat modifikátor přístupu člena. Vzhledem k tomu, že všechny místní funkce `private` jsou soukromé, včetně modifikátoru přístupu, například klíčové slovo, generuje chybu kompilátoru CS0106, "Modifikátor 'private' není platný pro tuto položku.

> [!NOTE]
> Před C# 8.0 místní funkce `static` nemohou obsahovat modifikátor. Včetně `static` klíčového slova generuje chybu kompilátoru CS0106, "Modifikátor 'statické' není platný pro tuto položku."

Kromě toho atributy nelze použít na místní funkci nebo na její parametry a parametry typu.

Následující příklad definuje místní funkci `AppendPathSeparator` s názvem, která `GetText`je soukromá pro metodu s názvem :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Místní funkce a výjimky

Jednou z užitečných funkcí místních funkcí je, že mohou povolit výjimky na povrch okamžitě. Pro metodu iterátory výjimky jsou zobrazeny pouze v případě, že vrácená sekvence je výčtu a ne při iterátoru je načten. Pro asynchronní metody jsou pozorovány všechny výjimky vyzdvižené v asynchronní metodě, když je očekávaná vrácená úloha.

Následující příklad definuje `OddSequence` metodu, která vytvoří vyjmenovává lichá čísla mezi zadaným rozsahem. Protože předá číslo větší než 100 do metody `OddSequence` čítače <xref:System.ArgumentOutOfRangeException>výčtu, metoda vyvolá . Jak ukazuje výstup z příkladu, výjimka se zobrazí pouze při iterát čísla a ne při načtení čítače výčtu.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Místo toho můžete vyvolat výjimku při provádění ověření a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci. Obvykle výjimky vyzývané v asynchronní metodě <xref:System.AggregateException>vyžadují, abyste prozkoumali vnitřní výjimky . Místní funkce umožňují váš kód selhat rychle a umožňují výjimku, které mají být vyvolány a sledovány synchronně.

Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavit po zadaný počet sekund a vrátit hodnotu, která je náhodný násobek tohoto počtu sekund. Maximální zpoždění je 5 sekund; výsledky, <xref:System.ArgumentOutOfRangeException> pokud je hodnota větší než 5. Jak ukazuje následující příklad, výjimka, která je vyvolána při `GetMultipleAsync` předání hodnoty 6 <xref:System.AggregateException> metodě, je zabalena v po `GetMultipleAsync` zahájení spuštění metody.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Stejně jako jsme to udělali s metodou iterátoru, můžeme refaktorovat kód z tohoto příkladu provést ověření před voláním asynchronní metody. Jak ukazuje výstup z následujícího <xref:System.ArgumentOutOfRangeException> příkladu, není <xref:System.AggregateException>zabalen v .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a>Viz také

- [Metody](methods.md)
