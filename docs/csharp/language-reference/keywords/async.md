---
title: asynchronní C# odkaz
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 3bf71bbe0e3f4e14f140f5a1b98a662ceaaea419
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68362992"
---
# <a name="async-c-reference"></a>async (Referenční dokumentace jazyka C#)

Použijte modifikátor k určení toho, že metoda, [výraz lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metoda](../../../csharp/language-reference/operators/delegate-operator.md) je asynchronní. `async` Použijete-li tento modifikátor na metodu nebo výraz, je označována jako *asynchronní metoda*. Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync`:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Pokud začínáte s asynchronním programováním nebo nerozumíte, jak asynchronní metoda používá `await` klíčové slovo pro potenciálně dlouhodobě spuštěnou práci bez blokování vlákna volajícího, přečtěte si Úvod do [asynchronního programování s použitím modifikátoru Async a očekává](../../../csharp/programming-guide/concepts/async/index.md)se. Následující kód byl nalezen v asynchronní metodě a volá <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodu: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Asynchronní metoda běží synchronně, dokud nedosáhne svého prvního `await` výrazu, v tomto okamžiku je metoda pozastavena, dokud není dokončen očekávaný úkol. Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.  
  
Pokud metoda, kterou `async` klíčové slovo upravuje `await` , neobsahuje výraz nebo příkaz, metoda se provede synchronně. Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu. Viz [Upozornění kompilátoru (úroveň 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` Klíčové slovo je kontextové v tom, že se jedná o klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje strukturu a tok řízení mezi obslužnou rutinou asynchronní události, `StartButton_Click`a asynchronní `ExampleMethodAsync`metodou. Výsledek z asynchronní metody je počet znaků webové stránky. Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikaci pro Windows Store, kterou vytvoříte v aplikaci Visual Studio; Podívejte se na komentáře ke kódu pro nastavení aplikace.  

Tento kód můžete spustit v aplikaci Visual Studio jako aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store. Potřebujete ovládací prvek tlačítko s názvem `StartButton` a ovládací prvek TextBox s `ResultsTextBox`názvem. Nezapomeňte nastavit názvy a obslužné rutiny tak, abyste měli něco podobného:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Spuštění kódu jako aplikace WPF:  

- Vložte tento kód do `MainWindow` třídy v MainWindow.XAML.cs.  
- Přidejte odkaz na System .NET. http.  
- `using` Přidejte direktivu pro System .NET. http.  
  
Spuštění kódu jako aplikace pro Windows Store:  
- Vložte tento kód do `MainPage` třídy v MainPage.XAML.cs.  
- Přidejte direktivy using pro System .NET. http a System. Threading. Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Další informace o úlohách a kódu, který se spouští při čekání na úlohu, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../csharp/programming-guide/concepts/async/index.md). Úplný příklad WPF, který používá podobné prvky, naleznete v [tématu Návod: Přístup k webu pomocí modifikátoru Async a](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)operátoru await  
  
## <a name="return-types"></a>Návratové typy  
Asynchronní metoda může mít následující návratové typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md). `async void`metody se obecně nedoporučují pro jiný kód než obslužné rutiny událostí, protože `await` volající nemůžou tyto metody a musí implementovat jiný mechanismus, aby hlásili úspěšné dokončení nebo chybové stavy.
- Počínaje C# 7,0, jakýkoli typ, který má přístupnou `GetAwaiter` metodu. `System.Threading.Tasks.ValueTask<TResult>` Typ představuje jednu takovou implementaci. Je k dispozici přidáním balíčku `System.Threading.Tasks.Extensions`NuGet. 

Asynchronní metoda nemůže deklarovat jakýkoli parametr [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) , ani nemůže mít [odkazovou návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají tyto parametry.  
  
Zadáte `Task<TResult>` jako návratový typ asynchronní metody, pokud příkaz [return](../../../csharp/language-reference/keywords/return.md) metody určuje operand typu `TResult`. Použijete `Task` , pokud není vrácena žádná smysluplná hodnota po dokončení metody. To znamená, `Task`že volání metody vrátí, ale `Task` po dokončení je libovolný `await` výraz `void`, který čeká `Task` na vyhodnotit.  
  
Pro definování obslužných rutin událostí, které vyžadují návratový typ, použijte `void` primárně návratový typ. Volající `void`asynchronní metody vracející výjimku nemůže očekávat a zachytit výjimky, které metoda vyvolá.  

Počínaje C# 7,0 vrátíte jiný typ, obvykle hodnotový typ, který má `GetAwaiter` metodu pro minimalizaci přidělení paměti v částech v kódu kritickém pro výkon. 

Další informace a příklady naleznete v tématu [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../../../csharp/language-reference/keywords/await.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/index.md)
