---
title: asynchronní C# odkaz
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 3d3f045eed3bad3624ed4994aebb862c52a4e196
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713783"
---
# <a name="async-c-reference"></a>async (Referenční dokumentace jazyka C#)

Použijte modifikátor `async` k určení, že metoda, [výraz lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metoda](../operators/delegate-operator.md) je asynchronní. Použijete-li tento modifikátor na metodu nebo výraz, je označována jako *asynchronní metoda*. Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync`:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Pokud s asynchronním programováním začínáte a nerozumíte tomu, jak asynchronní metoda používá [operátor`await`](../operators/await.md) pro potenciálně dlouhotrvající práci bez blokování vlákna volajícího, přečtěte si Úvod do [asynchronního programování pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/index.md). Následující kód byl nalezen v asynchronní metodě a volá metodu <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Asynchronní metoda běží synchronně, dokud nedosáhne prvního `await` výrazu, na kterém je metoda pozastavena, dokud není dokončen očekávaný úkol. Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.  
  
Pokud metoda, kterou klíčová slova `async` upravuje, neobsahuje výraz nebo příkaz `await`, metoda se provede synchronně. Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu. Viz [Upozornění kompilátoru (úroveň 1) CS4014](../compiler-messages/cs4014.md).  
  
 Klíčové slovo `async` je kontextové v tom, že se jedná o klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje strukturu a tok řízení mezi obslužnou rutinou asynchronní události, `StartButton_Click`a asynchronní metodou `ExampleMethodAsync`. Výsledek z asynchronní metody je počet znaků webové stránky. Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikaci pro Windows Store, kterou vytvoříte v aplikaci Visual Studio; Podívejte se na komentáře ke kódu pro nastavení aplikace.  

Tento kód můžete spustit v aplikaci Visual Studio jako aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store. Potřebujete ovládací prvek tlačítko s názvem `StartButton` a ovládací prvek TextBox s názvem `ResultsTextBox`. Nezapomeňte nastavit názvy a obslužné rutiny tak, abyste měli něco podobného:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Spuštění kódu jako aplikace WPF:  

- Vložte tento kód do třídy `MainWindow` v MainWindow.xaml.cs.  
- Přidejte odkaz na System .NET. http.  
- Přidejte direktivu `using` pro System .NET. http.  
  
Spuštění kódu jako aplikace pro Windows Store:  

- Vložte tento kód do třídy `MainPage` v MainPage.xaml.cs.  
- Přidejte direktivy using pro System .NET. http a System. Threading. Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Další informace o úlohách a kódu, který se spouští při čekání na úlohu, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../programming-guide/concepts/async/index.md). Úplný příklad WPF, který používá podobné prvky, naleznete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Návratové typy  
Asynchronní metoda může mít následující návratové typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](./void.md). metody `async void` jsou obecně nedoporučovány pro jiný kód než obslužné rutiny událostí, protože volající nemohou `await` tyto metody a musí implementovat jiný mechanismus, který bude hlásit úspěšné dokončení nebo chybové stavy.
- Počínaje C# 7,0, jakýkoli typ, který má přístupnou metodu `GetAwaiter`. Typ `System.Threading.Tasks.ValueTask<TResult>` představuje jednu takovou implementaci. Je k dispozici přidáním balíčku NuGet `System.Threading.Tasks.Extensions`. 

Asynchronní metoda nemůže deklarovat jakýkoli parametr [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md) , ani nemůže mít [odkazovou návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají tyto parametry.  
  
Zadejte `Task<TResult>` jako návratový typ asynchronní metody, pokud příkaz [return](./return.md) metody určuje operand typu `TResult`. Použijete `Task`, pokud není vrácena žádná smysluplná hodnota po dokončení metody. To znamená, že volání metody vrací `Task`, ale po dokončení `Task` všechny `await` výrazy, které čekají `Task`, se vyhodnotí jako `void`.  
  
Použijte `void` návratový typ primárně k definování obslužných rutin událostí, které vyžadují návratový typ. Volající asynchronní metody vracející `void`nemůže použít operátor await a nemůže zachytit výjimky, které metoda vyvolá.  

Počínaje C# 7,0 vrátíte jiný typ, obvykle hodnotový typ, který má metodu `GetAwaiter` pro minimalizaci přidělení paměti v částech kódu kritických pro výkon. 

Další informace a příklady naleznete v tématu [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../programming-guide/concepts/async/index.md)
