---
title: Změna typu sloupce DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 976f257d38dc7be5c904e63da47c61486bd3301c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737129"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="0bfc0-102">Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0bfc0-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="0bfc0-103">Někdy budete chtít změnit typ sloupce, který již byl přidán do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0bfc0-104">Například můžete chtít upravit typy některých sloupců, které jsou generovány automaticky při svázání ovládacího prvku se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="0bfc0-105">To je užitečné v případě, že zobrazená tabulka obsahuje sloupce, které obsahují cizí klíče, do řádků v tabulce v relaci.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="0bfc0-106">V takovém případě možná budete chtít nahradit sloupce textového pole, které zobrazují tyto cizí klíče, sloupci pole se seznamem, které zobrazují smysluplnější hodnoty ze související tabulky.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="0bfc0-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0bfc0-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0bfc0-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="0bfc0-109">Změna typu sloupce pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="0bfc0-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="0bfc0-110">V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="0bfc0-111">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="0bfc0-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="0bfc0-112">V mřížce **vlastnosti sloupce** nastavte vlastnost `ColumnType` na nový typ sloupce.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0bfc0-113">Vlastnost `ColumnType` je vlastnost pouze pro dobu návrhu, která označuje třídu reprezentující typ sloupce.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="0bfc0-114">Nejedná se o skutečnou vlastnost definovanou ve třídě Column.</span><span class="sxs-lookup"><span data-stu-id="0bfc0-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bfc0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bfc0-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="0bfc0-116">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="0bfc0-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="0bfc0-117">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0bfc0-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
