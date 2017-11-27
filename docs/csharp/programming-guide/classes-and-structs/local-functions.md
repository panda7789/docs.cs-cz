---
title: "Lokální funkce (C# Průvodce programováním)"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e95d48e451038f0f7004d0901f329b2c57fe5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="local-functions-c-programming-guide"></a>Lokální funkce (C# Průvodce programováním)

Od verze jazyka C# 7, C# podporuje *lokální funkce*. Lokální funkce jsou privátní metody typu, které jsou vnořené v jiného člena. Může být volána pouze z jejich obsahující člen. Lokální funkce můžete v deklarována a volat z:

- Metody, hlavně iterator metody a asynchronní metody
- Konstruktory
- Přístupové objekty vlastnosti
- Přístupové objekty událostí
- Anonymní metody
- Lambda – výrazy
- Finalizační metody
- Další místní funkce

Lokální funkce však nelze deklarovat uvnitř výrazu vozidlo člen.

> [!NOTE]
> V některých případech můžete implementovat funkce podporovány také místní funkcí výrazu lambda. Porovnání najdete v tématu [lokální funkce ve srovnání s výrazy Lambda](../../local-functions-vs-lambdas.md).

Lokální funkce byl záměr vymazat kódu. Každý, kdo čtení kódu můžete uvidíte, že metoda není s výjimkou volatelné obsahující metoda. Pro týmové projekty, budou také znemožňují pro jiné vývojáře omylem zavolat metodu přímo z jinde v dané třídě nebo stuct.
 
## <a name="local-function-syntax"></a>Syntaxe místní – funkce

Místní funkce je definován jako vnořené metoda uvnitř obsahující člena. Její definice obsahuje následující syntaxi:

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Můžete použít místní funkce [asynchronní](../../language-reference/keywords/async.md) a [unsafe](../../language-reference/keywords/unsafe.md) modifikátory. 

Všimněte si, že všechny místní proměnné, které jsou definovány v obsahující členovi, včetně jeho parametry metody jsou dostupné v místní funkce. 

Na rozdíl od metoda definice definice místní funkce nesmí obsahovat následující prvky:

- Modifikátor přístupu členů. Protože všechny místní funkce privátní, včetně – modifikátor přístupu, jako například `private` – klíčové slovo, vygeneruje Chyba kompilátoru CS0106, "modifikátor 'privátní' není platný pro tuto položku."
 
- [Statické](../../language-reference/keywords/static.md) – klíčové slovo. Včetně `static` – klíčové slovo vygeneruje Chyba kompilátoru CS0106, "modifikátor"statická"není platný pro tuto položku."

Kromě toho atributy nelze použít k funkci místní nebo jeho parametry a parametry typu. 
 
V následujícím příkladu definuje místní funkce s názvem `AppendPathSeparator` , je pro metodu s názvem soukromý `GetText`:
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a>Místní funkce a výjimky

Jedna z funkcí užitečné místní funkcí je, že umožňují výjimky prezentovat okamžitě. Pro metodu iterátory výjimky jsou prezentované jenom v případě, že je výčet vrácený pořadí, a ne v případě, že se načítají iteraci. Pro asynchronní metody je možné vysledovat všechny výjimky vzniklé v asynchronní metody při vrácený úloh je očekáváno. 

V následujícím příkladu definuje `OddSequence` metoda, která vytvoří výčet liché číslo mezi zadaném rozsahu. Protože předává číslo větší než 100, která `OddSequence` enumerátor metoda vyvolá metoda <xref:System.ArgumentOutOfRangeException>. Jak ukazuje výstup z příkladu, výjimka zobrazí jenom v případě, že iterace čísla, a ne už při načtení enumerátoru.

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

Místo toho můžete při provádění ověřování může vyvolat výjimku a před načtením iteraci vrácením iteraci z místní funkce, jako následující příklad ukazuje.

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Místní funkcí lze podobným způsobem zpracování výjimek mimo asynchronní operaci. Normálně, výjimky vzniklé v asynchronní metody vyžadují, že byste zkontrolovat vnitřní výjimky z <xref:System.AggregateException>. Lokální funkce povolit kódu služeb při selhání rychle a povolit vaší výjimka být vyvolána i zjištěnými synchronně.

Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavení pro zadaný počet sekund, a vrátí hodnotu, která je náhodný násobkem tento počet sekund. Maximální zpoždění je 5 sekund; <xref:System.ArgumentOutOfRangeException> výsledků, pokud je hodnota větší než 5. Jak ukazuje následující příklad, výjimka, která se vyvolá, když hodnota 6 předána `GetMultipleAsync` metoda je uzavřen do <xref:System.AggregateException> po `GetMultipleAsync` metoda zahájí spuštění.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

Jako jsme to udělali s iterator metoda, jsme Refaktorovat kód z tohoto příkladu k ověření před voláním asynchronní metody. Jako výstup z následující příklad ukazuje <xref:System.ArgumentOutOfRangeException> není uzavřen do < x:System.AggregateException >.

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a>Viz také
[Metody](methods.md)
