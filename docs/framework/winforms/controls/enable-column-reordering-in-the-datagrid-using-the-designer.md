---
title: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 823c0064b2710ab5dfd0f67edf95374590d4490b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745839"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="394c9-102">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="394c9-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="394c9-103">Když uživatelé budou zobrazovat data zobrazená v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>, někdy chtějí porovnat hodnoty v určitých sloupcích.</span><span class="sxs-lookup"><span data-stu-id="394c9-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="394c9-104">To může být nevhodné, pokud jsou sloupce v ovládacím prvku široce oddělené, zejména pokud se uživatelé musí posunout zpátky a vodorovně, aby viděli všechny sloupce, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="394c9-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="394c9-105">Úkol porovnání hodnot sloupce můžete usnadnit tím, že uživatelům umožníte změnit pořadí sloupců.</span><span class="sxs-lookup"><span data-stu-id="394c9-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="394c9-106">Když povolíte změnu pořadí sloupců, uživatelé můžou přesunout sloupec na novou pozici přetažením záhlaví sloupce myší.</span><span class="sxs-lookup"><span data-stu-id="394c9-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="394c9-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="394c9-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="394c9-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="394c9-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="394c9-109">Povolení Změna pořadí sloupců</span><span class="sxs-lookup"><span data-stu-id="394c9-109">To enable column reordering</span></span>

- <span data-ttu-id="394c9-110">Klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> a pak vyberte **Povolit změnu pořadí sloupců**.</span><span class="sxs-lookup"><span data-stu-id="394c9-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="394c9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="394c9-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="394c9-112">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="394c9-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="394c9-113">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="394c9-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="394c9-114">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="394c9-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
