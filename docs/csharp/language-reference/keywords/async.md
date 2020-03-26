---
title: asynchronní – odkaz jazyka C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 89133339a75c70e3ac86d627065e78d555bff71d
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507201"
---
# <a name="async-c-reference"></a>async (Referenční dokumentace jazyka C#)

Modifikátor slouží k určení, že metoda, [výraz lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo anonymní metoda je asynchronní. [anonymous method](../operators/delegate-operator.md) `async` Pokud použijete tento modifikátor na metodu nebo výraz, je označován jako *asynchronní metoda*. Následující příklad definuje asynchronní `ExampleMethodAsync`metodu s názvem :
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Pokud jste novým asynchronní programování nebo nerozumíte, jak asynchronní metoda používá [ `await` operátor](../operators/await.md) k tomu potenciálně dlouhotrvající práci bez blokování volajícího vlákno, přečtěte si úvod v [asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md). Následující kód se nachází uvnitř asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody a volá metodu:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Asynchronní metoda se spouští synchronně, `await` dokud nedosáhne svého prvního výrazu, kdy je metoda pozastavena, dokud není očekávaná úloha dokončena. Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.  
  
Pokud metoda, `async` kterou klíčové slovo upravuje, neobsahuje `await` výraz nebo příkaz, metoda se provede synchronně. Upozornění kompilátoru vás upozorní na všechny asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu. Viz [Upozornění kompilátoru (úroveň 1) CS4014](../compiler-messages/cs4014.md).  
  
 Klíčové `async` slovo je kontextové v tom, že je klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu. Ve všech ostatních kontextech je interpretováno jako identifikátor.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje strukturu a tok řízení mezi `StartButton_Click`obslužnou rutinou asynchronní události a asynchronní metodou `ExampleMethodAsync`. Výsledkem asynchronní metody je počet znaků webové stránky. Kód je vhodný pro aplikaci WPF (Windows Presentation Foundation) nebo pro Windows Store, kterou vytvoříte ve Visual Studiu. podívejte se na komentáře kódu pro nastavení aplikace.  

Tento kód můžete spustit ve Visual Studiu jako aplikaci WPF (Windows Presentation Foundation) nebo windows store. Potřebujete ovládací prvek `StartButton` Button s názvem `ResultsTextBox`a ovládací prvek Textové pole s názvem . Nezapomeňte nastavit jména a obslužnou rutinu tak, abyste měli něco takového:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Spuštění kódu jako aplikace WPF:  

- Vložte tento `MainWindow` kód do třídy v MainWindow.xaml.cs.  
- Přidejte odkaz na System.Net.Http.  
- Přidejte `using` direktivu pro System.Net.Http.  
  
Spuštění kódu jako aplikace pro Windows Store:  

- Vložte tento `MainPage` kód do třídy v MainPage.xaml.cs.  
- Přidat pomocí direktiv pro System.Net.Http a System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Další informace o úkolech a kódu, který se provádí při čekání na úlohu, naleznete [v tématu Asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md). Úplný příklad WPF, který používá podobné prvky, naleznete [v tématu Návod: Přístup k webu pomocí Async a Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Návratové typy  
Asynchronní metoda může mít následující návratové typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [neplatné](../builtin-types/void.md). `async void`Metody jsou obecně nedoporučuje pro kód než obslužné rutiny událostí, protože volající nemohou `await` tyto metody a musí implementovat jiný mechanismus pro hlášení úspěšné dokončení nebo chybové stavy.
- Počínaje C# 7.0, libovolný typ, `GetAwaiter` který má přístupnou metodu. Typ `System.Threading.Tasks.ValueTask<TResult>` je jedna taková implementace. Je k dispozici přidáním `System.Threading.Tasks.Extensions`balíčku NuGet .

Asynchronní metoda nemůže deklarovat žádné [parametry in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out,](./out-parameter-modifier.md) ani nemůže mít [referenční vrácenou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají takové parametry.  
  
Jako `Task<TResult>` návratový typ asynchronní metody zadáte, pokud [příkaz return](./return.md) metody určuje `TResult`operand typu . Můžete `Task` použít, pokud není vrácena žádná smysluplná hodnota po dokončení metody. To znamená, že volání metody `Task`vrátí , `Task` ale po `await` dokončení, jakýkoli výraz, který čeká na `Task` vyhodnocuje `void`.  
  
Návratový `void` typ slouží především k definování obslužných rutin událostí, které tento návratový typ vyžadují. Volající `void`-vracející asynchronní metoda nemůže čekat a nemůže zachytit výjimky, které metoda vyvolá.  

Počínaje C# 7.0 vrátíte jiný typ, obvykle typ hodnoty, který má metodu `GetAwaiter` minimalizovat přidělení paměti v části kódu kritické pro výkon.

Další informace a příklady naleznete [v tématu Asynchronní návratové typy](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Návod: Přístup k webu pomocí Async a Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s asynchronní a čekají](../../programming-guide/concepts/async/index.md)
