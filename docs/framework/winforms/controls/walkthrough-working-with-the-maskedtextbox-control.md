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
ms.openlocfilehash: ca505b062be8c60c1dd9b08fead4855eb1eb4cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103841"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Návod: Práce s ovládacím prvkem MaskedTextBox
Úlohy v tomto návodu zahrnují:  
  
-   Inicializuje <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku  
  
-   Použití <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obslužnou rutinu události pro uživatele o upozornění, když znak neodpovídá masce  
  
-   Přiřazení typu k <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost a použití <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obslužnou rutinu události pro uživatele o upozornění, když se pokoušíte potvrzení hodnota není platná pro typ  
  
## <a name="creating-the-project-and-adding-a-control"></a>Vytvoření projektu a přidání ovládacího prvku  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Chcete-li přidat MaskedTextBox – ovládací prvek do formuláře  
  
1.  Otevřete formulář, na kterém chcete umístit <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku.  
  
2.  Přetáhněte <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku **nástrojů** do formuláře.  
  
3.  Klikněte pravým tlačítkem na ovládací prvek a vyberte **vlastnosti**. V **vlastnosti** okna, vyberte **maska** vlastnosti a klikněte na tlačítko **...**  tlačítko (tři tečky) vedle názvu vlastnosti.  
  
4.  V **vstupní maska** dialogové okno, vyberte **krátkého formátu data** masku a klikněte na tlačítko **OK**.  
  
5.  V **vlastnosti** okno sady <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> vlastnost `true`. Tato vlastnost způsobí, že pípnutí krátké zvukové pokaždé, když se uživatel pokusí o vstupní znak, který je v rozporu s definicí masky.  
  
 Přehled znaky, které podporuje vlastnost maska, naleznete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
## <a name="alert-the-user-to-input-errors"></a>Upozornit uživatele k zadání chyby  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Přidat zobrazení tipu v bublině pro vstup odmítnuté masky  
  
1.  Vraťte se na **nástrojů** a přidejte <xref:System.Windows.Forms.ToolTip> do formuláře.  
  
2.  Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> událost, která vyvolá <xref:System.Windows.Forms.ToolTip> , když dojde k chybě vstupu. Zobrazení tipu v bublině zůstává viditelná pro pět sekund, nebo dokud na něj uživatel klikne.  
  
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
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Přidat zobrazení tipu v bublině pro neplatné datové typy  
  
1.  Do formuláře <xref:System.Windows.Forms.Form.Load> obslužná rutina události, přiřadit <xref:System.Type> objekt představující <xref:System.DateTime> typ, který <xref:System.Windows.Forms.MaskedTextBox> ovládacího prvku <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost:  
  
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
  
2.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> události:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MaskedTextBox>
- [Ovládací prvek MaskedTextBox](maskedtextbox-control-windows-forms.md)
