---
title: Udělat volání bezpečná pro přístup z více vláken na ovládací prvky
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 101457ab2a02b8de49d06c354ca307e07b690ba2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736159"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Postupy: provádění volání bezpečných pro přístup z více vláken k ovládacím prvkům model Windows Forms

Multithreading může zlepšit výkon aplikací model Windows Forms, ale přístup k ovládacím prvkům model Windows Forms není v podstatě bezpečný pro přístup z více vláken. Multithreading může váš kód vystavit velmi vážným a složitým chybám. Dva nebo více vláken manipulující s ovládacím prvkem může vynutit ovládací prvek do nekonzistentního stavu a vést ke konfliktům časování, zablokování a zablokování nebo zablokování. Pokud implementujete multithreading v aplikaci, nezapomeňte volat ovládací prvky pro více vláken v bezpečném vlákně. Další informace najdete v tématu [osvědčené postupy pro spravované vlákno](../../../standard/threading/managed-threading-best-practices.md). 

Existují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které tento ovládací prvek nevytvořil. Můžete použít metodu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> pro volání delegáta vytvořeného v hlavním vlákně, který zase volá ovládací prvek. Nebo můžete implementovat <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, která používá model řízený událostmi k oddělení práce provedené ve vlákně na pozadí z vytváření sestav o výsledcích. 

## <a name="unsafe-cross-thread-calls"></a>Nebezpečná volání mezi vlákny

Není bezpečné volat ovládací prvek přímo z vlákna, které ho nevytvořilo. Následující fragment kódu ilustruje nebezpečné volání ovládacího prvku <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>. Obslužná rutina události `Button1_Click` vytvoří nové vlákno `WriteTextUnsafe`, které nastaví vlastnost <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> hlavního vlákna přímo. 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Ladicí program sady Visual Studio detekuje tato nebezpečná volání vlákna tím, že vyvolává <xref:System.InvalidOperationException> se zprávou, **operace křížového vlákna není platná. Ovládací prvek "", ke kterému se přistupoval z jiného vlákna než z vlákna, ve kterém byl vytvořen.** <xref:System.InvalidOperationException> vždy dochází pro nebezpečná volání mezi vlákny během ladění sady Visual Studio a může dojít v modulu runtime aplikace. Měli byste problém vyřešit, ale tuto výjimku můžete zakázat nastavením vlastnosti <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> na `false`.

## <a name="safe-cross-thread-calls"></a>Bezpečná volání mezi vlákny 

Následující příklady kódu ukazují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které ho nevytvořilo: 

1. Metoda <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>, která volá delegáta z hlavního vlákna pro volání ovládacího prvku. 
2. Komponenta <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, která nabízí model řízený událostmi. 

V obou příkladech je vlákno na pozadí v jednom sekundu pro simulaci práce v tomto vlákně. 

Tyto příklady můžete sestavit a spustit jako aplikace .NET Framework z příkazového C# řádku nebo Visual Basic. Další informace najdete v tématu [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Počínaje rozhraním .NET Core 3,0 můžete také sestavit a spustit příklady jako aplikace Windows .NET Core ze složky, která má model Windows Forms *\<název složky >. csproj* souboru projektu rozhraní .NET Core. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Příklad: použití metody Invoke s delegátem

Následující příklad ukazuje vzor pro zajištění volání bezpečného pro přístup z více vláken do ovládacího prvku model Windows Forms. Dotazuje se na vlastnost <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>, která porovnává vytvoření ID vlákna pro ID volajícího vlákna. Pokud jsou identifikátory vlákna stejné, volá ovládací prvek přímo. Pokud jsou ID vláken odlišná, volá metodu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> s delegátem z hlavního vlákna, které provádí vlastní volání ovládacího prvku.

`SafeCallDelegate` umožňuje nastavit vlastnost <xref:System.Windows.Forms.TextBox.Text%2A> ovládacího prvku <xref:System.Windows.Forms.TextBox>. Metoda `WriteTextSafe` se dotazuje <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, `WriteTextSafe` předá `SafeCallDelegate` metodě <xref:System.Windows.Forms.Control.Invoke%2A>, aby mohl uskutečnit vlastní volání ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `false`, `WriteTextSafe` nastaví <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> přímo. Obslužná rutina události `Button1_Click` vytvoří nové vlákno a spustí metodu `WriteTextSafe`. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Příklad: použití obslužné rutiny události BackgroundWorker

Snadný způsob, jak implementovat multithreading, je pomocí komponenty <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, která používá model řízený událostmi. Vlákno na pozadí spouští událost <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>, která nekomunikuje s hlavním vláknem. Hlavní vlákno spustí <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> obslužné rutiny událostí, které mohou volat ovládací prvky hlavního vlákna.

Chcete-li provést volání bezpečné pro přístup z více vláken pomocí <xref:System.ComponentModel.BackgroundWorker>, vytvořte v vlákně na pozadí metodu, která provede práci, a navažte ji na událost <xref:System.ComponentModel.BackgroundWorker.DoWork>. Vytvořte další metodu v hlavním vlákně, abyste nahlásili výsledky práce na pozadí a navázali ji na <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> nebo <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událost. Chcete-li spustit vlákno na pozadí, zavolejte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

V příkladu se používá obslužná rutina události <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> k nastavení vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A> ovládacího prvku <xref:System.Windows.Forms.TextBox>. Příklad použití události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> naleznete v tématu <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Vývoj vlastních ovládacích prvků model Windows Forms pomocí .NET Framework](developing-custom-windows-forms-controls.md)
