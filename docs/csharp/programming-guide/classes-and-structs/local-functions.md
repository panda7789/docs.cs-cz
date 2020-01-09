---
title: Místní funkce – C# Průvodce programováním
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 2036e576a44aa3e1e7829e2091e5a9243d6b6010
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705519"
---
# <a name="local-functions-c-programming-guide"></a>Místní funkce (C# Průvodce programováním)

Počínaje C# 7,0 C# podporuje *místní funkce*. Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu. Mohou být volány pouze ze svých nadřazených členů. Místní funkce mohou být deklarovány v a volány z:

- Metody, zejména iterátorové metody a asynchronní metody
- Konstruktory
- Přistupující objekty vlastnosti
- Přístupové objekty událostí
- Anonymní metody
- Výrazy lambda
- Finalizační metody
- Jiné místní funkce

Místní funkce však nelze deklarovat uvnitř člena Expression-těle.

> [!NOTE]
> V některých případech můžete použít výraz lambda pro implementaci funkcí, které podporuje také místní funkce. Porovnání naleznete v tématu [místní funkce v porovnání s lambda výrazy](../../local-functions-vs-lambdas.md).

Místní funkce usnadňují záměr vašeho kódu. Každý, kdo čte váš kód, uvidí, že metoda není možné volat s výjimkou obsahující metody. U týmových projektů také znemožňuje, aby jiný vývojář omylem volal metodu přímo z jiného místa ve třídě nebo struktuře.
 
## <a name="local-function-syntax"></a>Syntaxe lokální funkce

Lokální funkce je definována jako vnořená metoda uvnitř nadřazeného člena. Jeho definice má následující syntaxi:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Místní funkce můžou používat modifikátory [Async](../../language-reference/keywords/async.md) a [unsafe](../../language-reference/keywords/unsafe.md) . 

Všimněte si, že všechny místní proměnné, které jsou definovány v nadřazeném členu, včetně jeho parametrů metody, jsou přístupné v místní funkci. 

Na rozdíl od definice metody nemůže definice lokální funkce zahrnovat modifikátor přístupu ke členu. Vzhledem k tomu, že jsou všechny místní funkce soukromé, včetně modifikátoru přístupu, jako je například klíčové slovo `private`, vygeneruje chybu kompilátoru CS0106, modifikátor Private není pro tuto položku platný.

> [!NOTE]
> Před C# 8,0 nemohou místní funkce obsahovat modifikátor `static`. Zahrnutí klíčového slova `static` generuje chybu kompilátoru CS0106, modifikátor "static" není pro tuto položku platný. "

Kromě toho nelze atributy použít pro místní funkci nebo její parametry a parametry typu. 
 
Následující příklad definuje místní funkci s názvem `AppendPathSeparator`, která je soukromá pro metodu s názvem `GetText`:
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Místní funkce a výjimky

Jednou z užitečných funkcí lokálních funkcí je to, že může dojít k okamžitému povrchování výjimek. U iterátorů metod jsou výjimky vyhodnoceny pouze v případě, že je vyhodnocena vrácená sekvence, a ne při načtení iterátoru. Pro asynchronní metody jsou při očekávaných úlohách pozorovány jakékoli výjimky vyvolané v asynchronní metodě. 

Následující příklad definuje metodu `OddSequence`, která vytváří výčet lichých čísel mezi zadaným rozsahem. Vzhledem k tomu, že předává číslo větší než 100 metodě čítače `OddSequence`, vyvolá metoda <xref:System.ArgumentOutOfRangeException>. Jak výstup z příkladu ukazuje, plochy výjimky pouze při iteraci čísel, a ne při načtení čítače výčtu.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Místo toho můžete vyvolat výjimku při provádění ověřování a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci. Výjimky vyvolané v asynchronní metodě obvykle vyžadují, abyste prozkoumali vnitřní výjimky <xref:System.AggregateException>. Místní funkce umožňují vašemu kódu selhání rychle a umožňují, aby vaše výjimka byla vyvolána a byla sledována synchronně.

Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` k pozastavení po zadaný počet sekund a vrátí hodnotu, která je náhodnou násobek tohoto počtu sekund. Maximální zpoždění je 5 sekund; <xref:System.ArgumentOutOfRangeException> výsledků, pokud je hodnota větší než 5. Jak ukazuje následující příklad, výjimka, která je vyvolána, když je předána hodnota 6 do metody `GetMultipleAsync` je zabalena do <xref:System.AggregateException> poté, co metoda `GetMultipleAsync` zahájí provádění.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Stejně jako u metody iterátoru můžeme kód z tohoto příkladu Refaktorovat, aby bylo ověřování provedeno před voláním asynchronní metody. Jak ukazuje výstup z následujícího příkladu, <xref:System.ArgumentOutOfRangeException> není zabalen do <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Viz také:

- [Metody](methods.md)
