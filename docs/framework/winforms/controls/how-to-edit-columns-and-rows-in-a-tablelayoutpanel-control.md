---
title: 'Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040298"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="f7d1c-102">Postupy: Úpravy sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f7d1c-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="f7d1c-103">Můžete použít Editor <xref:System.Windows.Forms.TableLayoutPanel> kolekce ovládacího prvku, označovaný jako dialogové okno **styly sloupců a řádků** , chcete-li upravit řádky a sloupce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="f7d1c-104">Chcete-li, aby ovládací prvek zahrnoval více řádků nebo sloupců, nastavte `RowSpan` vlastnosti `ColumnSpan` a na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="f7d1c-105">Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="f7d1c-106">Chcete-li zarovnat ovládací prvek v rámci buňky, nebo pokud chcete, aby se ovládací prvek roztáhl v rámci buňky, použijte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="f7d1c-107">Další informace najdete v tématu [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="f7d1c-108">Úprava řádků a sloupců</span><span class="sxs-lookup"><span data-stu-id="f7d1c-108">To edit rows and columns</span></span>

1. <span data-ttu-id="f7d1c-109">Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="f7d1c-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="f7d1c-110">![](./media/vs-winformsmttagglyph.gif "") <xref:System.Windows.Forms.TableLayoutPanel> Klikněte na glyf inteligentních značek ovládacího prvku (VS_WinFormSmtTagGlyph glyf inteligentních značek) a vyberte **Upravit řádky a sloupce** . otevře se dialogové okno Styly sloupců a řádků.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="f7d1c-111">Můžete také kliknout <xref:System.Windows.Forms.TableLayoutPanel> pravým tlačítkem myši na ovládací prvek a vybrat možnost **Upravit řádky a sloupce** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="f7d1c-112">Chcete-li přidat nebo odebrat sloupce, vyberte **sloupce** z rozevíracího seznamu **typ člena** .</span><span class="sxs-lookup"><span data-stu-id="f7d1c-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="f7d1c-113">Chcete-li přidat nebo odebrat řádky, vyberte **řádky** v rozevíracím seznamu **typ člena** .</span><span class="sxs-lookup"><span data-stu-id="f7d1c-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="f7d1c-114">Kliknutím na tlačítko **Přidat** přidáte řádek nebo sloupec na konec seznamu **členů** .</span><span class="sxs-lookup"><span data-stu-id="f7d1c-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="f7d1c-115">Kliknutím na tlačítko **Vložit** přidáte řádek nebo sloupec před aktuálně vybranou položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="f7d1c-116">Pokud přidáváte řádek nebo sloupec, vyberte **typ velikosti** pro nový řádek nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="f7d1c-117">Další informace naleznete v tématu <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="f7d1c-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="f7d1c-118">Chcete-li odebrat řádek nebo sloupec, klikněte na tlačítko **Odebrat** a odstraňte aktuálně vybranou položku v seznamu **členů** .</span><span class="sxs-lookup"><span data-stu-id="f7d1c-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7d1c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7d1c-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="f7d1c-120">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f7d1c-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
