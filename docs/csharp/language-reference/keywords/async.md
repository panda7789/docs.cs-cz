---
title: "async (Referenční dokumentace jazyka C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4a89736822342a9d9a24db6d43435f9795b81b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="async-c-reference"></a>async (Referenční dokumentace jazyka C#)
Použití `async` modifikátor určíte, že a metody [výrazu lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), nebo [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) je asynchronní. Pokud použijete tento modifikátor způsobu nebo výraz, ho se označuje jako *asynchronní metody*. V následujícím příkladu definuje použití asynchronní metody s názvem `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Pokud jste ještě nikdy nepracovali do asynchronního programování nebo není srozumitelný používání asynchronní metody `await` – klíčové slovo práci potenciálně dlouhotrvající bez blokování vláken volajícího, přečtěte si úvod v [asynchronní programování s Async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md). Následující kód je nalezena uvnitř asynchronní metody a počet volání <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metoda: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Asynchronní metody spouští synchronně, dokud nebude dosaženo prvním `await` výrazu, v tomto okamžiku je metoda pozastaveno, dokud awaited úkol je dokončen. Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.  
  
Pokud metodě, `async` upraví – klíčové slovo neobsahuje `await` výraz nebo příkaz metoda spustí synchronně. Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují žádný `await` příkazy, protože tato situace může znamenat chybu. V tématu [upozornění kompilátoru (úroveň 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` – Klíčové slovo je kontextová v, aby se klíčové slovo jenom v případě, že upravuje metodu, výraz lambda nebo anonymní metody. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje strukturu a toku řízení mezi obslužnou rutinu události asynchronní `StartButton_Click`a použití asynchronní metody `ExampleMethodAsync`. Výsledek z asynchronní metody je počet znaků webové stránky. Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store, které vytvoříte v sadě Visual Studio; Zobrazte komentáře kódu pro nastavení aplikace.  

Tento kód můžete spustit v sadě Visual Studio jako aplikace Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store. Je třeba ovládacího prvku tlačítko s názvem `StartButton` a ovládací prvek textové pole s názvem `ResultsTextBox`. Nezapomeňte nastavit názvy a obslužné rutiny tak, že máte přibližně takto:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Kód spuštění jako aplikaci WPF:  

- Vložte tento kód do `MainWindow` třídy v MainWindow.xaml.cs.  
- Přidáte odkaz na System.Net.Http.  
- Přidat `using` direktivy pro System.Net.Http.  
  
Chcete-li spustit kód jako aplikace pro Windows Store:  
- Vložte tento kód do `MainPage` třídy v MainPage.xaml.cs.  
- Přidání direktivy using pro System.Net.Http a System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Další informace o úlohách a kód, který se spustí při čekání na úlohu najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md). Úplný příklad WPF, který používá podobným elementům, najdete v části [návod: přístup k webu pomocí modifikátoru Async a Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Návratové typy  
Asynchronní metody může mít následující návratové typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), které musí být použit pouze pro obslužné rutiny událostí.
- Od verze jazyka C# 7, žádný typ, který má přístupné `GetAwaiter` metoda. `System.Threading.Tasks.ValueTask<TResult>` Typ je jednou z těchto implementací. Je k dispozici přidáním balíček NuGet `System.Threading.Tasks.Extensions`. 

Asynchronní metody nelze deklarovat všechny [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out.md) parametry, ani může ho mít <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->návratovou hodnotu odkazu, ale můžete volat metody, které mají tyto parametry.  
  
Zadáte `Task<TResult>` jako návratový typ asynchronní metody Pokud [vrátit](../../../csharp/language-reference/keywords/return.md) příkaz metody určuje operand typu `TResult`. Používáte `Task` Pokud žádná smysluplný hodnota je vrácena, pokud je metoda dokončena. To znamená, vrátí volání do metody `Task`, ale při `Task` dokončení žádné `await` výraz, který se čeká na `Task` vyhodnotí jako `void`.  
  
Můžete použít `void` návratový typ primárně k definování obslužné rutiny událostí, které vyžadují, které vrací typ. Volající `void`-vrátíte asynchronní metody nelze await a nemůže catch výjimky, které vyvolá metoda.  

Od verze jazyka C# 7, vrátíte jiného typu, obvykle hodnota typu, který má `GetAwaiter` metoda přidělení paměti miminize v výkonu kritická sekce kódu. 

Další informace a příklady naleznete v tématu [asynchronní vrátit typy](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [await](../../../csharp/language-reference/keywords/await.md)  
 [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md)
