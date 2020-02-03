---
title: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cc9aff0f15d1bd6de5c469ee7069a99f3360837a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728705"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="24a8c-102">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="24a8c-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="24a8c-103">Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo odstranění existujících řádků v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="24a8c-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="24a8c-104">Nové řádky jsou zadány do speciálního řádku pro nové záznamy v dolní části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="24a8c-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="24a8c-105">Když zaškrtnete přidávání řádků, řádek pro nové záznamy se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="24a8c-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="24a8c-106">Ovládací prvek lze následně nastavit jen pro čtení zakázáním odstranění řádků a úprav buňky.</span><span class="sxs-lookup"><span data-stu-id="24a8c-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="24a8c-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="24a8c-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="24a8c-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="24a8c-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="24a8c-109">Prevence přidávání a odstraňování řádků</span><span class="sxs-lookup"><span data-stu-id="24a8c-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="24a8c-110">V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a zrušte zaškrtnutí políčka **Povolit přidávání** a **povolování odstraňování** .</span><span class="sxs-lookup"><span data-stu-id="24a8c-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24a8c-111">Chcete-li nastavit, aby byl ovládací prvek úplně jen pro čtení, zrušte zaškrtnutí políčka **Povolit úpravy** .</span><span class="sxs-lookup"><span data-stu-id="24a8c-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="24a8c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="24a8c-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="24a8c-113">Postupy: vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="24a8c-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="24a8c-114">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24a8c-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
