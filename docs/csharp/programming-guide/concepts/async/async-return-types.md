---
title: Asynchronní návratové typy (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 9926fea5308f9088ad924bcc98d8deed319c6300
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170036"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typy (C#)
Asynchronní metody mohou mít následující návratové typy:

- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metodu, která vrací hodnotu.

- <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale vrací žádnou hodnotu.

- `void`, pro obslužnou rutinu události.

- Počínaje C# 7.0, libovolný typ, `GetAwaiter` který má přístupnou metodu. Objekt vrácený `GetAwaiter` metodou musí <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> implementovat rozhraní.
  
Další informace o asynchronních metodách naleznete [v tématu Asynchronní programování s asynchronní a await (C#)](./index.md).  
  
Každý návratový typ je zkoumán v jedné z následujících částí a můžete najít úplný příklad, který používá všechny tři typy na konci tématu.  
  
## <a name="BKMK_TaskTReturnType"></a>Návratový\> typ tresult úkolu\<  
Návratový <xref:System.Threading.Tasks.Task%601> typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../language-reference/keywords/return.md) (C#), ve kterém má operand typ `TResult`.  
  
V následujícím příkladu `GetLeisureHours` asynchronní `return` metoda obsahuje příkaz, který vrací celé číslo. Proto deklarace metody musí určit `Task<int>`návratový typ .  Asynchronní <xref:System.Threading.Tasks.Task.FromResult%2A> metoda je zástupný symbol pro operaci, která vrací řetězec.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Když `GetLeisureHours` je volána z v `ShowTodaysInfo` rámci await výraz v metodě, await výraz `leisureHours`načte hodnotu celé číslo `GetLeisureHours` (hodnota ), která je uložena v úloze vrácené metodou. Další informace o výrazy await naleznete v [tématu await](../../../language-reference/operators/await.md).  
  
Můžete lépe pochopit, jak k tomu `GetLeisureHours` dochází oddělením `await`volání od aplikace , jak ukazuje následující kód. Volání metody, `GetLeisureHours` která není okamžitě očekávána `Task<int>`vrátí , jak byste očekávali od deklarace metody. Úkol je přiřazen `integerTask` proměnné v příkladu. Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost `TResult`typu . V tomto `TResult` případě představuje celý typ. Při `await` použití `integerTask`na , await výraz vyhodnotí <xref:System.Threading.Tasks.Task%601.Result%2A> obsah `integerTask`vlastnosti . Hodnota je přiřazena `ret` proměnné.  
  
> [!IMPORTANT]
> Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> je blokující vlastnost. Pokud se pokusíte získat přístup před dokončením úlohy, vlákno, které je aktuálně aktivní, je blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici. Ve většině případů byste měli přistupovat k hodnotě pomocí `await` namísto přístupu k vlastnosti přímo. <br/> V předchozím příkladu načetl <xref:System.Threading.Tasks.Task%601.Result%2A> hodnotu vlastnosti blokovat `ShowTodaysInfo` hlavní vlákno tak, aby metoda mohla dokončit provádění před ukončením aplikace.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a>Typ vrácení úkolu  
Asynchronní metody, které `return` neobsahují příkaz `return` nebo které obsahují příkaz, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody `void` vrátit, pokud jsou spuštěny synchronně. Pokud použijete <xref:System.Threading.Tasks.Task> návratový typ pro asynchronní metodu, volající metoda může použít `await` operátor k pozastavení dokončení volajícího, dokud nebude ukončena volaná asynchronní metoda.  
  
V následujícím příkladu `WaitAndApologize` asynchronní metoda neobsahuje `return` příkaz, takže <xref:System.Threading.Tasks.Task> metoda vrátí objekt. To `WaitAndApologize` umožňuje čekat. Všimněte <xref:System.Threading.Tasks.Task> si, že typ `Result` neobsahuje vlastnost, protože nemá žádnou vrácenou hodnotu.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize`is waited by using await statement instead of await expression, similar to the calling statement for a synchronní void-returning method. Použití operátoru await v tomto případě nevytváří hodnotu.  
  
Stejně jako <xref:System.Threading.Tasks.Task%601> v předchozím příkladu `WaitAndApologize` můžete oddělit volání od aplikace operátoru await, jak ukazuje následující kód. Mějte však `Task` na paměti, `Result` že a nemá vlastnost a že žádná hodnota `Task`je vytvořena při čekání operátor je použita na .  
  
Následující kód odděluje volání `WaitAndApologize` metody od čekání na úkol, který metoda vrátí.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  

## <a name="BKMK_VoidReturnType"></a>Typ vrácení void

Návratový `void` typ se používá v obslužných `void` rutinách asynchronních událostí, které vyžadují návratový typ. Pro metody jiné než obslužné rutiny událostí, <xref:System.Threading.Tasks.Task> které nevracejí hodnotu, `void` byste měli vrátit místo, protože asynchronní metoda, která vrátí nelze čekat. Každý volající takové metody musí být schopen pokračovat v dokončení bez čekání na dokončení volané asynchronní metody a volající musí být nezávislý na všech hodnotách nebo výjimkách, které generuje asynchronní metoda.  
  
Volající asynchronní metody vracející se za neplatné nemůže zachytit výjimky, které jsou vyvolány z metody, a takové neošetřené výjimky pravděpodobně způsobí selhání aplikace. Pokud dojde k výjimce v asynchronní metodě, která vrátí <xref:System.Threading.Tasks.Task> a nebo <xref:System.Threading.Tasks.Task%601>, je výjimka uložena v vrácené úloze a je znovu vyvolána při čekání na úlohu. Proto se ujistěte, že všechny asynchronní metody, <xref:System.Threading.Tasks.Task> které <xref:System.Threading.Tasks.Task%601> mohou způsobit výjimku má návratový typ nebo, že volání metody jsou očekávány.  
  
Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v části [Výjimky v asynchronních metodách](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) tématu [try-catch.](../../../language-reference/keywords/try-catch.md)  
  
Následující příklad ukazuje chování obslužné rutiny události asynchronní. Všimněte si, že v ukázkovém kódu musí obslužná rutina asynchronní události povědět hlavní vlákno, když skončí. Hlavní vlákno pak může čekat na dokončení obslužné rutiny asynchronní události před ukončením programu.

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Generalizované asynchronní návratové\<typy a ValueTask TResult\>

Počínaje C# 7.0 asynchronní metoda může vrátit libovolný `GetAwaiter` typ, který má přístupnou metodu.

Vzhledem k tomu, <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> jsou typy odkazů, přidělení paměti v cestě kritické pro výkon, zejména v případě, že přidělení dojít v těsné smyčky, může nepříznivě ovlivnit výkon. Podpora pro generalizované návratové typy znamená, že můžete vrátit zjednodušený typ hodnoty namísto typu odkazu, aby se zabránilo další přidělení paměti.

Rozhraní .NET <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> poskytuje strukturu jako zjednodušenou implementaci zobecněné hodnoty vrácení úloh. Chcete-li <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> použít typ, `System.Threading.Tasks.Extensions` musíte přidat balíček NuGet do projektu. Následující příklad používá <xref:System.Threading.Tasks.ValueTask%601> strukturu k načtení hodnoty dvou kostky válců.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Tok řízení v asynchronních programech (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
