---
title: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 14dc1081a8608c6e6add67f641c4b55825d2fc81
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626968"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="7f46b-102">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7f46b-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="7f46b-103">Když uživatelé budou zobrazovat data zobrazená v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>, někdy chtějí porovnat hodnoty v určitých sloupcích.</span><span class="sxs-lookup"><span data-stu-id="7f46b-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="7f46b-104">To může být nevhodné, pokud jsou sloupce v ovládacím prvku široce oddělené, zejména pokud se uživatelé musí posunout zpátky a vodorovně, aby viděli všechny sloupce, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="7f46b-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="7f46b-105">Úkol porovnání hodnot sloupce můžete usnadnit tím, že uživatelům umožníte změnit pořadí sloupců.</span><span class="sxs-lookup"><span data-stu-id="7f46b-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="7f46b-106">Když povolíte změnu pořadí sloupců, uživatelé můžou přesunout sloupec na novou pozici přetažením záhlaví sloupce myší.</span><span class="sxs-lookup"><span data-stu-id="7f46b-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="7f46b-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="7f46b-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7f46b-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7f46b-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="7f46b-109">Povolení Změna pořadí sloupců</span><span class="sxs-lookup"><span data-stu-id="7f46b-109">To enable column reordering</span></span>

- <span data-ttu-id="7f46b-110">V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Povolit změnu pořadí sloupců**.</span><span class="sxs-lookup"><span data-stu-id="7f46b-110">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f46b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f46b-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7f46b-112">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7f46b-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="7f46b-113">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="7f46b-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="7f46b-114">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f46b-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
