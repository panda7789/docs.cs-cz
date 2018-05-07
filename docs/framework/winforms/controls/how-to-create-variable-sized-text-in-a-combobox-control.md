---
title: 'Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: a76e1d78cd9fade550fa846488e8bf4a93a21c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox
Tento příklad ukazuje vlastní kreslení textu v <xref:System.Windows.Forms.ComboBox> ovládacího prvku. Pokud položku splňuje určitá kritéria, je vykreslen větší písmeny a zapnuté red.  
  
## <a name="example"></a>Příklad  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Formuláře systému Windows.  
  
-   A <xref:System.Windows.Forms.ComboBox> ovládací prvek s názvem `ListBox1` s tři položky v <xref:System.Windows.Forms.ComboBox.Items%2A> vlastnost. V tomto příkladu jsou tři položky s názvem `"One", Two", and Three"`. <xref:System.Windows.Forms.ComboBox.DrawMode%2A> Vlastnost `ComboBox1` musí být nastavena na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.  
  
    > [!NOTE]
    >  Tento postup lze také použít <xref:System.Windows.Forms.ListBox> ovládací prvek – můžete nahradit <xref:System.Windows.Forms.ListBox> pro <xref:System.Windows.Forms.ComboBox>.  
  
-   Odkazuje na <xref:System.Windows.Forms?displayProperty=nameWithType> a <xref:System.Drawing?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [Ovládací prvky s vestavěnou podporou vykreslování vlastníkem](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [Ovládací prvek ListBox](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [Ovládací prvek ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
