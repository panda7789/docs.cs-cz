---
title: Asynchronní návratové typyC#()
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: f40592038ce16173e6dced5e8bcb914cfeb1b1f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922042"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typyC#()
Asynchronní metody mohou mít následující návratové typy:

- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metodu, která vrací hodnotu. 
 
- <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale nevrací žádnou hodnotu.

- `void`, pro obslužnou rutinu události. 

- Počínaje C# 7,0, jakýkoli typ, který má přístupnou `GetAwaiter` metodu. Objekt vrácený `GetAwaiter` metodou musí <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> implementovat rozhraní.
  
Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s modifikátoremC#Async a await ()](./index.md).  
  
Každý návratový typ je zkontrolován v jednom z následujících sekcí a můžete najít úplný příklad, který používá všechny tři typy na konci tématu.  
  
## <a name="BKMK_TaskTReturnType"></a>Návratový\<typ\> Task TResult  
Návratový typ se používá pro asynchronní metodu, která obsahuje příkaz [return](../../../language-reference/keywords/return.md) C#(), ve kterém je operand typu `TResult`. <xref:System.Threading.Tasks.Task%601>  
  
V následujícím příkladu `GetLeisureHours` asynchronní metoda `return` obsahuje příkaz, který vrací celé číslo. Proto deklarace metody musí specifikovat návratový typ `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Asynchronní metoda je zástupný symbol pro operaci, která vrací řetězec.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Když `GetLeisureHours` je volána z výrazu await `ShowTodaysInfo` v metodě, výraz await načte celočíselnou `leisureHours`hodnotu (hodnotu), která `GetLeisureHours` je uložena v úkolu vráceném metodou. Další informace o výrazech await naleznete v tématu [await](../../../language-reference/keywords/await.md).  
  
Můžete lépe porozumět tomu `GetLeisureHours` `await`, jak se to stane, oddělením volání z aplikace, jak ukazuje následující kód. Volání metody `GetLeisureHours` , která není okamžitě očekávána `Task<int>`, vrátí, jak byste očekávali od deklarace metody. Úkol je přiřazen k `integerTask` proměnné v příkladu. Protože `integerTask` je,obsahuje<xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`. <xref:System.Threading.Tasks.Task%601> V tomto případě `TResult` představuje typ Integer. Při `await` použití na `integerTask`je výraz await vyhodnocen jako `integerTask`obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti. Hodnota je přiřazena `ret` proměnné.  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastnost je vlastnost blokování. Pokud se pokusíte o přístup k tomuto úkolu před jeho dokončením, bude vlákno, které je aktuálně aktivní, blokováno, dokud se úloha nedokončí a hodnota nebude k dispozici. Ve většině případů byste měli k hodnotě přistupovat pomocí `await` místo přímého přístupu k vlastnosti. <br/> Předchozí příklad získal hodnotu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti pro blokování hlavního vlákna `ShowTodaysInfo` , aby metoda mohla dokončit provádění před ukončením aplikace.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a>Návratový typ úlohy  
Asynchronní metody, které neobsahují `return` příkaz nebo `return` obsahují příkaz, který nevrací operand, obvykle <xref:System.Threading.Tasks.Task>mají návratový typ. Tyto metody vrátí `void` , pokud jsou spouštěny synchronně. Použijete- <xref:System.Threading.Tasks.Task> li návratový typ pro asynchronní metodu, volající metoda může `await` použít operátor pro pozastavení dokončování volajícího až do dokončení volané asynchronní metody.  
  
V následujícím příkladu `WaitAndApologize` asynchronní metoda `return` neobsahuje příkaz, <xref:System.Threading.Tasks.Task> takže metoda vrátí objekt. To umožňuje `WaitAndApologize` očekávat. Všimněte si, <xref:System.Threading.Tasks.Task> že typ neobsahuje `Result` vlastnost, protože nemá žádnou návratovou hodnotu.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize`je očekáván pomocí příkazu await namísto výrazu await, podobně jako volání příkazu pro synchronní metodu vracející typ void. Použití operátoru await v tomto případě nevytvoří hodnotu.  
  
Stejně jako v předchozím <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit `WaitAndApologize` volání z aplikace operátoru await, jak ukazuje následující kód. Mějte ale na paměti, `Task` že `Result` vlastnost neobsahuje vlastnost a že při použití operátoru await na objekt `Task`není vyprodukována žádná hodnota.  
  
Následující kód odděluje volání `WaitAndApologize` metody z čekání na úlohu, kterou metoda vrátí.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
## <a name="BKMK_VoidReturnType"></a>Návratový typ void

Použijete `void` návratový typ v obslužných rutinách asynchronní události, které `void` vyžadují návratový typ. Pro jiné metody než obslužné rutiny událostí, které nevracejí hodnotu, byste měli <xref:System.Threading.Tasks.Task> místo toho vracet výjimku, protože asynchronní metoda `void` , která vrací, nemůže být očekávána. Každý volající takové metody musí být schopný pokračovat v dokončování bez čekání na dokončení volané asynchronní metody a volající musí být nezávislý na všech hodnotách nebo výjimkách, které asynchronní metoda generuje.  
  
Volající asynchronní metody vracející hodnotu void nemůže zachytit výjimky, které jsou vyvolány z metody, a tyto neošetřené výjimky pravděpodobně způsobí selhání aplikace. Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimka je uložena v vrácené úloze a znovu vyvolána, když je úloha očekávána. Proto se ujistěte, že jakákoliv asynchronní metoda, která může vyvolat výjimku, má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávána.  
  
Další informace o tom, jak zachytit výjimky v asynchronních metodách, naleznete v části [výjimky v asynchronních metodách](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) v tématu [try-catch](../../../language-reference/keywords/try-catch.md) .  
  
Následující příklad ukazuje chování obslužné rutiny asynchronní události. Všimněte si, že v příkladu kódu musí obslužná rutina asynchronní události při dokončení dát hlavní vlákno vědět. Pak hlavní vlákno může počkat na dokončení asynchronní obslužné rutiny události před ukončením programu.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Generalizované asynchronní návratové typy a\<ValueTask TResult\>

Počínaje C# 7,0 může asynchronní metoda vracet libovolný typ, který má přístupnou `GetAwaiter` metodu.
 
Vzhledem <xref:System.Threading.Tasks.Task> k <xref:System.Threading.Tasks.Task%601> tomu, že a jsou typy odkazů, přidělování paměti v cestách kritických pro výkon, zejména v případě, že přidělení dochází v těsných smyčkách, může negativně ovlivnit výkon. Podpora zobecněných návratových typů znamená, že můžete místo typu odkazu vrátit typ s odlehčenou hodnotou, abyste zabránili dalšímu přidělení paměti. 

Rozhraní .NET poskytuje <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturu jako zjednodušenou implementaci generalizované hodnoty vracející úlohy. Chcete-li <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> použít typ, je nutné `System.Threading.Tasks.Extensions` přidat balíček NuGet do projektu. V následujícím příkladu se pomocí <xref:System.Threading.Tasks.ValueTask%601> struktury načte hodnota dvou indexů. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Řízení toku v asynchronních programechC#()](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/keywords/await.md)
