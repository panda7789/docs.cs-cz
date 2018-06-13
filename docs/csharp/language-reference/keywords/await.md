---
title: await – – operátor (Referenční dokumentace jazyka C#)
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: e32c7007ca98ce2153386665b60c45ff9e90cc3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218917"
---
# <a name="await-c-reference"></a>await – – operátor (Referenční dokumentace jazyka C#)
`await` Operátor se použije pro úlohu v asynchronní metodu vložit bod pozastavení při provádění metody až do dokončení awaited úloh. Úloha reprezentuje probíhající práce.  
  
`await` lze použít pouze v upraveném asynchronní metodu [asynchronní](../../../csharp/language-reference/keywords/async.md) – klíčové slovo. Tato metoda, definované pomocí `async` modifikátor a obvykle obsahují jeden nebo více `await` výrazy, se označuje jako *asynchronní metody*.  
  
> [!NOTE]
>  `async` a `await` klíčová slova byly zavedeny v C# 5. Úvod do asynchronního programování, najdete v části [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).  
  
Úlohy, ke kterému `await` operátor platí obvykle se vrátí po volání metody, která implementuje [Task-Based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Patří mezi ně metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, a `System.Threading.Tasks.ValueType<TResult>` objekty.  

  
 V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda vrátí `Task<byte[]>`. Tato úloha je promise k vytvoření skutečné bajtové pole po dokončení úlohy. `await` Operátor pozastaví spuštění, dokud práci <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metoda je dokončena. Do té doby ovládací prvek se vrátí do volajícího `GetPageSizeAsync`. Po dokončení provádění této úlohy `await` výraz vyhodnocen jako bajtové pole.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  Úplný příklad najdete v tématu [návod: přístup k webu pomocí modifikátoru Async a Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Si můžete stáhnout ukázkový z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu společnosti Microsoft. Příkladem je v AsyncWalkthrough_HttpClient projektu.  
  
Jak ukazuje předchozí příklad, pokud `await` se použije na výsledek volání metody, která vrátí `Task<TResult>`, pak typ `await` výraz `TResult`. Pokud `await` se použije na výsledek volání metody, která vrátí `Task`, pak typ `await` výraz `void`. Následující příklad ukazuje rozdíl.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Výraz neblokuje vláken, na kterém je prováděna. Místo toho ji způsobí, že kompilátor zaregistrujte se jako pokračování na úlohu awaited zbytek asynchronní metody. Ovládací prvek pak vrátí volajícímu asynchronní metody. Po dokončení úlohy vyvolá jeho pokračování a spouštění obnoví asynchronní metody, kde bylo přerušeno.  
  
`await` Výrazu může dojít pouze v textu jeho uzavření metoda, výrazu lambda nebo anonymní metody, která musí být označen `async` modifikátor. Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinam je interpretován jako identifikátor. V rámci metody, výrazu lambda nebo anonymní metody `await` výraz nemůže proběhnout v těle synchronní funkce ve výrazu dotazu v bloku [lock – příkaz](../../../csharp/language-reference/keywords/lock-statement.md), nebo [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu.  
  
## <a name="exceptions"></a>Výjimky  
Většina asynchronní metody vrátit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácený úlohy přenosu informací o jeho stav a historie, například zda byl dokončen, jestli asynchronní metody způsobila výjimku nebo byla zrušena a jaké konečný výsledek je. `await` Operátor přistupuje tyto vlastnosti voláním metody pro objekt vrácený `GetAwaiter` metoda.  
  
Pokud await vrácení úloh asynchronní metody, které způsobí výjimku, `await` operátor znovu vyvolá výjimku.  
  
Pokud await vrácení úloh asynchronní metody, kterou zruší, `await` znovu vyvolá operátor <xref:System.OperationCanceledException>.  
  
Jeden úkol, který je v chybovém stavu skutečnost více výjimek. Úloha může být například výsledek volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud jste await takové úlohy, znovu vyvolá operaci await pouze jeden z výjimky. Nelze však předpovědi, které výjimky znovu vyvolány.  
  
Příklady zpracování chyb v asynchronní metody naleznete v tématu [try-catch –](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Příklad  
Následující příklad vrátí celkový počet znaků v adresách URL jsou předány jako argumenty příkazového řádku stránky. Příklad volání `GetPageLengthsAsync` metodu, která je označena `async` – klíčové slovo. `GetPageLengthsAsync` Metoda dále používá `await` klíčové slovo await volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metoda.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Protože použití `async` a `await` v položce aplikace bodu není podporováno, nemůžeme použít `async` atribut `Main` metoda ani může jsme await `GetPageLengthsAsync` volání metody. Jsme zajistit, aby `Main` metoda čeká na dokončení načtením hodnotu asynchronní operace <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnost. Pro úlohy, která nevrátí hodnotu, můžete zavolat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda. 

## <a name="see-also"></a>Viz také  
[Asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md)   
[Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[async](../../../csharp/language-reference/keywords/async.md)
