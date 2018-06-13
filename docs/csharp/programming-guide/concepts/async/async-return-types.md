---
title: Asynchronní návratové typy (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 07aefcf3149b2210e3dc97713647fa3a0133a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334181"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typy (C#)
Asynchronní metody může mít následující návratové typy:

- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metody, která vrátí hodnotu. 
 
-  <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale nevrací žádnou hodnotu.

- `void`, pro obslužnou rutinu události. 

- Od verze jazyka C# 7.0, žádný typ, který má přístupné `GetAwaiter` metoda. Objekt vrácený `GetAwaiter` metoda musí implementovat <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> rozhraní.
  
Další informace o asynchronní metody najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
V jednom z těchto částí je zkontrolován každý návratový typ a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.  
  
##  <a name="BKMK_TaskTReturnType"></a> Návratový typ Task(T)  
<xref:System.Threading.Tasks.Task%601> Vrátí typ se používá pro asynchronní metody, která obsahuje [vrátit](../../../../csharp/language-reference/keywords/return.md) (C#) příkaz, ve kterém má operand typu `TResult`.  
  
V následujícím příkladu `GetLeisureHours` obsahuje asynchronní metody `return` příkaz, který vrátí celé číslo. Proto deklarace metody musíte zadat návratový typ `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Asynchronní metody je zástupný symbol pro operace, která vrací řetězec.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Při `GetLeisureHours` je volána v rámci výrazu await v `ShowTodaysInfo` metoda, výraz await načte celočíselnou hodnotu (hodnota `leisureHours`) který je uložený v úloze vrácený `GetLeisureHours` metoda. Další informace o await výrazy najdete v tématu [await](../../../../csharp/language-reference/keywords/await.md).  
  
Můžete lépe pochopit, jak tomu oddělením volání `GetLeisureHours` z používání `await`, jak ukazuje následující kód. Volání metody `TaskOfT_MethodAsync` , není okamžitě očekávaná vrátí `Task<int>`, jak očekáváte od deklaraci metody. Úloha je přiřazená `integerTask` proměnné v příkladu. Protože `integerTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`. V takovém případě TResult představuje celočíselného typu. Když `await` se použije pro `integerTask`, await vyhodnocen jako obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `integerTask`. Hodnota je přiřazena k `result2` proměnné.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Je blokování vlastnost. Pokud se pokusíte k němu přístup před dokončení úkolu, vláken, který je aktuálně aktivní je blokován, dokud úloha dokončí, a hodnota je k dispozici. Ve většině případů byste měli hodnota přistupovat pomocí `await` místo přístupu k vlastnosti. <br/> Předchozí příklad načíst hodnotu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost blokování hlavního vlákna tak, aby `ShowTodaysInfo` metoda může dokončí provádění, než aplikace skončila.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Návratový typ úlohy  
Asynchronní metody, které neobsahují žádný `return` prohlášení nebo které obsahovat `return` příkaz, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody vrací `void` Pokud spouští synchronně. Pokud používáte <xref:System.Threading.Tasks.Task> návratový typ pro asynchronní metody, můžete použít volání metody `await` operátor volajícího dokončení pozastavit, dokud volané asynchronní metody dokončení.  
  
V následujícím příkladu `WaitAndApologize` neobsahuje asynchronní metody `return` prohlášení, vrátí metoda <xref:System.Threading.Tasks.Task> objektu. To umožňuje `WaitAndApologize` k být očekáváno. Všimněte si, že <xref:System.Threading.Tasks.Task> neobsahuje typ `Result` vlastnost protože nemá žádnou návratovou hodnotu.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` je očekáváno pomocí příkazu await místo výrazu await, podobně jako příkaz volání pro metodu synchronní vrácení void. Aplikace operátoru await v tomto případě neobsahuje hodnotu.  
  
Stejně jako v předchozí <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `Task_MethodAsync` z aplikace operátoru await, jako následující kód ukazuje. Nezapomeňte však, že `Task` nemá `Result` vlastnost a že při použití operátoru await vytváří žádná hodnota `Task`.  
  
Následující kód odděluje volání `WaitAndApologize` metoda z čeká na úlohu, která vrátí metoda.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Typ vrácené hodnoty void  
Můžete použít `void` návratový typ v obslužné rutiny asynchronní událostí, které vyžadují `void` návratovým typem. Pro jiných metod než událost obslužné rutiny nevrací hodnotu, měli byste se vrátit <xref:System.Threading.Tasks.Task> místo, protože asynchronní metody, která vrací `void` nelze očekáváno. Všechny volající tato metoda musí být schopen dál dokončení bez čekání na volané asynchronní metody dokončení a volající musí být nezávislé na všechny hodnoty nebo které generuje asynchronní metody.  
  
Volající asynchronní metody vrácení void nelze catch výjimky, které jsou vyvolány z metody a může způsobit selhání aplikace jsou takové neošetřené výjimky. Pokud dojde k výjimce v asynchronní metody, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložený v vrácený úkolů a je znovu vyvolány, když je očekáváno úlohu. Proto se ujistěte, že asynchronní metody, která může vytvořit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že jsou očekáváno volání metody.  
  
Další informace o tom, jak zachycení výjimek v asynchronní metody najdete v tématu [try-catch –](../../../../csharp/language-reference/keywords/try-catch.md) .  
  
Následující eample definuje obslužnou rutinu události asynchronní.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetaskt"></a>Zobecněný asynchronní návratové typy a ValueTask<T>

Od verze 7.0 C#, může použití asynchronní metody vrátit žádný typ, který má přístupné `GetAwaiter` metoda.
 
Protože <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> jsou odkazové typy přidělení paměti v výkon kritických cest, zejména v případě, že v úzkou smyčky, dojde k přidělení může nepříznivě ovlivnit výkon. Podpora pro zobecněný návratové typy znamená, že se můžete vrátit typu lightweight hodnoty místo typu odkazu. aby se zabránilo přidělení další paměť. 

Poskytuje rozhraní .NET <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> struktura jako šedé – implementace zobecněný úloh vrácení hodnoty. Použít <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, je nutné přidat `System.Threading.Tasks.Extensions` balíček NuGet do projektu. Následující příklad používá <xref:System.Threading.Tasks.ValueTask%601> se vrátí k načtení hodnoty dvou rozčlenění strukturu. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Viz také  
<xref:System.Threading.Tasks.Task.FromResult%2A>   
[Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[Řízení toku v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
[Asynchronní](../../../../csharp/language-reference/keywords/async.md)   
[await](../../../../csharp/language-reference/keywords/await.md)
