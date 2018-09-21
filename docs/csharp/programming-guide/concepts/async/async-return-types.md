---
title: Asynchronní návratové typy (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 3d3c7d610dd1287d2c7284a5edd9c92810a74dba
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532724"
---
# <a name="async-return-types-c"></a>Asynchronní návratové typy (C#)
Asynchronní metody může mít tyto návratové typy:

- <xref:System.Threading.Tasks.Task%601>, pro asynchronní metodu, která vrací hodnotu. 
 
-  <xref:System.Threading.Tasks.Task>, pro asynchronní metodu, která provádí operaci, ale nevrací žádnou hodnotu.

- `void`, pro obslužnou rutinu události. 

- Od verze C# 7.0, libovolný typ, který má k dispozici přístup `GetAwaiter` metody. Objekt vrácený rutinou `GetAwaiter` musí implementovat metodu <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> rozhraní.
  
Další informace o metodách async naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
Každý návratový typ je zkontrolován v jedné z následujících částí a najdete úplný příklad, který používá všechny tři typy na konci tohoto tématu.  
  
##  <a name="BKMK_TaskTReturnType"></a> Úloha\<TResult\> návratový typ  
<xref:System.Threading.Tasks.Task%601> Typ vrácení se používá pro asynchronní metodu, která obsahuje [vrátit](../../../../csharp/language-reference/keywords/return.md) – příkaz (C#), ve kterém je operand má typ `TResult`.  
  
V následujícím příkladu `GetLeisureHours` asynchronní metoda obsahuje `return` příkaz, který vrátí celé číslo. Proto deklarace metody musíte zadat návratový typ `Task<int>`.  <xref:System.Threading.Tasks.Task.FromResult%2A> Asynchronní metody je zástupný symbol pro operace, která vrátí hodnotu typu string.
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

Při `GetLeisureHours` je volat z výrazu await v `ShowTodaysInfo` metodu, výraz await získá celočíselnou hodnota (hodnotu `leisureHours`), který je uložen v úloze vrácené `GetLeisureHours` metoda. Další informace o výrazech await naleznete [await](../../../../csharp/language-reference/keywords/await.md).  
  
Můžete lépe pochopit, jak to probíhá oddělením volání `GetLeisureHours` od aplikace `await`, jak ukazuje následující kód. Volání metody `GetLeisureHours` , které není okamžitě očekáváno, vrátí `Task<int>`, dle očekávání od deklarace metody. Úkol je přidělen `infoTask` proměnné v příkladu. Protože `infoTask` je <xref:System.Threading.Tasks.Task%601>, obsahuje <xref:System.Threading.Tasks.Task%601.Result> vlastnost typu `TResult`. V takovém případě `TResult` představuje typ integer. Když `await` platí pro `infoTask`, výraz await se vyhodnocuje na obsah <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost `infoTask`. Je hodnota přiřazená `ret` proměnné.  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Vlastností je vlastnost blokování. Pokud se pokusíte o přístup k ní před dokončením její úlohy, blokovaný vláknem, které je právě aktivní až do dokončení úlohy a hodnota je k dispozici. Ve většině případů byste měli přistupovat k hodnotě pomocí `await` namísto přímého přístupu. <br/> Načíst hodnotu z předchozího příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost blokování hlavního vlákna tak, aby `ShowTodaysInfo` metoda může předtím, než skončila aplikace dokončí provádění.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
##  <a name="BKMK_TaskReturnType"></a> Návratový typ úlohy  
Asynchronní metody, které neobsahují slovo `return` obsahovat prohlášení nebo které `return` příkaz, který nevrací operand obvykle mají návratový typ <xref:System.Threading.Tasks.Task>. Tyto metody vrací `void` Pokud spusťte synchronně. Pokud používáte <xref:System.Threading.Tasks.Task> návratový typ pro asynchronní metodu, volající metoda můžete použít `await` operátor k pozastavení dokončení volajícího až do dokončení volané asynchronní metody.  
  
V následujícím příkladu `WaitAndApologize` neobsahuje asynchronní metody `return` příkaz, metoda vrátí <xref:System.Threading.Tasks.Task> objektu. Díky tomu `WaitAndApologize` do ní použít operátor await. Všimněte si, že <xref:System.Threading.Tasks.Task> neobsahuje `Result` vlastnost protože nemá žádnou návratovou hodnotu.  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` je očekáván pomocí příkazu await namísto výrazu await, podobného volání příkazu pro synchronní metody vracející hodnotu void. Použití operátoru await v tomto případě nevytvoří hodnotu.  
  
Stejně jako v předchozím <xref:System.Threading.Tasks.Task%601> příkladu můžete oddělit volání `WaitAndApologize` od použití operátoru await, jako je následující kód ukazuje. Nezapomeňte však, že `Task` nemá `Result` vlastnost a že se při použití operátoru await nevytvoří žádná hodnota `Task`.  
  
Následující kód oddělí volání `WaitAndApologize` metoda z čekajícího na úkol, který metoda vrátí.  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
##  <a name="BKMK_VoidReturnType"></a> Návratový typ void

Můžete použít `void` návratový typ v asynchronní obslužné rutiny, které vyžadují `void` návratového typu. U jiných metod než obslužné rutiny událostí, které nevracejí hodnotu, měli byste vrátit <xref:System.Threading.Tasks.Task> místo, protože asynchronní metoda, která vrací `void` nemůže být očekávána. Jakýkoli volající této metody musí být schopen pokračovat v dokončení bez čekání na dokončení volané asynchronní metody a volající musí být nezávislé na všech hodnotách nebo výjimkách, které generuje asynchronní metoda.  
  
Volající asynchronní metody vracející typ void nemůže zachytit výjimky, které jsou vyvolány z metody a takové neošetřené výjimky mohou způsobit selhání aplikace. Pokud dojde k výjimce v asynchronní metodě, která vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, výjimky jsou uložena v rámci vrácené úlohy a je znovu vyvolána při očekávání úkolu. Proto se ujistěte, že asynchronní metody, které mohou způsobit výjimku má návratový typ <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> a že volání metody jsou očekávaná.  
  
Další informace o tom, jak zachytávat výjimky v asynchronních metodách, naleznete v tématu [výjimky v asynchronních metodách](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) část [bloku try-catch](../../../language-reference/keywords/try-catch.md) tématu.  
  
Následující příklad ukazuje chování asynchronní obslužnou rutinu události. Všimněte si, že v příkladu kódu nutné nechat asynchronní obslužnou rutinu události vědět po dokončení hlavního vlákna. Hlavní vlákno může pak čekat asynchronní obslužnou rutinu události pro dokončení před ukončením programu.
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>Zobecněný asynchronní návratové typy a ValueTask\<TResult\>

Od verze C# 7.0, asynchronní metoda může vrátit libovolný typ, který má k dispozici přístup `GetAwaiter` metody.
 
Protože <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> jsou typy odkazů, přidělení paměti v kritickém pro výkon cesty, zejména pokud dojde k přidělení v těsné smyčky může nepříznivě ovlivnit výkon. Podpora zobecněný návratové typy znamená, že se můžete vrátit zjednodušené hodnotový typ místo typu odkazu, aby se zabránilo další paměť přidělení. 

Poskytuje rozhraní .NET <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> strukturu jako implementace odlehčené zobecněný hodnoty vracející úlohy. Použít <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> typu, je nutné přidat `System.Threading.Tasks.Extensions` do svého projektu balíček NuGet. V následujícím příkladu <xref:System.Threading.Tasks.ValueTask%601> struktury k načtení hodnoty dvou dice postupně. 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.FromResult%2A>   
- [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
- [Tok řízení v asynchronních programech (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
- [async](../../../../csharp/language-reference/keywords/async.md)   
- [await](../../../../csharp/language-reference/keywords/await.md)
