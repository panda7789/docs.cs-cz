---
title: Asynchronní návratové typy (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 73a6e1924652c8635377547e2faddc864ac5540a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389136"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typy (C#)

Asynchronní metody mohou mít následující návratové typy:

- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metodu, která vrací hodnotu.
- <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale vrací žádnou hodnotu.
- `void`, pro obslužnou rutinu události.
- Počínaje C# 7.0, libovolný typ, `GetAwaiter` který má přístupnou metodu. Objekt vrácený `GetAwaiter` metodou musí <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> implementovat rozhraní.
- Počínaje C# 8.0 <xref:System.Collections.Generic.IAsyncEnumerable%601>, pro asynchronní metodu, která vrací *asynchronní datový proud*.

Další informace o asynchronních metodách naleznete [v tématu Asynchronní programování s asynchronní a await (C#)](./index.md).  
  
## <a name="tasktresult-return-type"></a>Návratový\> typ tresult úkolu\<  
Návratový <xref:System.Threading.Tasks.Task%601> typ se používá pro asynchronní metodu, která obsahuje příkaz `TResult` [return](../../../language-reference/keywords/return.md) (C#), ve kterém je operand .  
  
V následujícím příkladu `GetLeisureHours` asynchronní `return` metoda obsahuje příkaz, který vrací celé číslo. Proto deklarace metody musí určit `Task<int>`návratový typ .  Asynchronní <xref:System.Threading.Tasks.Task.FromResult%2A> metoda je zástupný symbol pro operaci, která vrací řetězec.
  
:::code language="csharp" source="./snippets/async-returns1.cs" id="SnippetFirstExample":::

Když `GetLeisureHours` je volána z v `ShowTodaysInfo` rámci await výraz v metodě, await výraz `leisureHours`načte hodnotu celé číslo `GetLeisureHours` (hodnota ), která je uložena v úloze vrácené metodou. Další informace o výrazy await naleznete v [tématu await](../../../language-reference/operators/await.md).  
  
Můžete lépe pochopit, `await` jak načte `Task<T>` výsledek z oddělením volání `GetLeisureHours` `await`od aplikace , jak ukazuje následující kód. Volání metody, `GetLeisureHours` která není okamžitě očekávána `Task<int>`vrátí , jak byste očekávali od deklarace metody. Úkol je přiřazen `integerTask` proměnné v příkladu. Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost `TResult`typu . V tomto `TResult` případě představuje celý typ. Při `await` použití `integerTask`na , await výraz vyhodnotí <xref:System.Threading.Tasks.Task%601.Result%2A> obsah `integerTask`vlastnosti . Hodnota je přiřazena `ret` proměnné.  
  
> [!IMPORTANT]
> Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> je blokující vlastnost. Pokud se pokusíte získat přístup před dokončením úlohy, vlákno, které je aktuálně aktivní, je blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici. Ve většině případů byste měli přistupovat k hodnotě pomocí `await` namísto přístupu k vlastnosti přímo. <br/> V předchozím příkladu načetl <xref:System.Threading.Tasks.Task%601.Result%2A> hodnotu vlastnosti blokovat `ShowTodaysInfo` hlavní vlákno tak, aby metoda mohla dokončit provádění před ukončením aplikace.  

:::code language="csharp" source="./snippets/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>Typ vrácení úkolu  
Asynchronní metody, které `return` neobsahují příkaz `return` nebo které obsahují příkaz, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody `void` vrátit, pokud jsou spuštěny synchronně. Pokud použijete <xref:System.Threading.Tasks.Task> návratový typ pro asynchronní metodu, volající metoda může použít `await` operátor k pozastavení dokončení volajícího, dokud nebude ukončena volaná asynchronní metoda.  
  
V následujícím příkladu `WaitAndApologize` asynchronní metoda neobsahuje `return` příkaz, takže <xref:System.Threading.Tasks.Task> metoda vrátí objekt. Vrácení `Task` umožňuje `WaitAndApologize` být očekáván. Typ <xref:System.Threading.Tasks.Task> neobsahuje vlastnost, `Result` protože nemá žádnou vrácenou hodnotu.  

:::code language="csharp" source="./snippets/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize`is waited by using await statement instead of await expression, similar to the calling statement for a synchronní void-returning method. Použití operátoru await v tomto případě nevytváří hodnotu.  
  
Stejně jako <xref:System.Threading.Tasks.Task%601> v předchozím příkladu `WaitAndApologize` můžete oddělit volání od aplikace operátoru await, jak ukazuje následující kód. Mějte však `Task` na paměti, `Result` že a nemá vlastnost a že žádná hodnota `Task`je vytvořena při čekání operátor je použita na .  
  
Následující kód odděluje volání `WaitAndApologize` metody od čekání na úkol, který metoda vrátí.  

:::code language="csharp" source="./snippets/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a>Typ vrácení void

Návratový `void` typ se používá v obslužných `void` rutinách asynchronních událostí, které vyžadují návratový typ. Pro metody jiné než obslužné rutiny událostí, <xref:System.Threading.Tasks.Task> které nevracejí hodnotu, `void` byste měli vrátit místo, protože asynchronní metoda, která vrátí nelze čekat. Každý volající takové metody musí pokračovat v dokončení bez čekání na dokončení volané asynchronní metody. Volající musí být nezávislý na všech hodnotách nebo výjimkách, které generuje asynchronní metoda.  
  
Volající asynchronní metody vracející se za neplatné nemůže zachytit výjimky vyvoláné z metody a takové neošetřené výjimky pravděpodobně způsobí selhání aplikace. Pokud metoda, která <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> vrátí nebo vyvolá výjimku, výjimka je uložena v vrácené úloze. Výjimka je znovu vyvolána, když je úkol očekáván. Proto se ujistěte, že všechny asynchronní metody, <xref:System.Threading.Tasks.Task> které <xref:System.Threading.Tasks.Task%601> mohou způsobit výjimku má návratový typ nebo, že volání metody jsou očekávány.  
  
Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v části [Výjimky v asynchronních metodách](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) v článku [try-catch.](../../../language-reference/keywords/try-catch.md)  
  
Následující příklad ukazuje chování obslužné rutiny události asynchronní. V ukázkovém kódu musí obslužná rutina asynchronní události povědět hlavní vlákno, když skončí. Hlavní vlákno pak může čekat na dokončení obslužné rutiny asynchronní události před ukončením programu.

:::code language="csharp" source="./snippets/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Generalizované asynchronní návratové\<typy a ValueTask TResult\>

Počínaje C# 7.0 asynchronní metoda může vrátit libovolný `GetAwaiter` typ, který má přístupnou metodu.

Vzhledem k tomu, <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> jsou typy odkazů, přidělení paměti v cestě kritické pro výkon, zejména v případě, že přidělení dojít v těsné smyčky, může nepříznivě ovlivnit výkon. Podpora pro generalizované návratové typy znamená, že můžete vrátit zjednodušený typ hodnoty namísto typu odkazu, aby se zabránilo další přidělení paměti.

Rozhraní .NET <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> poskytuje strukturu jako zjednodušenou implementaci zobecněné hodnoty vrácení úloh. Chcete-li <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> použít typ, `System.Threading.Tasks.Extensions` musíte přidat balíček NuGet do projektu. Následující příklad používá <xref:System.Threading.Tasks.ValueTask%601> strukturu k načtení hodnoty dvou kostky válců.
  
:::code language="csharp" source="./snippets/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Asynchronní datové proudy s\<iAsyncEsnumerable T\>

Počínaje C# 8.0 asynchronní metoda může vrátit *asynchronní datový proud*, reprezentované <xref:System.Collections.Generic.IAsyncEnumerable%601>. Asynchronní datový proud poskytuje způsob, jak vytvořit výčet položek číst z datového proudu, když jsou prvky generovány v blocích s opakovanými asynchronními voláními. Následující příklad ukazuje asynchronní metodu, která generuje asynchronní datový proud:

:::code language="csharp" source="./snippets/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

Předchozí příklad čte řádky z řetězce asynchronně. Po přečtení každého řádku kód vytvoří výčet každé slovo v řetězci. Volající by výčet každé slovo `await foreach` pomocí příkazu. Metoda čeká, když potřebuje asynchronně číst další řádek ze zdrojového řetězce.

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Tok řízení v asynchronních programech (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
