---
title: Volání ovládacích prvků bezpečná pro přístup z více vláken
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142001"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Postup: Volání ovládacích prvků windows forms bezpečných pro přístup z více vláken

Multithreading může zlepšit výkon aplikací pro Windows Forms, ale přístup k ovládacím prvkům Windows Forms není ze své podstaty bezpečný pro přístup z více vláken. Multithreading může vystavit váš kód velmi závažné a složité chyby. Dvě nebo více podprocesů manipulaci s ovládacím prvkem může vynutit ovládací prvek do nekonzistentního stavu a vést ke sporovým stavům, zablokování a zamrznutí nebo zablokování. Pokud implementujete multithreading ve vaší aplikaci, nezapomeňte volat ovládací prvky mezi vlákny bezpečným způsobem. Další informace naleznete v [tématu Osvědčené postupy spravovaného podprocesu](../../../standard/threading/managed-threading-best-practices.md).

Existují dva způsoby, jak bezpečně volat ovládací prvek Windows Forms z vlákna, které tento ovládací prvek nevytvořilo. Tuto metodu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> můžete použít k volání delegáta vytvořeného v hlavním vlákně, který zase volá ovládací prvek. Nebo můžete implementovat <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, který používá model řízený událostmi k oddělení práce provedené ve vlákně na pozadí od vykazování výsledků.

## <a name="unsafe-cross-thread-calls"></a>Nebezpečná volání mezi vlákny

Je nebezpečné volat ovládací prvek přímo z vlákna, které jej nevytvořilo. Následující fragment kódu ilustruje nebezpečné volání ovládacího <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> prvku. Obslužná `Button1_Click` `WriteTextUnsafe` rutina události vytvoří nové <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> vlákno, které přímo nastaví vlastnost hlavního vlákna.

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

Ladicí program sady Visual Studio zjistí tato <xref:System.InvalidOperationException> nebezpečná volání vlákna vyvoláním funkce s **neplatnou operací mezi vlákny. Ovládací prvek "" přistupovat z podprocesu než vlákno, které bylo vytvořeno na.** Vždy <xref:System.InvalidOperationException> dochází pro nebezpečné volání mezi vlákny během ladění sady Visual Studio a může dojít za běhu aplikace. Problém byste měli vyřešit, ale výjimku <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> můžete `false`zakázat nastavením vlastnosti na .

## <a name="safe-cross-thread-calls"></a>Bezpečná volání mezi vlákny

Následující příklady kódu ukazují dva způsoby, jak bezpečně volat ovládací prvek Windows Forms z vlákna, které jej nevytvořilo:

1. Metoda, <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> která volá delegáta z hlavního vlákna pro volání ovládacího prvku.
2. Součást, <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> která nabízí model řízený událostmi.

V obou příkladech podproces na pozadí spí po dobu jedné sekundy simulovat práci, která se provádí v tomto vlákně.

Tyto příklady můžete vytvořit a spustit jako aplikace rozhraní .NET Framework z příkazového řádku jazyka C# nebo Visual Basic. Další informace naleznete v [tématu Vytvoření příkazového řádku s csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [Sestavení z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Počínaje rozhraním .NET Core 3.0 můžete také vytvářet a spouštět příklady jako aplikace Windows .NET Core ze složky, která má název složky .NET Core Windows Forms * \<>.csproj* soubor projektu.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Příklad: Použití metody Invoke s delegátem

Následující příklad ukazuje vzor pro zajištění volání bezpečné pro přístup z více vláken ovládacího prvku Windows Forms. Dotazuje <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> vlastnost, která porovnává id vytvoření vlákna ovládacího prvku s ID volajícího vlákna. Pokud ID podprocesu jsou stejné, volá ovládací prvek přímo. Pokud ID podprocesu se liší, volá metodu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> s delegátem z hlavního vlákna, který provede skutečné volání ovládacího prvku.

Umožňuje `SafeCallDelegate` nastavení <xref:System.Windows.Forms.TextBox> vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A> ovládacího prvku. Metoda `WriteTextSafe` se <xref:System.Windows.Forms.Control.InvokeRequired%2A>dotazuje . Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true`vrátí `WriteTextSafe` , `SafeCallDelegate` předá metodu <xref:System.Windows.Forms.Control.Invoke%2A> provést skutečné volání ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false`vrátí `WriteTextSafe` , <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> nastaví přímo. Obslužná rutina `Button1_Click` události `WriteTextSafe` vytvoří nové vlákno a spustí metodu.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Příklad: Použití obslužné rutiny události BackgroundWorker

Snadný způsob, jak implementovat multithreading je s komponentou, <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> která používá model řízený událostmi. Podproces na <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> pozadí spustí událost, která nepracuje s hlavním vláknem. Hlavní vlákno spustí <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> obslužné rutiny a události, které mohou volat ovládací prvky hlavního vlákna.

Chcete-li provést volání bezpečné <xref:System.ComponentModel.BackgroundWorker>pro přístup z více vláken pomocí , vytvořte <xref:System.ComponentModel.BackgroundWorker.DoWork> metodu ve vlákně na pozadí, která provede práci, a spojte ji s událostí. Vytvořte jinou metodu v hlavním vlákně pro hlášení výsledků <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> práce na pozadí a svázání s událostí nebo. Chcete-li spustit vlákno <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>na pozadí, volejte .

Příklad používá <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužnou <xref:System.Windows.Forms.TextBox> rutinu <xref:System.Windows.Forms.TextBox.Text%2A> události k nastavení vlastnosti ovládacího prvku. Příklad použití události <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> naleznete <xref:System.ComponentModel.BackgroundWorker>v tématu .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.BackgroundWorker>
- [Postup: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)
- [Postup: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Vývoj vlastních ovládacích prvků windows forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
