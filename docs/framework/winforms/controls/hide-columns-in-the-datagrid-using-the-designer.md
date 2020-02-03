---
title: Skrýt sloupce v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738651"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="50fad-102">Postupy: Skrývání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="50fad-102">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="50fad-103">Někdy budete chtít zobrazit pouze některé sloupce, které jsou k dispozici v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="50fad-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="50fad-104">Například můžete chtít zobrazit mzdový sloupec zaměstnanců uživatelům s přihlašovacími údaji pro správu při jejich skrývání od jiných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="50fad-104">For example, you may want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="50fad-105">Alternativně můžete chtít navazovat ovládací prvek na zdroj dat, který obsahuje mnoho sloupců, pouze některé z nich chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="50fad-105">Alternately, you may want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="50fad-106">V takovém případě obvykle odeberete sloupce, které nemají zájem o zobrazení, a ne jejich skrytí.</span><span class="sxs-lookup"><span data-stu-id="50fad-106">In this case, you will typically remove the columns you are not interested in displaying rather than hiding them.</span></span> <span data-ttu-id="50fad-107">Další informace naleznete v tématu [Postup: Přidání a odebrání sloupců v ovládacím prvku model Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="50fad-107">For more information, see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>

 <span data-ttu-id="50fad-108">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="50fad-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="50fad-109">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="50fad-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-hide-a-column-using-the-designer"></a><span data-ttu-id="50fad-110">Skrytí sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="50fad-110">To hide a column using the designer</span></span>

1. <span data-ttu-id="50fad-111">V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="50fad-111">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="50fad-112">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="50fad-112">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="50fad-113">V mřížce **vlastnosti sloupce** nastavte vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="50fad-113">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property to `false`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="50fad-114">Sloupec můžete také při přidávání skrýt tak, že zrušíte zaškrtnutí políčka **viditelné** v dialogovém okně **Přidat sloupec** .</span><span class="sxs-lookup"><span data-stu-id="50fad-114">You can also hide a column when adding it by clearing the **Visible** check box in the **Add Column** dialog box.</span></span>

## <a name="see-also"></a><span data-ttu-id="50fad-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="50fad-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="50fad-116">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="50fad-116">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="50fad-117">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="50fad-117">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="50fad-118">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50fad-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
