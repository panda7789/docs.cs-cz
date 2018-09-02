---
title: async (Referenční dokumentace jazyka C#)
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 10f1d62c5aa29f2074106ab102775b9a0283d646
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389543"
---
# <a name="async-c-reference"></a>async (Referenční dokumentace jazyka C#)
Použití `async` modifikátor určit, že je metoda, [výraz lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), nebo [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) je asynchronní. Pokud použijete tento modifikátor na metodu nebo výraz, to se označuje jako *asynchronní metoda*. Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Pokud začínáte s asynchronním programováním nebo není srozumitelný použití asynchronní metody `await` – klíčové slovo provádět potenciálně dlouhotrvající práci bez blokování vlákna volajícího, přečtěte si úvod v kapitole [Asynchronous Programming with Async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md). Následující kód se nachází uvnitř a volá asynchronní metodu <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Asynchronní metoda pracuje synchronně, dokud nedosáhne svého prvního `await` výrazu, v tomto okamžiku je metoda pozastavena, dokud není dokončen očekávaný úkol. Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.  
  
Pokud metoda, která `async` upraví – klíčové slovo neobsahuje `await` výraz nebo příkaz, metoda je provedena synchronně. Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují slovo `await` příkazy, protože tato situace může značit chybu. Zobrazit [upozornění kompilátoru (úroveň 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` – Klíčové slovo je kontextové, v tom, že je klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje strukturu a tok řízení mezi asynchronním ovladačem událostí, `StartButton_Click`a asynchronní metody, `ExampleMethodAsync`. Výsledkem asynchronní metody je počet znaků na webové stránce. Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikace Windows Store, který vytvoříte v sadě Visual Studio; Podívejte se v komentářích ke kódu pro nastavení aplikace.  

Tento kód lze spustit v sadě Visual Studio jako aplikace Windows Presentation Foundation (WPF) nebo aplikaci Windows Store. Je třeba ovládacího prvku tlačítko s názvem `StartButton` a ovládacího prvku textového pole s názvem `ResultsTextBox`. Nezapomeňte nastavit názvy a obslužné rutiny, abyste měli vypadat přibližně takto:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Chcete-li spustit kód jako aplikaci WPF:  

- Vložte tento kód do `MainWindow` třídy v MainWindow.xaml.cs.  
- Přidejte odkaz na System.Net.Http.  
- Přidat `using` směrnice pro System.Net.Http.  
  
Chcete-li spustit kód jako aplikaci Windows Store:  
- Vložte tento kód do `MainPage` třídy v MainPage.xaml.cs.  
- Přidání direktivy using pro System.Net.Http a System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Další informace o úkolech a kódu, který se spustí při čekání na úlohy, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md). Úplný příklad WPF používající podobné prvky, naleznete v tématu [návod: přístup k webu pomocí Async a Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Návratové typy  
Asynchronní metoda může mít tyto návratové typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), která by měla sloužit pouze pro obslužné rutiny událostí.
- Od verze C# 7.0, libovolný typ, který má k dispozici přístup `GetAwaiter` metody. `System.Threading.Tasks.ValueTask<TResult>` Typ je jeden takový implementace. Je k dispozici přidáním balíčku NuGet `System.Threading.Tasks.Extensions`. 

Asynchronní metoda nemůže deklarovat všechny [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ani použít ji [odkazovat na návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody které mají tyto parametry.  
  
Zadáte `Task<TResult>` jako návratový typ asynchronní metody Pokud [vrátit](../../../csharp/language-reference/keywords/return.md) příkaz metody určuje operand typu `TResult`. Použijete `Task` Pokud není vrácena žádná smysluplná hodnota po dokončení metody. To znamená, volání metody vrací `Task`, ale když `Task` dokončení jakékoli `await` výraz, který čeká na `Task` vyhodnotí jako `void`.  
  
Můžete použít `void` především k definování obslužných rutin událostí, kde je požadován návratový typ. Volající `void`-asynchronní metody vracející ni nemohou čekat a zaznamenat tak výjimky, které metoda vyvolá.  

Od verze C# 7.0, vrátí jiný typ, obvykle hodnota typu, který má `GetAwaiter` metodu miminize přidělení paměti v kritickém pro výkon části kódu. 

Další informace a příklady najdete v tématu [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
- [await](../../../csharp/language-reference/keywords/await.md)  
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await](../../../csharp/programming-guide/concepts/async/index.md)
