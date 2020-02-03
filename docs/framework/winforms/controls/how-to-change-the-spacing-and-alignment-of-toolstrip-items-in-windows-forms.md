---
title: 'Postupy: Změna mezer a zarovnání položek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746561"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="74d4c-102">Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74d4c-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="74d4c-103">Ovládací prvek <xref:System.Windows.Forms.ToolStrip> plně podporuje funkce rozložení, jako je například velikost, rozestup <xref:System.Windows.Forms.ToolStripItem>ch ovládacích prvků, které jsou vzájemně relativní, uspořádání ovládacích prvků na <xref:System.Windows.Forms.ToolStrip>a mezery mezi ovládacími prvky relativními k <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="74d4c-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="74d4c-104">Vzhledem k tomu, že je výchozí hodnota vlastnosti <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> `true`, mají ovládací prvky velikost automaticky, pokud nenastavíte vlastnost <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="74d4c-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="74d4c-105">Ruční změna velikosti prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="74d4c-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="74d4c-106">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false` pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74d4c-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="74d4c-107">Vlastnost <xref:System.Windows.Forms.ToolStripItem.Size%2A> nastavte tak, jak chcete pro související <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="74d4c-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="74d4c-108">Nastavení mezer ovládacího prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="74d4c-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="74d4c-109">Vložte požadované hodnoty (v pixelech) do vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> přidruženého ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="74d4c-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="74d4c-110">Hodnoty vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> určují mezery mezi položkou a sousedními položkami v tomto pořadí: vlevo, nahoře, vpravo a dole.</span><span class="sxs-lookup"><span data-stu-id="74d4c-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="74d4c-111">Zarovnání prvku ToolStripItem na pravou stranu ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="74d4c-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="74d4c-112">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> na <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74d4c-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="74d4c-113">Ve výchozím nastavení je <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> nastavena na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, která zarovnává ovládací prvky na levou stranu <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="74d4c-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="74d4c-114">Uspořádání položek ToolStrip na ovládacím prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="74d4c-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="74d4c-115">Vlastnost <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> nastavte na hodnotu <xref:System.Windows.Forms.ToolStripLayoutStyle>, kterou požadujete.</span><span class="sxs-lookup"><span data-stu-id="74d4c-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74d4c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="74d4c-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="74d4c-117">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="74d4c-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="74d4c-118">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="74d4c-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="74d4c-119">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="74d4c-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
