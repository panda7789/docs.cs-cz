---
title: Udělat volání bezpečná pro přístup z více vláken na ovládací prvky
ms.date: 02/19/2019
description: Naučte se implementovat multithreading ve vaší aplikaci voláním ovládacích prvků pro více vláken v bezpečném vlákně.
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
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904179"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Postupy: provádění volání bezpečných pro přístup z více vláken k ovládacím prvkům model Windows Forms

Multithreading může zlepšit výkon aplikací model Windows Forms, ale přístup k ovládacím prvkům model Windows Forms není v podstatě bezpečný pro přístup z více vláken. Multithreading může váš kód vystavit velmi vážným a složitým chybám. Dva nebo více vláken manipulující s ovládacím prvkem může vynutit ovládací prvek do nekonzistentního stavu a vést ke konfliktům časování, zablokování a zablokování nebo zablokování. Pokud implementujete multithreading v aplikaci, nezapomeňte volat ovládací prvky pro více vláken v bezpečném vlákně. Další informace najdete v tématu [osvědčené postupy pro spravované vlákno](../../../standard/threading/managed-threading-best-practices.md).

Existují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které tento ovládací prvek nevytvořil. Můžete použít <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metodu pro volání delegáta vytvořeného v hlavním vlákně, který zase volá ovládací prvek. Nebo můžete implementovat <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> , který používá model řízený událostmi k oddělení práce provedené ve vlákně na pozadí z vytváření sestav o výsledcích.

## <a name="unsafe-cross-thread-calls"></a>Nebezpečná volání mezi vlákny

Není bezpečné volat ovládací prvek přímo z vlákna, které ho nevytvořilo. Následující fragment kódu ilustruje nebezpečné volání <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> ovládacího prvku. `Button1_Click`Obslužná rutina události vytvoří nové `WriteTextUnsafe` vlákno, které nastaví vlastnost hlavního vlákna <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> přímo.

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

Ladicí program sady Visual Studio detekuje tato nebezpečná volání vláken tím <xref:System.InvalidOperationException> , že vyvolává zprávu, **operace křížového vlákna není platná. Ovládací prvek "", ke kterému se přistupoval z jiného vlákna než z vlákna, ve kterém byl vytvořen.** <xref:System.InvalidOperationException>Vždy dojde k nebezpečným voláním mezi vlákny během ladění sady Visual Studio a může dojít v modulu runtime aplikace. Měli byste problém vyřešit, ale tuto výjimku můžete zakázat nastavením <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> vlastnosti na `false` .

## <a name="safe-cross-thread-calls"></a>Bezpečná volání mezi vlákny

Následující příklady kódu ukazují dva způsoby, jak bezpečně volat ovládací prvek model Windows Forms z vlákna, které ho nevytvořilo:

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>Metoda, která volá delegáta z hlavního vlákna pro volání ovládacího prvku.
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>Komponenta, která nabízí model řízený událostmi.

V obou příkladech je vlákno na pozadí v jednom sekundu pro simulaci práce v tomto vlákně.

Tyto příklady můžete sestavit a spustit jako aplikace .NET Framework z příkazového řádku jazyka C# nebo Visual Basic. Další informace najdete v tématu [sestavování z příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Počínaje rozhraním .NET Core 3,0 můžete také sestavit a spustit příklady jako aplikace Windows .NET Core ze složky, která obsahuje soubor projektu .NET Core model Windows Forms * \<folder name> . csproj* .

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Příklad: použití metody Invoke s delegátem

Následující příklad ukazuje vzor pro zajištění volání bezpečného pro přístup z více vláken do ovládacího prvku model Windows Forms. Dotazuje se na <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> vlastnost, která porovnává vytvoření ID vlákna pro ID volajícího vlákna. Pokud jsou identifikátory vlákna stejné, volá ovládací prvek přímo. Pokud jsou ID vláken odlišná, volá <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metodu s delegátem z hlavního vlákna, které provádí vlastní volání ovládacího prvku.

`SafeCallDelegate`Umožňuje nastavit <xref:System.Windows.Forms.TextBox> vlastnost ovládacího prvku <xref:System.Windows.Forms.TextBox.Text%2A> . `WriteTextSafe`Metoda se dotazuje <xref:System.Windows.Forms.Control.InvokeRequired%2A> . Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true` , `WriteTextSafe` předává `SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A> metodu metodě, aby provedla skutečné volání ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false` se vrátí, `WriteTextSafe` nastaví <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> přímo. `Button1_Click`Obslužná rutina události vytvoří nové vlákno a spustí `WriteTextSafe` metodu.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Příklad: použití obslužné rutiny události BackgroundWorker

Snadný způsob, jak implementovat multithreading, je s <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> komponentou, která používá model řízený událostmi. Vlákno na pozadí spouští <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> událost, která nekomunikuje s hlavním vláknem. Hlavní vlákno spouští <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> obslužné rutiny události a, které mohou volat ovládací prvky hlavního vlákna.

Chcete-li provést volání bezpečné pro přístup z více vláken pomocí <xref:System.ComponentModel.BackgroundWorker> , vytvořte v vlákně na pozadí metodu, která provede práci, a navažte ji na <xref:System.ComponentModel.BackgroundWorker.DoWork> událost. Vytvořte další metodu v hlavním vlákně, abyste nahlásili výsledky práce na pozadí a navázali ji <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> na <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událost nebo. Chcete-li spustit vlákno na pozadí, zavolejte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> .

V příkladu se používá <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužná rutina události k nastavení <xref:System.Windows.Forms.TextBox> vlastnosti ovládacího prvku <xref:System.Windows.Forms.TextBox.Text%2A> . Příklad použití <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> události naleznete v tématu <xref:System.ComponentModel.BackgroundWorker> .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Vývoj vlastních ovládacích prvků model Windows Forms pomocí .NET Framework](developing-custom-windows-forms-controls.md)
