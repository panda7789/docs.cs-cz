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
ms.openlocfilehash: 9155893b3d47707e0e55ee33e30d7998654f9e93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965491"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="d75d9-102">Postupy: Vytvoření textu proměnlivé velikosti v ovládacím prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="d75d9-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="d75d9-103">Tento příklad ukazuje vlastní kreslení textu v <xref:System.Windows.Forms.ComboBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d75d9-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="d75d9-104">Pokud položka splňuje určitá kritéria, je vykreslen v větší písma a zapnout červené.</span><span class="sxs-lookup"><span data-stu-id="d75d9-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d75d9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d75d9-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d75d9-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d75d9-106">Compiling the Code</span></span>  
 <span data-ttu-id="d75d9-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d75d9-107">This example requires:</span></span>  
  
- <span data-ttu-id="d75d9-108">Formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="d75d9-108">A Windows form.</span></span>  
  
- <span data-ttu-id="d75d9-109">A <xref:System.Windows.Forms.ComboBox> ovládací prvek s názvem `ListBox1` se tři položky v <xref:System.Windows.Forms.ComboBox.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d75d9-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="d75d9-110">V tomto příkladu jsou tři položky s názvem `"One", Two", and Three"`.</span><span class="sxs-lookup"><span data-stu-id="d75d9-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="d75d9-111"><xref:System.Windows.Forms.ComboBox.DrawMode%2A> Vlastnost `ComboBox1` musí být nastaveno na <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span><span class="sxs-lookup"><span data-stu-id="d75d9-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d75d9-112">Tento postup se vztahuje také na <xref:System.Windows.Forms.ListBox> ovládacího prvku – můžete nahradit <xref:System.Windows.Forms.ListBox> pro <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="d75d9-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
- <span data-ttu-id="d75d9-113">Odkazy <xref:System.Windows.Forms?displayProperty=nameWithType> a <xref:System.Drawing?displayProperty=nameWithType> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d75d9-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75d9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d75d9-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [<span data-ttu-id="d75d9-115">Ovládací prvky s vestavěnou podporou vykreslování vlastníkem</span><span class="sxs-lookup"><span data-stu-id="d75d9-115">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="d75d9-116">Ovládací prvek ListBox</span><span class="sxs-lookup"><span data-stu-id="d75d9-116">ListBox Control</span></span>](listbox-control-windows-forms.md)
- [<span data-ttu-id="d75d9-117">Ovládací prvek ComboBox</span><span class="sxs-lookup"><span data-stu-id="d75d9-117">ComboBox Control</span></span>](combobox-control-windows-forms.md)
