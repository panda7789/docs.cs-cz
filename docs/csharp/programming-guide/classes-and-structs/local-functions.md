---
title: Lokální funkce - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e91069c25ebe6c2a22927391734e5030a908e4ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646225"
---
# <a name="local-functions-c-programming-guide"></a>Lokální funkce (C# Programming Guide)

Od verze C# 7.0, C# podporuje *lokální funkce*. Lokální funkce jsou privátní metody typu, které jsou vnořeny v jiném členu. Může být volána pouze od jejich nadřazeného člena. Lokální funkce může deklarovat v a volat z:

- Metody, hlavně iterátory a asynchronní metody
- Konstruktory
- Přistupující objekty vlastnosti
- Přístupové objekty událostí
- Anonymní metody
- Výrazy lambda
- Finalizační metody
- Jiné místní funkce

Lokální funkce však nemohou být deklarovány uvnitř na člena s výrazem v těle.

> [!NOTE]
> V některých případech slouží k implementaci funkcionality také podporuje místní funkce výraz lambda. Porovnání najdete v tématu [lokální funkce ve srovnání s Lambda výrazy](../../local-functions-vs-lambdas.md).

Lokální funkce zkontrolujte záměru kódu jasný. Každému, kdo čte kód můžete vidět, metoda se nedá volat s výjimkou obsahující metodou. Pro týmové projekty, jsou také znemožnit pro jiné vývojáře omylem volat metodu přímo z jinde v dané třídy nebo struktury.
 
## <a name="local-function-syntax"></a>Syntaxe místní funkce

Lokální funkce je definován jako metodu vnořené uvnitř nadřazeného člena. Jeho definice má následující syntaxi:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Lokální funkce můžete použít [asynchronní](../../language-reference/keywords/async.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory. 

Všimněte si, že jsou k dispozici v lokální funkce všech místních proměnných, které jsou definovány v obsahující členu, včetně jeho parametry metody. 

Na rozdíl od definice metody definice lokální funkce nesmí obsahovat následující prvky:

- Členský modifikátor přístupu. Protože jsou všechny lokální funkce privátní, včetně modifikátor přístupu, jako `private` – klíčové slovo, vygeneruje Chyba kompilátoru CS0106 "modifikátor 'private' není platný pro tuto položku."
 
- [Statické](../../language-reference/keywords/static.md) – klíčové slovo. Včetně `static` – klíčové slovo vygeneruje Chyba kompilátoru CS0106, "modifikátor 'static' není platný pro tuto položku."

Kromě toho atributy nejde použít na místní funkci nebo na jeho parametry a parametry typu. 
 
Následující příklad definuje lokální funkce s názvem `AppendPathSeparator` , který je pro metodu s názvem soukromý `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Lokální funkce a výjimky

Jedním z užitečných funkcí lokální funkce je, že umožňují výjimky k poskytování okamžitě. U metody iterátorů výjimky zobrazují se jenom v případě, že vrácená sekvence je vypočten, a ne v případě, že se načte iterátor. Pro asynchronní metody jsou dodržovány zůstanou veškeré výjimky vyvolané v asynchronní metodě při očekávání vrácené úlohy. 

Následující příklad definuje `OddSequence` metodu, která vytvoří výčet lichá čísla zadaného rozsahu. Protože předá číslo větší než 100, aby se `OddSequence` – metoda výčtu, metoda vyvolá <xref:System.ArgumentOutOfRangeException>. Jak výstup z příkladu ukazuje, vyvolá výjimku pouze v případě, že je iterace čísla, a ne už při načtení enumerátoru.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Místo toho může vyvolat výjimku při provádění ověření a před načtením iterátor tak, že vrací iterátor z místní funkce, jako následující příklad ukazuje.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Lokální funkce můžete použít podobným způsobem jako pro zpracování výjimek mimo asynchronní operace. Obvykle vyžadují výjimky vyvolané v asynchronní metodě, že zkoumají vnitřní výjimky, které <xref:System.AggregateException>. Lokální funkce umožňují váš kód k rychle vygenerovala chybu a povolit výjimky být vyvolána i zjištěnými synchronně.

Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavení pro zadaný počet sekund a vrací hodnotu, která je náhodné násobek tento počet sekund. Maximální zpoždění je 5 sekund. <xref:System.ArgumentOutOfRangeException> výsledky, pokud je hodnota větší než 5. Jak ukazuje následující příklad, je předán výjimku, která je vyvolána, když je hodnota 6 `GetMultipleAsync` metoda zabalené do <xref:System.AggregateException> po `GetMultipleAsync` metoda zahájí vykonávání.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Jako jsme to udělali s metodu iterátoru, jsme Refaktorovat kód z tohoto příkladu a provést ověření před volání asynchronní metody. Jak výstup z následující příklad ukazuje <xref:System.ArgumentOutOfRangeException> není zabalena v <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Viz také:

- [Metody](methods.md)
