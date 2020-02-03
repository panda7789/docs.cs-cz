---
title: 'Postupy: Správa přetečení ToolStrip'
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
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736142"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="1f56a-102">Postupy: Správa přetečení ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f56a-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="1f56a-103">Pokud se všechny položky v ovládacím prvku <xref:System.Windows.Forms.ToolStrip> nevejdou do přiděleného místa, můžete povolit funkci přetečení na <xref:System.Windows.Forms.ToolStrip> a určit chování přetečení u určitých <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="1f56a-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="1f56a-104">Když přidáte <xref:System.Windows.Forms.ToolStripItem>s, které vyžadují více místa, než se přiděluje <xref:System.Windows.Forms.ToolStrip>, která má aktuální velikost formuláře, <xref:System.Windows.Forms.ToolStripOverflowButton> se automaticky zobrazí na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1f56a-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1f56a-105">Zobrazí se <xref:System.Windows.Forms.ToolStripOverflowButton> a položky s povoleným přetečením se přesunou do nabídky přetečení rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="1f56a-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="1f56a-106">Díky tomu můžete přizpůsobit a nastavit prioritu způsobu, jakým se <xref:System.Windows.Forms.ToolStrip> položky správně přizpůsobí různým velikostem formuláře.</span><span class="sxs-lookup"><span data-stu-id="1f56a-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="1f56a-107">Můžete také změnit vzhled položek, když spadají do přetečení pomocí vlastností <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> a události <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>.</span><span class="sxs-lookup"><span data-stu-id="1f56a-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="1f56a-108">Pokud zvětšíte formulář buď v době návrhu, nebo v době běhu, může se v hlavním <xref:System.Windows.Forms.ToolStrip> Zobrazit více <xref:System.Windows.Forms.ToolStripItem>s a <xref:System.Windows.Forms.ToolStripOverflowButton> může dokonce zmizet, dokud nezmenšíte velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="1f56a-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="1f56a-109">Povolení přetečení ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1f56a-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="1f56a-110">Ujistěte se, že vlastnost <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1f56a-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1f56a-111">Výchozí formát je `True`.</span><span class="sxs-lookup"><span data-stu-id="1f56a-111">The default is `True`.</span></span>

     <span data-ttu-id="1f56a-112">Pokud je <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` (výchozí nastavení), do rozevírací nabídky přetečení se pošle <xref:System.Windows.Forms.ToolStripItem>, když obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířku vodorovného <xref:System.Windows.Forms.ToolStrip>u nebo výšku vertikálního <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="1f56a-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="1f56a-113">Určení chování přetečení konkrétního prvku ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="1f56a-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="1f56a-114">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1f56a-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="1f56a-115">Možnosti jsou `Always`, `Never`a `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="1f56a-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="1f56a-116">Výchozí formát je `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="1f56a-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="1f56a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f56a-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="1f56a-118">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1f56a-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="1f56a-119">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1f56a-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="1f56a-120">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="1f56a-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
