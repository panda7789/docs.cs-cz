---
title: 'Postup: Změna mezer a zarovnání položek panelu nástrojů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182233"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="4228c-102">Postupy: Změna mezer a zarovnání položek ToolStrip ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4228c-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="4228c-103">Ovládací <xref:System.Windows.Forms.ToolStrip> prvek plně podporuje funkce rozložení, jako je <xref:System.Windows.Forms.ToolStripItem> například velikost, mezery ovládacích <xref:System.Windows.Forms.ToolStrip>prvků vzhledem k sobě navzájem, uspořádání ovládacích prvků na , a mezery ovládacích prvků vzhledem <xref:System.Windows.Forms.ToolStrip>k .</span><span class="sxs-lookup"><span data-stu-id="4228c-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="4228c-104">Vzhledem k tomu, <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> `true`že výchozí hodnota vlastnosti je <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> , `false`ovládací prvky jsou velikosti automaticky, pokud nenastavíte vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="4228c-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="4228c-105">Ruční velikost položky ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4228c-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="4228c-106">Nastavte <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> vlastnost `false` pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4228c-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="4228c-107">Nastavte <xref:System.Windows.Forms.ToolStripItem.Size%2A> vlastnost požadovaným způsobem pro <xref:System.Windows.Forms.ToolStripItem>přidružené .</span><span class="sxs-lookup"><span data-stu-id="4228c-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="4228c-108">Nastavení mezer položky ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="4228c-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="4228c-109">Vložte požadované hodnoty v obrazových <xref:System.Windows.Forms.ToolStripItem.Margin%2A> bodech do vlastnosti přidruženého ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4228c-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="4228c-110">Hodnoty vlastnosti <xref:System.Windows.Forms.ToolStripItem.Margin%2A> určují mezery mezi položkou a sousedními položkami v tomto pořadí: Vlevo, Nahoře, Vpravo a Dole.</span><span class="sxs-lookup"><span data-stu-id="4228c-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="4228c-111">Zarovnání položky ToolStripItem k pravé straně panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="4228c-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="4228c-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pro přidružený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4228c-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="4228c-113">Ve výchozím <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> nastavení <xref:System.Windows.Forms.ToolStripItemAlignment.Left>je nastavena na , která <xref:System.Windows.Forms.ToolStrip>zarovná ovládací prvky na levou stranu rozhraní .</span><span class="sxs-lookup"><span data-stu-id="4228c-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="4228c-114">Uspořádání položek Panelu nástrojů na panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="4228c-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="4228c-115">Nastavte <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost na požadovanou hodnotu. <xref:System.Windows.Forms.ToolStripLayoutStyle></span><span class="sxs-lookup"><span data-stu-id="4228c-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4228c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4228c-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="4228c-117">ToolStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4228c-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="4228c-118">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4228c-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="4228c-119">Souhrn technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4228c-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
