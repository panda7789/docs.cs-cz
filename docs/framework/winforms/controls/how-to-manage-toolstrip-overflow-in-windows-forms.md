---
title: 'Postupy: Správa přetečení ToolStrip ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 5f26217c92aef1d568349aefb87dd5a882a0cf28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541154"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="a1bc0-102">Postupy: Správa přetečení ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1bc0-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="a1bc0-103">Při všech položek na <xref:System.Windows.Forms.ToolStrip> ovládací prvek se nevejdou do přiděleného prostoru, můžete povolit funkci přetečení na <xref:System.Windows.Forms.ToolStrip> a zjistit, konkrétní chování přetečení <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="a1bc0-104">Po přidání <xref:System.Windows.Forms.ToolStripItem>, které vyžadují více místa, než je přidělený <xref:System.Windows.Forms.ToolStrip> uvedeny formulářovou aktuální velikost, <xref:System.Windows.Forms.ToolStripOverflowButton> automaticky zobrazí na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="a1bc0-105"><xref:System.Windows.Forms.ToolStripOverflowButton> Se zobrazí, a položek s povolenou přetečení přesunou do nabídky přetečení rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="a1bc0-106">Díky tomu můžete k přizpůsobení a stanovení priorit jak vaše <xref:System.Windows.Forms.ToolStrip> položky správně nastavit pro různé velikosti.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="a1bc0-107">Můžete také změnit vzhled vašich položkách při spadají do přetečení s použitím <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="a1bc0-108">Pokud více zvětšit formuláře v době návrhu nebo běhu <xref:System.Windows.Forms.ToolStripItem>s mohou být zobrazeny v hlavním <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripOverflowButton> můžou i zmizet, dokud snížit velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="a1bc0-109">Povolit přetečení v ovládacím prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1bc0-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="a1bc0-110">Ujistěte se, <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="a1bc0-111">Výchozí hodnota je `True`.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="a1bc0-112">Když <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> je `True` (výchozí), <xref:System.Windows.Forms.ToolStripItem> je odeslána do přetečení rozevírací nabídky při obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířka vodorovného <xref:System.Windows.Forms.ToolStrip> nebo výšku a jsou odděleny svislou <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="a1bc0-113">Chcete-li určit chování přetečení konkrétní ovládací prvek ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="a1bc0-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="a1bc0-114">Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="a1bc0-115">Možnosti jsou `Always`, `Never`, a `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="a1bc0-116">Defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="a1bc0-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a1bc0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1bc0-117">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="a1bc0-118">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1bc0-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="a1bc0-119">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1bc0-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [<span data-ttu-id="a1bc0-120">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1bc0-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
