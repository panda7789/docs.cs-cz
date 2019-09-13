---
title: 'Postupy: Provádění volání bezpečných pro přístup z více vláken na ovládací prvky model Windows Forms'
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928621"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Postupy: Provádění volání bezpečných pro přístup z více vláken na ovládací prvky model Windows Forms

Multithreading může zlepšit výkon aplikací model Windows Forms, ale přístup k ovládacím prvkům model Windows Forms není v podstatě bezpečný pro přístup z více vláken. Multithreading může váš kód vystavit velmi vážným a složitým chybám. Dva nebo více vláken manipulující s ovládacím prvkem může vynutit ovládací prvek do nekonzistentního stavu a vést ke konfliktům časování, zablokování a zablokování nebo zablokování. Pokud implementujete multithreading v aplikaci, nezapomeňte volat ovládací prvky pro více vláken v bezpečném vlákně. Další informace najdete v tématu [osvědčené postupy pro spravované vlákno](../../../standard/threading/managed-threading-best-practices.md). 

Existují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které tento ovládací prvek nevytvořil. Můžete použít <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metodu pro volání delegáta vytvořeného v hlavním vlákně, který zase volá ovládací prvek. Nebo můžete implementovat <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, který používá model řízený událostmi k oddělení práce provedené ve vlákně na pozadí z vytváření sestav o výsledcích. 

## <a name="unsafe-cross-thread-calls"></a>Nebezpečná volání mezi vlákny

Není bezpečné volat ovládací prvek přímo z vlákna, které ho nevytvořilo. Následující fragment kódu ilustruje nebezpečné volání <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> ovládacího prvku. Obslužná rutina `WriteTextUnsafe`událostivytvoří nové vlákno, které <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> nastaví vlastnost hlavního vlákna přímo. `Button1_Click` 

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

Ladicí program sady Visual Studio detekuje tato nebezpečná volání vláken tím <xref:System.InvalidOperationException> , že vyvolává zprávu **, operace křížového vlákna není platná. Ovládací prvek "", ke kterému se přistupoval z jiného vlákna než z vlákna, ve kterém byl vytvořen.** <xref:System.InvalidOperationException> Vždy dojde k nebezpečným voláním mezi vlákny během ladění sady Visual Studio a může dojít v modulu runtime aplikace. Měli byste problém vyřešit, ale tuto výjimku můžete zakázat nastavením <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> vlastnosti na. `false`

## <a name="safe-cross-thread-calls"></a>Bezpečná volání mezi vlákny 

Následující příklady kódu ukazují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které ho nevytvořilo: 

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Metoda, která volá delegáta z hlavního vlákna pro volání ovládacího prvku. 
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> Komponenta, která nabízí model řízený událostmi. 

V obou příkladech je vlákno na pozadí v jednom sekundu pro simulaci práce v tomto vlákně. 

Tyto příklady můžete sestavit a spustit jako aplikace .NET Framework z příkazového C# řádku nebo Visual Basic. Další informace najdete v tématu [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Počínaje rozhraním .NET Core 3,0 můžete také sestavit a spustit příklady jako aplikace Windows .NET Core ze složky, která má  *\<název složky* model Windows Forms .NET Core > souboru projektu. csproj. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Příklad: Použití metody Invoke s delegátem

Následující příklad ukazuje vzor pro zajištění volání bezpečného pro přístup z více vláken do ovládacího prvku model Windows Forms. Dotazuje se <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> na vlastnost, která porovnává vytvoření ID vlákna pro ID volajícího vlákna. Pokud jsou identifikátory vlákna stejné, volá ovládací prvek přímo. Pokud jsou ID vláken odlišná, volá <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metodu s delegátem z hlavního vlákna, které provádí vlastní volání ovládacího prvku.

Umožňuje nastavit vlastnost<xref:System.Windows.Forms.TextBox.Text%2A>ovládacíhoprvku. <xref:System.Windows.Forms.TextBox> `SafeCallDelegate` Metoda `WriteTextSafe` se dotazuje <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true` ,`WriteTextSafe` předává`SafeCallDelegate`metodumetodě , aby provedla skutečné volání ovládacího prvku. <xref:System.Windows.Forms.Control.Invoke%2A> Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> se `false`vrátí ,`WriteTextSafe` nastaví<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> přímo. Obslužná rutina `WriteTextSafe`událostivytvoří nové vlákno a spustí metodu. `Button1_Click` 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Příklad: Použití obslužné rutiny události BackgroundWorker

Snadný způsob, jak implementovat multithreading, je s <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> komponentou, která používá model řízený událostmi. Vlákno na pozadí spouští <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> událost, která nekomunikuje s hlavním vláknem. Hlavní vlákno spouští <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> události a, které mohou volat ovládací prvky hlavního vlákna.

Chcete-li provést volání bezpečné pro přístup z <xref:System.ComponentModel.BackgroundWorker>více vláken pomocí, vytvořte v vlákně na pozadí metodu, která provede práci, a navažte ji <xref:System.ComponentModel.BackgroundWorker.DoWork> na událost. Vytvořte další metodu v hlavním vlákně, abyste nahlásili výsledky práce na pozadí a navázali ji <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> na <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událost nebo. Chcete-li spustit vlákno na pozadí <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>, zavolejte. 

V příkladu se používá <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužná rutina události k <xref:System.Windows.Forms.TextBox> nastavení <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti ovládacího prvku. Příklad použití <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události naleznete v tématu <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Vývoj vlastních ovládacích prvků model Windows Forms pomocí .NET Framework](developing-custom-windows-forms-controls.md)
