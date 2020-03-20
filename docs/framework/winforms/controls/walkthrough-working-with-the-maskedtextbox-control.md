---
title: 'Návod: Práce s ovládacím prvkem MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182061"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Návod: Práce s ovládacím prvkem MaskedTextBox
Mezi úkoly znázorněné v tomto návodu patří:  
  
- Inicializace ovládacího <xref:System.Windows.Forms.MaskedTextBox> prvku  
  
- Použití <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obslužné rutiny události k upozornění uživatele, když znak neodpovídá masce  
  
- Přiřazení typu vlastnosti <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> a použití <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obslužné rutiny události k upozornění uživatele, když hodnota, kterou se pokouší tepotvrzení, není pro daný typ platná.  
  
## <a name="creating-the-project-and-adding-a-control"></a>Vytvoření projektu a přidání ovládacího prvku  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Přidání ovládacího prvku MaskedTextBox do formuláře  
  
1. Otevřete formulář, na který <xref:System.Windows.Forms.MaskedTextBox> chcete ovládací prvek umístit.  
  
2. Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek z **panelu nástrojů** do formuláře.  
  
3. Klepněte pravým tlačítkem myši na ovládací prvek a zvolte **Vlastnosti**. V okně **Vlastnosti** vyberte vlastnost **Maska** a klepněte na tlačítko **...** (tři tečky) vedle názvu vlastnosti.  
  
4. V dialogovém okně **Vstupní maska** vyberte masku **Krátké datum** a klepněte na **OK**.  
  
5. V okně **Vlastnosti** <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> nastavte `true`vlastnost na . Tato vlastnost způsobí, že krátké pípnutí zvuk pokaždé, když se uživatel pokusí zadat znak, který porušuje definici masky.  
  
 Souhrn znaků, které podporuje vlastnost Mask, naleznete v <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> části Poznámky vlastnosti.  
  
## <a name="alert-the-user-to-input-errors"></a>Upozornit uživatele na vstupní chyby  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Přidání tipu pozice pro odmítnutý vstup masky  
  
1. Vraťte se do **panelu nástrojů** a přidejte <xref:System.Windows.Forms.ToolTip> do formuláře.  
  
2. Vytvořte obslužnou rutinu <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> události, která vyvolá při výskytu <xref:System.Windows.Forms.ToolTip> vstupní chyby. Špička pozice zůstane viditelná po dobu pěti sekund nebo dokud na ni uživatel neklikne.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Upozornit uživatele na typ, který není platný  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Přidání tipu pozice pro neplatné datové typy  
  
1. <xref:System.Windows.Forms.Form.Load> V obslužné rutině <xref:System.Type> události formuláře <xref:System.DateTime> přiřaďte objekt představující typ vlastnosti ovládacího <xref:System.Windows.Forms.MaskedTextBox> <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> prvku:  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. Přidejte obslužnou rutinu <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> události pro událost:  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox – ovládací prvek](maskedtextbox-control-windows-forms.md)
