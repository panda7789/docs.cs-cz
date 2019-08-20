---
title: await – C# referenční informace
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 2f6fb9fb8c29013165298c186ec072aa1e750ab9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602298"
---
# <a name="await-c-reference"></a>await – – operátor (Referenční dokumentace jazyka C#)
`await` Operátor je použit na úlohu v asynchronní metodě pro vložení bodu zavěšení při provádění metody do dokončení očekávané úlohy. Úkol představuje probíhající práci.  
  
`await`lze ji použít pouze v asynchronní metodě upravené klíčovým slovem [Async](./async.md) . Taková metoda, která je definována pomocí `async` modifikátoru a obvykle obsahuje jeden nebo více `await` výrazů, je označována jako *asynchronní metoda*.  
  
> [!NOTE]
> Klíčová `await` slova C# a byla představena v 5. `async` Úvod do asynchronního programování naleznete v tématu [asynchronní programování s Async a await](../../programming-guide/concepts/async/index.md).  
  
Úkol, na který `await` je operátor použit, obvykle je vrácen voláním metody, která implementuje [asynchronní vzor založený na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Zahrnují metody, které vracejí <xref:System.Threading.Tasks.Task>objekty <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, a <xref:System.Threading.Tasks.ValueTask%601> .  

V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda `Task<byte[]>`vrátí hodnotu. Úkol je příslib, který vytvoří skutečné bajtové pole po dokončení úkolu. Operátor pozastaví provádění, dokud nebude dokončena práce <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody. `await` Mezitím se ovládací prvek vrátí volajícímu `GetPageSizeAsync`. Po dokončení `await` úlohy se výraz vyhodnotí jako bajtové pole.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
> Úplný příklad najdete v tématu [Návod: Přístup k webu pomocí modifikátoru Async a](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)operátoru await Ukázku si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) na webu Microsoftu. Příklad je v projektu AsyncWalkthrough_HttpClient.  
  
Jak je znázorněno v předchozím příkladu, `await` Pokud je použita na výsledek volání metody, která `Task<TResult>`vrací, `await` potom je `TResult`typ výrazu. Pokud `await` je použita na výsledek volání metody, která `Task`vrací, `await` potom je `void`typ výrazu. Rozdíl je znázorněn v následujícím příkladu.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` Výraz neblokuje vlákno, na kterém je spuštěn. Místo toho způsobí, že kompilátor zaregistruje zbytek asynchronní metody jako pokračování u očekávané úlohy. Ovládací prvek se pak vrátí volajícímu asynchronní metody. Po dokončení úkolu vyvolá jeho pokračování a spuštění asynchronní metody pokračuje tam, kde skončila.  
  
Výraz může nastat pouze v těle své ohraničující metody, lambda výrazu nebo anonymní metody, které musí být označeny `async` modifikátorem. `await` Termín *await* slouží jako klíčové slovo pouze v tomto kontextu. Jinde je interpretován jako identifikátor. V rámci metody, výrazu lambda nebo anonymní metody `await` nemůže výraz nastat v těle synchronní funkce, ve výrazu dotazu, v bloku [příkazu Lock](./lock-statement.md)nebo v nebezpečném kontextu. [](./unsafe.md)  
  
## <a name="exceptions"></a>Výjimky  
Většina asynchronních metod vrací <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>. Vlastnosti vrácené úlohy obsahují informace o jeho stavu a historii, například o tom, zda je úloha dokončena, zda asynchronní metoda způsobila výjimku nebo byla zrušena a co je konečný výsledek. Operátor přistupuje k těmto vlastnostem voláním metod objektu vráceného `GetAwaiter` metodou. `await`  
  
Pokud očekáváte asynchronní metodu vracející úlohu, která způsobí výjimku, `await` operátor znovu vyvolá výjimku.  
  
Pokud očekáváte asynchronní metodu vracející úlohu, která je zrušena, `await` operátor znovu vyvolá. <xref:System.OperationCanceledException>  
  
Jeden úkol, který je v chybovém stavu, může odrážet více výjimek. Například úloha může být výsledkem volání metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Pokud očekáváte takovou úlohu, operace Await znovu vyvolá pouze jednu výjimku. Nemůžete však odhadnout, které výjimky jsou znovu vyvolány.  
  
Příklady zpracování chyb v asynchronních metodách naleznete v tématu [try-catch](./try-catch.md).  
  
## <a name="example"></a>Příklad  
Následující příklad vrátí celkový počet znaků na stránkách, jejichž adresy URL jsou do něj předány jako argumenty příkazového řádku. V příkladu je volána `GetPageLengthsAsync` metoda, která je označena `async` klíčovým slovem. Metoda zase pomocí klíčového slova očekává volání <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metody. `await` `GetPageLengthsAsync`  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

Předchozí příklad používá C# 7,1, který podporuje [ `async` `Main` metodu](../../programming-guide/main-and-command-args/index.md). Protože starší C# verze nepodporují vstupní body aplikací, které <xref:System.Threading.Tasks.Task> vracejí <xref:System.Threading.Tasks.Task%601>nebo, nemůžete `async` použít modifikátor na `Main` metodu a očekávat `GetPageLengthsAsync` volání metody. V takovém případě můžete zajistit, aby `Main` metoda čekala na dokončení asynchronní operace načtením hodnoty <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnosti. Pro úlohy, které nevracejí hodnotu, můžete zavolat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu. Informace o tom, jak vybrat jazykovou verzi, najdete v tématu [ C# výběr jazykové verze](../configure-language-version.md).

## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../programming-guide/concepts/async/index.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [async](./async.md)
