---
title: 'Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040350"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="b8ab4-102">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="b8ab4-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="b8ab4-103">Když uživatelé zobrazují data zobrazená v <xref:System.Windows.Forms.DataGridView> ovládacím prvku model Windows Forms, někdy chtějí porovnat hodnoty v určitých sloupcích.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="b8ab4-104">To může být nevhodné, pokud jsou sloupce v ovládacím prvku široce oddělené, zejména pokud se uživatelé musí posunout zpátky a vodorovně, aby viděli všechny sloupce, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="b8ab4-105">Úkol porovnání hodnot sloupce můžete usnadnit tím, že uživatelům umožníte změnit pořadí sloupců.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="b8ab4-106">Když povolíte změnu pořadí sloupců, uživatelé můžou přesunout sloupec na novou pozici přetažením záhlaví sloupce myší.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="b8ab4-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b8ab4-108">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="b8ab4-109">Povolení Změna pořadí sloupců</span><span class="sxs-lookup"><span data-stu-id="b8ab4-109">To enable column reordering</span></span>

- <span data-ttu-id="b8ab4-110">V pravém horním <xref:System.Windows.Forms.DataGridView> rohu ovládacího prvku klikněte na glyf inteligentních značek ((./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")![glyf inteligentních značek]) a pak vyberte **Povolit změnu pořadí sloupců**.</span><span class="sxs-lookup"><span data-stu-id="b8ab4-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8ab4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8ab4-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b8ab4-112">Postupy: Ukotvit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="b8ab4-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="b8ab4-113">Postupy: Vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="b8ab4-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="b8ab4-114">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8ab4-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
