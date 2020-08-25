---
title: Asynchronní návratové typy (C#)
description: Přečtěte si o návratových typech, které asynchronní metody mohou mít v jazyce C# s příklady kódu pro každý typ a další prostředky.
ms.date: 08/19/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 71e560ed8ee0cae14da396e5ea2f3ab29611ebab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811493"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typy (C#)

Asynchronní metody mohou mít následující návratové typy:

- <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale nevrací žádnou hodnotu.
- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metodu, která vrací hodnotu.
- `void`, pro obslužnou rutinu události.
- Počínaje jazykem C# 7,0, jakýkoli typ, který má přístupnou `GetAwaiter` metodu. Objekt vrácený `GetAwaiter` metodou musí implementovat <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> rozhraní.
- Počínaje jazykem C# 8,0, <xref:System.Collections.Generic.IAsyncEnumerable%601> pro asynchronní metodu, která vrací *asynchronní datový proud*.

Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await (C#)](./index.md).

Existuje také několik dalších typů, které jsou specifické pro úlohy Windows:

- <xref:System.Windows.Threading.DispatcherOperation>, pro asynchronní operace omezené na Windows.
- <xref:Windows.Foundation.IAsyncAction>, pro asynchronní akce v UWP, které nevracejí hodnotu.
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>, pro asynchronní akce v UWP, které hlásí průběh, ale nevrací hodnotu.
- <xref:Windows.Foundation.IAsyncOperation%601>pro asynchronní operace v UWP, které vracejí hodnotu.
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>, pro asynchronní operace v UWP, které nastavují průběh a vracejí hodnotu.

## <a name="task-return-type"></a>Návratový typ úlohy

Asynchronní metody, které neobsahují `return` příkaz nebo obsahují `return` příkaz, který nevrací operand, obvykle mají návratový typ <xref:System.Threading.Tasks.Task> . Tyto metody vrátí, `void` Pokud jsou spouštěny synchronně. Použijete-li <xref:System.Threading.Tasks.Task> návratový typ pro asynchronní metodu, volající metoda může použít `await` operátor pro pozastavení dokončování volajícího až do dokončení volané asynchronní metody.

V následujícím příkladu `WaitAndApologizeAsync` Metoda neobsahuje `return` příkaz, takže metoda vrátí <xref:System.Threading.Tasks.Task> objekt. Vrácení, `Task` `WaitAndApologizeAsync` které umožňuje očekávat. <xref:System.Threading.Tasks.Task>Typ nezahrnuje vlastnost, `Result` protože nemá žádnou návratovou hodnotu.

:::code language="csharp" source="snippets/async-return-types/async-returns2.cs" id="TaskReturn":::

`WaitAndApologizeAsync` je očekáván pomocí příkazu await namísto výrazu await, podobně jako volání příkazu pro synchronní metodu vracející typ void. Použití operátoru await v tomto případě nevytvoří hodnotu. Pro objasnění příkazu terms a Expression použijte následující tabulku:

| Typ čekání | Příklad                                      | Typ                                   |
|------------|----------------------------------------------|----------------------------------------|
| Příkaz  | `await SomeTaskMethodAsync()`                | <xref:System.Threading.Tasks.Task>     |
| Výraz | `T result = await SomeTaskMethodAsync<T>();` | <xref:System.Threading.Tasks.Task%601> |

Volání můžete oddělit `WaitAndApologizeAsync` od aplikace operátoru await, jak ukazuje následující kód. Mějte ale na paměti, že `Task` vlastnost neobsahuje `Result` vlastnost a že při použití operátoru await na objekt není vyprodukována žádná hodnota `Task` .

Následující kód odděluje volání `WaitAndApologizeAsync` metody z čekání na úlohu, kterou metoda vrátí.

:::code language="csharp" source="snippets/async-return-types/async-returns2a.cs" id="AwaitTask":::

## <a name="tasktresult-return-type"></a>\<TResult\>Návratový typ úlohy

<xref:System.Threading.Tasks.Task%601>Návratový typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../language-reference/keywords/return.md) , ve kterém je operand `TResult` .

V následujícím příkladu `GetLeisureHoursAsync` Metoda obsahuje `return` příkaz, který vrací celé číslo. Proto deklarace metody musí specifikovat návratový typ `Task<int>` . <xref:System.Threading.Tasks.Task.FromResult%2A>Asynchronní metoda je zástupný symbol pro operaci, která vrací <xref:System.DateTime.DayOfWeek> .

:::code language="csharp" source="snippets/async-return-types/async-returns1.cs" id="LeisureHours":::

Když `GetLeisureHoursAsync` je volána z výrazu await v `ShowTodaysInfo` metodě, výraz await načte celočíselnou hodnotu (hodnotu `leisureHours` ), která je uložena v úkolu vráceném `GetLeisureHours` metodou. Další informace o výrazech await naleznete v tématu [await](../../../language-reference/operators/await.md).

Můžete lépe pochopit, jak `await` načte výsledek z rozhraní `Task<T>` oddělením volání `GetLeisureHoursAsync` z aplikace `await` , jak ukazuje následující kód. Volání metody `GetLeisureHoursAsync` , která není okamžitě očekávána `Task<int>` , vrátí, jak byste očekávali od deklarace metody. Úkol je přiřazen k `getLeisureHoursTask` proměnné v příkladu. Protože `getLeisureHoursTask` je <xref:System.Threading.Tasks.Task%601> , obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult` . V tomto případě `TResult` představuje typ Integer. Při `await` použití na je `getLeisureHoursTask` Výraz Await vyhodnocen jako obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti `getLeisureHoursTask` . Hodnota je přiřazena `ret` proměnné.

> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A>Vlastnost je vlastnost blokování. Pokud se pokusíte o přístup k tomuto úkolu před jeho dokončením, bude vlákno, které je aktuálně aktivní, blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici. Ve většině případů byste měli k hodnotě přistupovat pomocí místo přímého `await` přístupu k vlastnosti.
>
> Předchozí příklad obnovil hodnotu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti pro blokování hlavního vlákna tak, aby `Main` Metoda mohla vytisknout `message` do konzoly před ukončením aplikace.

:::code language="csharp" source="snippets/async-return-types/async-returns1a.cs" id="StoreTask":::

## <a name="void-return-type"></a>Návratový typ void

Použijete `void` návratový typ v obslužných rutinách asynchronní události, které vyžadují `void` návratový typ. Pro jiné metody než obslužné rutiny událostí, které nevracejí hodnotu, byste měli <xref:System.Threading.Tasks.Task> místo toho vracet výjimku, protože asynchronní metoda, která vrací, `void` nemůže být očekávána. Jakýkoli volající takové metody musí pokračovat v dokončování bez čekání na dokončení volané asynchronní metody. Volající musí být nezávislý na všech hodnotách nebo výjimkách vygenerovaných asynchronní metodou.

Volající asynchronní metody vracející hodnotu void nemůže zachytit výjimky vyvolané z metody a tyto neošetřené výjimky pravděpodobně způsobí selhání aplikace. Pokud metoda, která vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> vyvolá výjimku, je tato výjimka uložena v vráceném úkolu. Výjimka je znovu vyvolána, když je úloha očekávána. Proto se ujistěte, že jakákoliv asynchronní metoda, která může vyvolat výjimku, má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávána.

Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v části [výjimky v asynchronních metodách](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) v článku [try-catch](../../../language-reference/keywords/try-catch.md) .

Následující příklad ukazuje chování obslužné rutiny asynchronní události. V ukázkovém kódu musí obslužná rutina asynchronní události dát hlavnímu vláknu po jeho dokončení informace. Pak hlavní vlákno může počkat na dokončení asynchronní obslužné rutiny události před ukončením programu.

:::code language="csharp" source="snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Generalizované asynchronní návratové typy a ValueTask\<TResult\>

Počínaje jazykem C# 7,0 může asynchronní metoda vracet libovolný typ, který má přístupnou `GetAwaiter` metodu.

Vzhledem <xref:System.Threading.Tasks.Task> k tomu, že a <xref:System.Threading.Tasks.Task%601> jsou typy odkazů, přidělování paměti v cestách kritických pro výkon, zejména v případě, že přidělení dochází v těsných smyčkách, může negativně ovlivnit výkon. Podpora zobecněných návratových typů znamená, že můžete místo typu odkazu vrátit typ s odlehčenou hodnotou, abyste zabránili dalšímu přidělení paměti.

Rozhraní .NET poskytuje <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturu jako zjednodušenou implementaci generalizované hodnoty vracející úlohy. Chcete-li použít <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typ, je nutné přidat `System.Threading.Tasks.Extensions` balíček NuGet do projektu. V následujícím příkladu se pomocí <xref:System.Threading.Tasks.ValueTask%601> struktury načte hodnota dvou indexů.

:::code language="csharp" source="snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Asynchronní streamování pomocí IAsyncEnumerable\<T\>

Počínaje jazykem C# 8,0 může asynchronní metoda vracet *asynchronní datový proud*reprezentovaný <xref:System.Collections.Generic.IAsyncEnumerable%601> . Asynchronní datový proud poskytuje způsob, jak vytvořit výčet položek čtených z datového proudu, když jsou prvky generovány v blocích s opakovanými asynchronními voláními. Následující příklad ukazuje asynchronní metodu, která generuje asynchronní datový proud:

:::code language="csharp" source="snippets/async-return-types/AsyncStreams.cs" id="GenerateAsyncStream":::

Předchozí příklad čte řádky z řetězce asynchronně. Po načtení každého řádku kód vytvoří výčet každého slova v řetězci. Volající by mohli vytvořit výčet každého slova pomocí `await foreach` příkazu. Metoda čeká v případě, kdy potřebuje asynchronní čtení dalšího řádku ze zdrojového řetězce.

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Zpracování asynchronních úloh po dokončení](start-multiple-async-tasks-and-process-them-as-they-complete.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
