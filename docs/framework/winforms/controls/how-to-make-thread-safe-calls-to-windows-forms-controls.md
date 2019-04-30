---
title: 'Postupy: Volání bezpečné pro vlákna ovládacích prvků Windows Forms'
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
ms.openlocfilehash: 3211df1f0e585780039471b80b5b913613ad9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913793"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Postupy: Volání bezpečné pro vlákna ovládacích prvků Windows Forms

Multithreading může zlepšit výkon aplikací Windows Forms, ale přístup k ovládacím prvkům Windows Forms není ze své podstaty bezpečné pro vlákna. Multithreading můžete zveřejnit kód do velmi závažných a složitých chyb. Dvě či více vláken manipulace s ovládacím můžete vynutit ovládacího prvku do nekonzistentního stavu a vést ke konfliktům časování, zablokování a zablokuje nebo přestane reagovat. Pokud se rozhodnete implementovat multithreadingu ve vaší aplikaci, nezapomeňte volat ovládacích prvků mezi vlákny způsobem bezpečným pro vlákno. Další informace najdete v tématu [dělení na spravovaná vlákna osvědčené postupy](../../../standard/threading/managed-threading-best-practices.md). 

Existují dva způsoby, jak bezpečně volat z vlákna, které se nepovedlo vytvořit ovládací prvek ovládacího prvku Windows Forms. Můžete použít <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metoda volání delegáta vytvořené v hlavním vlákně, které volá ovládacího prvku. Nebo můžete implementovat <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, který používá model založený na událostech pro oddělení práce ve vlákně na pozadí ze sestav na výsledky. 

## <a name="unsafe-cross-thread-calls"></a>Nezabezpečený volání mezi vlákny

Není bezpečné volat ovládacího prvku přímo z vlákna, které se nepovedlo vytvořit. Následující fragment kódu ukazuje nebezpečné volání <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> ovládacího prvku. `Button1_Click` Obslužná rutina události vytvoří novou `WriteTextUnsafe` podproces, který nastaví hlavní vlákno <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> vlastnost přímo. 

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

Ladicí program sady Visual Studio zjistí těchto nebezpečné vlákna volání vyvoláním <xref:System.InvalidOperationException> se zprávou, **operace mezi vlákny není platná. Ovládací prvek "" k němu přistupovat z vlákna kromě vlákna byl vytvořen.** <xref:System.InvalidOperationException> Vždy dojde k unsafe volání mezi vlákny během ladění sady Visual Studio a může dojít za běhu aplikace. By měla vyřešit problém, ale výjimky lze zakázat nastavením <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> vlastnost `false`.

## <a name="safe-cross-thread-calls"></a>Bezpečné volání mezi vlákny 

Následující příklady kódu znázorňují dva způsoby, jak bezpečně volat ovládacího prvku Windows Forms z vlákna, které se nepovedlo vytvořit: 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Metoda, která volá delegáta z hlavního vlákna volání ovládacího prvku. 
2. A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> komponenta, která nabízí model založený na událostech. 

V obou příkladech pozadí vlákno uspí jedné sekundy simulace práce prováděné v tomto vlákně. 

Můžete sestavit a spustit tyto příklady jako aplikace rozhraní .NET Framework C# nebo příkazového řádku jazyka Visual Basic. Další informace najdete v tématu [příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Od verze .NET Core 3.0, můžete také sestavit a spustit v příkladech jako Windows aplikace .NET Core ze složky, která má formulářů Windows .NET Core  *\<název složky > .csproj* souboru projektu. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Příklad: Metodu vyvolat pomocí delegáta

Následující příklad ukazuje vzor pro zajištění bezpečné pro vlákna volání ovládacího prvku Windows Forms. Vyžádá si <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> vlastnost, která porovnává ovládacího prvku na vytváření ID vlákna na ID volajícího vlákna. Pokud ID vlákna jsou stejné, zavolá ovládacího prvku přímo. Pokud ID vlákna se liší, zavolá <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metody delegáta z hlavního vlákna, která díky vlastnímu volání do ovládacího prvku.

`SafeCallDelegate` Umožňuje nastavení <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost. `WriteTextSafe` Metoda dotazy <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, `WriteTextSafe` předává `SafeCallDelegate` k <xref:System.Windows.Forms.Control.Invoke%2A> metoda skutečné volání do ovládacího prvku. Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `false`, `WriteTextSafe` nastaví <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> přímo. `Button1_Click` Obslužná rutina události vytvoří nové vlákno a spustí `WriteTextSafe` metody. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Příklad: Použijte obslužnou rutinu události podproces BackgroundWorker

Snadný způsob, jak se implementují multithreading <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> komponenta, která používá model založený na událostech. Vlákno na pozadí spouští <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> událost, která nepracuje s hlavním vlákně. Hlavní vlákno běží <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> obslužné rutiny událostí, které můžete volat ovládací prvky hlavního vlákna.

Volání bezpečným pro vlákno s použitím <xref:System.ComponentModel.BackgroundWorker>, vytvořte metodu ve vlákně na pozadí pro práci a vytvořte mu vazbu k <xref:System.ComponentModel.BackgroundWorker.DoWork> událostí. Vytvořte jinou metodu v hlavním vlákně do sestavy o výsledcích práce na pozadí a vytvořte mu vazbu k <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> nebo <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí. Chcete-li spustit vlákno na pozadí, zavolejte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

V příkladu se používá <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužnou rutinu události pro nastavení <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost. Příklad použití <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí, naleznete v tématu <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- [Postupy: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Vývoj vlastních ovládacích prvků Windows Forms s použitím rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
