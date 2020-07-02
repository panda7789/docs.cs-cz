---
title: 'Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel'
description: Naučte se, jak používat dialogové okno Styly sloupců a řádků pro úpravu řádků a sloupců ovládacích prvků model Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619348"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="6e99c-103">Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6e99c-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="6e99c-104">Můžete použít Editor kolekce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku, označovaný jako dialogové okno **styly sloupců a řádků** , chcete-li upravit řádky a sloupce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="6e99c-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="6e99c-105">Chcete-li, aby ovládací prvek zahrnoval více řádků nebo sloupců, nastavte `RowSpan` `ColumnSpan` vlastnosti a na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6e99c-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="6e99c-106">Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="6e99c-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="6e99c-107">Chcete-li zarovnat ovládací prvek v rámci buňky, nebo pokud chcete, aby se ovládací prvek roztáhl v rámci buňky, použijte vlastnost ovládacího prvku <xref:System.Windows.Forms.Control.Anchor%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e99c-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="6e99c-108">Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="6e99c-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="6e99c-109">Úprava řádků a sloupců</span><span class="sxs-lookup"><span data-stu-id="6e99c-109">To edit rows and columns</span></span>

1. <span data-ttu-id="6e99c-110">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="6e99c-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="6e99c-111">Klikněte na <xref:System.Windows.Forms.TableLayoutPanel> glyf akcí ovládacího prvku ( ![ malá černá šipka ](./media/designer-actions-glyph.gif) ) a vyberte **Upravit řádky a sloupce** . otevře se dialogové okno **styly sloupců a řádků** .</span><span class="sxs-lookup"><span data-stu-id="6e99c-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="6e99c-112">Můžete také kliknout pravým tlačítkem myši na <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek a vybrat možnost **Upravit řádky a sloupce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6e99c-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="6e99c-113">Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z rozevíracího seznamu **typ člena** .</span><span class="sxs-lookup"><span data-stu-id="6e99c-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="6e99c-114">Chcete-li přidat nebo odebrat řádky, vyberte **řádky** v rozevíracím seznamu **typ člena** .</span><span class="sxs-lookup"><span data-stu-id="6e99c-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="6e99c-115">Kliknutím na tlačítko **Přidat** přidáte řádek nebo sloupec na konec seznamu **členů** .</span><span class="sxs-lookup"><span data-stu-id="6e99c-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="6e99c-116">Kliknutím na tlačítko **Vložit** přidáte řádek nebo sloupec před aktuálně vybranou položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6e99c-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="6e99c-117">Pokud přidáváte řádek nebo sloupec, vyberte **typ velikosti** pro nový řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="6e99c-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="6e99c-118">Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="6e99c-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="6e99c-119">Chcete-li odebrat řádek nebo sloupec, klikněte na tlačítko **Odebrat** a odstraňte aktuálně vybranou položku v seznamu **členů** .</span><span class="sxs-lookup"><span data-stu-id="6e99c-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e99c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e99c-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="6e99c-121">TableLayoutPanel – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6e99c-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
