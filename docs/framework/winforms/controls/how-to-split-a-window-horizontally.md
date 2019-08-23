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
ms.openlocfilehash: 7ef3fe1210ae42c52a4fd7f23633d6566bc102a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956063"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="ad5bf-102">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="ad5bf-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="ad5bf-103">Následující příklad kódu nastaví rozdělovač, který rozdělí <xref:System.Windows.Forms.SplitContainer> ovládací prvek vodorovně.</span><span class="sxs-lookup"><span data-stu-id="ad5bf-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad5bf-104"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Vlastnost<xref:System.Windows.Forms.SplitContainer> ovládacího prvku určuje směr rozdělovače, nikoli samotného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ad5bf-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="ad5bf-105">Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="ad5bf-105">To split a window horizontally</span></span>  
  
1. <span data-ttu-id="ad5bf-106">V rámci procedury nastavte <xref:System.Windows.Forms.SplitContainer.Orientation%2A> vlastnost <xref:System.Windows.Forms.SplitContainer> ovládacího prvku na <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="ad5bf-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad5bf-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad5bf-107">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="ad5bf-108">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="ad5bf-108">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
