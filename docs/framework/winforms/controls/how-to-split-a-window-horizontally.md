---
title: 'Postupy: Vodorovné rozdělení okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: 1e097ce5623fab4c3c8c1d59d9bc8c9206abee2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533124"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="feec8-102">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="feec8-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="feec8-103">Následující příklad kódu vytvoří rozdělovače, která rozdělí <xref:System.Windows.Forms.SplitContainer> vodorovných ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="feec8-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feec8-104"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost <xref:System.Windows.Forms.SplitContainer> řízení Určuje směr, rozdělovače, není z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="feec8-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="feec8-105">Chcete-li vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="feec8-105">To split a window horizontally</span></span>  
  
1.  <span data-ttu-id="feec8-106">V rámci procedury, nastavte <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost <xref:System.Windows.Forms.SplitContainer> řídit k <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="feec8-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="feec8-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="feec8-107">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="feec8-108">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="feec8-108">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
