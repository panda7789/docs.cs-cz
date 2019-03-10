---
title: 'Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 954087fa893baf3aa623c912efb081491304d3fb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719439"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="60498-102">Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60498-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="60498-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvek plně podporuje rozložení funkce jako je například změna velikosti, mezery mezi <xref:System.Windows.Forms.ToolStripItem> řídí relativně vůči sobě navzájem, uspořádání ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>a mezery ovládacích prvků vzhledem k <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="60498-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="60498-104">Protože výchozí hodnotu <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `true`, ovládací prvky se velikost automaticky, pokud nenastavíte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="60498-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="60498-105">Chcete-li ručně změnit velikost prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="60498-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="60498-106">Nastavte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false` pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="60498-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="60498-107">Nastavte <xref:System.Windows.Forms.ToolStripItem.Size%2A> vlastnost tak, jak chcete, aby pro přidružený <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="60498-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="60498-108">Nastavit mezery mezi ovládacího prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="60498-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="60498-109">Vložit do požadované hodnoty v pixelech <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnost přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="60498-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="60498-110">Hodnoty <xref:System.Windows.Forms.ToolStripItem.Margin%2A> vlastnost určovat mezery mezi položkou a sousední položky v tomto pořadí: Vlevo, nahoře, vpravo a dole.</span><span class="sxs-lookup"><span data-stu-id="60498-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="60498-111">Chcete-li zarovnat ToolStripItem na pravé straně ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60498-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="60498-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="60498-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="60498-113">Ve výchozím nastavení <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> je nastavena na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, který odpovídá ovládacích prvků na levé straně <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="60498-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="60498-114">Chcete-li uspořádat ovládací prvek ToolStrip položek na ovládacím prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60498-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="60498-115">Nastavte <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost na hodnotu <xref:System.Windows.Forms.ToolStripLayoutStyle> , který chcete.</span><span class="sxs-lookup"><span data-stu-id="60498-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="60498-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60498-116">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="60498-117">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60498-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="60498-118">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60498-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="60498-119">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60498-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
