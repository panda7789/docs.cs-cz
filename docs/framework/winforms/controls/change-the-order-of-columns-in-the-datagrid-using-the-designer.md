---
title: Změna pořadí sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628745"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="f3199-102">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f3199-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="f3199-103">Když svážete ovládací prvek <xref:System.Windows.Forms.DataGridView> model Windows Forms ke zdroji dat, je pořadí zobrazení automaticky generovaných sloupců řízeno zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="f3199-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="f3199-104">Pokud toto pořadí nevyhovuje vašim požadavkům, můžete změnit pořadí sloupců pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="f3199-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="f3199-105">Do ovládacího prvku můžete také přidat nevázané sloupce a změnit jejich pořadí zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f3199-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="f3199-106">Informace o tom, jak změnit pořadí sloupců pomocí kódu programu, naleznete v tématu [How to: Change pořadí sloupců v ovládacím prvku DataGridView model Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3199-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="f3199-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f3199-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="f3199-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f3199-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="f3199-109">Změna pořadí sloupců pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="f3199-109">To change the column order using the designer</span></span>

1. <span data-ttu-id="f3199-110">V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Upravit sloupce**.</span><span class="sxs-lookup"><span data-stu-id="f3199-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="f3199-111">Vyberte sloupec ze seznamu **vybrané sloupce** .</span><span class="sxs-lookup"><span data-stu-id="f3199-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="f3199-112">Klikněte na šipku nahoru nebo dolů napravo od seznamu **vybrané sloupce** , dokud není vybraný sloupec v požadované pozici.</span><span class="sxs-lookup"><span data-stu-id="f3199-112">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3199-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3199-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="f3199-114">Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f3199-114">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="f3199-115">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="f3199-115">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="f3199-116">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3199-116">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
