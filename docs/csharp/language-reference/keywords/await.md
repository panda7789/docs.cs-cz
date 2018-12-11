---
title: await – C# odkaz
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c80d6598540700fdb8559497f10c66726c384519
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239680"
---
# <a name="await-c-reference"></a>await – – operátor (Referenční dokumentace jazyka C#)
`await` Operátor je použít pro úkol v asynchronní metodě vložte bodu pozastavení provádění metody až do dokončení očekávané úlohy. Úloha představuje probíhající práci.  
  
`await` jde použít jenom v asynchronní metodě změnil [asynchronní](../../../csharp/language-reference/keywords/async.md) – klíčové slovo. Tato metoda, definována pomocí `async` modifikátor a obvykle obsahuje jeden nebo více `await` výrazy, se označuje jako *asynchronní metoda*.  
  
> [!NOTE]
>  `async` a `await` klíčová slova byly zavedeny v jazyce C# 5. Úvod do asynchronního programování naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Úkol, na který `await` je použit operátor obvykle je vrácen voláním metody, která implementuje [Task-Based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Patří sem metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, a `System.Threading.Tasks.ValueType<TResult>` objekty.  

  
 V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda vrátí hodnotu `Task<byte[]>`. Úkol je příslib z k vytvoření pole bajtů po dokončení úkolu. `await` Operátor pozastaví provádění, dokud práce <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dokončení metody. Do té doby se ovládací prvek vrátí volajícímu metody `GetPageSizeAsync`. Po dokončení provádění úlohy `await` výraz vyhodnocen jako bajtové pole.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Kompletní příklad naleznete v tématu [názorný postup: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Můžete stáhnout ukázku z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu společnosti Microsoft. V příkladu je v projektu AsyncWalkthrough_HttpClient.  
  
Jak je znázorněno v předchozím příkladu, pokud `await` se použije na výsledek volání metody, která vrací `Task<TResult>`, potom je typ `await` výraz je `TResult`. Pokud `await` se použije na výsledek volání metody, která vrací `Task`, potom je typ `await` výraz je `void`. Následující příklad ukazuje rozdíl.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Výraz neblokuje vlákno, na kterém je spuštěn. Místo toho způsobí, že kompilátor zapíše zbytek asynchronní metody jako pokračování očekávané úlohy. Ovládací prvek vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a provádění asynchronní metody pokračuje tam, kde skončila.  
  
`await` Výraz může dojít pouze v těle jeho nadřazené metody, výrazu lambda nebo anonymní metodu, která musí být označeny pomocí `async` modifikátor. Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci metody, výrazu lambda nebo anonymní metodu `await` výrazu nelze provést v těle synchronní funkce, ve výrazu dotazu v bloku [lock – příkaz](../../../csharp/language-reference/keywords/lock-statement.md), nebo v [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu.  
  
## <a name="exceptions"></a>Výjimky  
Většina asynchronních metod vrátí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácené úlohy nesou informaci o jejím stavu a historii, např. Určuje, zda je úkol dokončený, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek je. `await` Operátor má přístup k těmto vlastnostem voláním metod na objekt vrácený rutinou `GetAwaiter` metody.  
  
Pokud očekáváte vracející úlohy asynchronní metodu, která způsobí výjimku, `await` operátor znovu vyvolá výjimku.  
  
Pokud očekáváte vracející úlohy asynchronní metody, která je zrušena, `await` znovu vyvolá operátor <xref:System.OperationCanceledException>.  
  
Jeden úkol, který je v chybovém stavu, může odrážet více výjimek. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Když budete očekávat takový úkol, operace await vrátí pouze jednu z výjimek. Nelze však předpovědět, které výjimky je znovu vyvolána.  
  
Příklady zpracování chyb v asynchronních metodách, naleznete v tématu [bloku try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Příklad  
Následující příklad vrátí celkový počet znaků na stránkách, jejichž adresy URL jsou předány jako argumenty příkazového řádku. Příklad volá `GetPageLengthsAsync` metodu, která je označena `async` – klíčové slovo. `GetPageLengthsAsync` Dále používá metodu `await` – klíčové slovo await pro čekání volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metody.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

V předchozím příkladu C# 7.1, která podporuje [ `async` `Main` metoda](../../programming-guide/main-and-command-args/index.md). Protože starší C# verze nepodporují vstupní body aplikace, které vracejí <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>, nelze použít `async` modifikátor `Main` metoda a operátoru await `GetPageLengthsAsync` volání metody. V takovém případě můžete zajistit, aby `Main` metoda čeká na dokončení načtením hodnoty asynchronní operace <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnost. Pro úlohy, které nesmí vracet hodnotu, můžete volat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody. Informace o tom, jak vyberte verzi jazyka najdete v tématu [vyberte C# jazykovou verzi](../configure-language-version.md).

## <a name="see-also"></a>Viz také:  
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/index.md)   
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
- [async](../../../csharp/language-reference/keywords/async.md)
