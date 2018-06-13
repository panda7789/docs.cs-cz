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
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534889"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="f9882-102">Postupy: Správa přetečení ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9882-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="f9882-103">Pokud všechny položky v <xref:System.Windows.Forms.ToolStrip> ovládacího prvku nelze uložit do přidělené místo, můžete povolit funkce přetečení na <xref:System.Windows.Forms.ToolStrip> a určují chování přetečení konkrétní <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="f9882-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="f9882-104">Když přidáte <xref:System.Windows.Forms.ToolStripItem>s, která vyžadují víc místa, než je vymezena pro <xref:System.Windows.Forms.ToolStrip> danou aktuální velikost formuláře, <xref:System.Windows.Forms.ToolStripOverflowButton> automaticky se zobrazí na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f9882-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f9882-105"><xref:System.Windows.Forms.ToolStripOverflowButton> Se zobrazí, a položek s povolenou přetečení přesunou do nabídky přetečení rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="f9882-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="f9882-106">To umožňuje přizpůsobit a určit jejich prioritu jak vaše <xref:System.Windows.Forms.ToolStrip> položky správně upravit pro různé typy velikosti.</span><span class="sxs-lookup"><span data-stu-id="f9882-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="f9882-107">Můžete také změnit vzhled položek, jsou-li do oblasti přetečení pomocí <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="f9882-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="f9882-108">V případě více zvětšení formuláře v době návrhu nebo běhu <xref:System.Windows.Forms.ToolStripItem>s lze zobrazit v hlavním <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripOverflowButton> může zmizet i, dokud snížit velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="f9882-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="f9882-109">Chcete-li povolit přetečení na ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f9882-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="f9882-110">Ujistěte se, že <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f9882-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f9882-111">Výchozí hodnota je `True`.</span><span class="sxs-lookup"><span data-stu-id="f9882-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="f9882-112">Při <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> je `True` (výchozí), <xref:System.Windows.Forms.ToolStripItem> je odeslána do nabídky rozevíracího seznamu přetečení při obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířka vodorovného <xref:System.Windows.Forms.ToolStrip> nebo výšky svislého <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f9882-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="f9882-113">K určení chování přetečení konkrétní ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="f9882-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="f9882-114">Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f9882-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="f9882-115">Možnosti jsou `Always`, `Never`, a `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="f9882-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="f9882-116">Defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="f9882-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9882-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9882-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="f9882-118">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f9882-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="f9882-119">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f9882-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="f9882-120">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f9882-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
