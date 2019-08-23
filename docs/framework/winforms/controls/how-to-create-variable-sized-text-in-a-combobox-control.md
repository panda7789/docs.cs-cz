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
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914751"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox
Tento příklad ukazuje vlastní vykreslování textu v <xref:System.Windows.Forms.ComboBox> ovládacím prvku. Pokud položka splňuje určitá kritéria, je vykreslena větším písmem a červeně.  
  
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
  
- Formulář Windows  
  
- Ovládací prvek s `ListBox1` názvem<xref:System.Windows.Forms.ComboBox.Items%2A> se třemi položkami ve vlastnosti. <xref:System.Windows.Forms.ComboBox> V tomto příkladu jsou tři položky pojmenovány `"One", Two", and Three"`. Vlastnost třídy `ComboBox1` musí být nastavena na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>hodnotu. <xref:System.Windows.Forms.ComboBox.DrawMode%2A>  
  
    > [!NOTE]
    > Tato technika je také platná <xref:System.Windows.Forms.ListBox> pro ovládací prvek – můžete <xref:System.Windows.Forms.ListBox> použít pro <xref:System.Windows.Forms.ComboBox>.  
  
- Odkazy na <xref:System.Windows.Forms?displayProperty=nameWithType> obory <xref:System.Drawing?displayProperty=nameWithType> názvů a.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [Ovládací prvky s vestavěnou podporou vykreslování vlastníkem](controls-with-built-in-owner-drawing-support.md)
- [Ovládací prvek ListBox](listbox-control-windows-forms.md)
- [Ovládací prvek ComboBox](combobox-control-windows-forms.md)
