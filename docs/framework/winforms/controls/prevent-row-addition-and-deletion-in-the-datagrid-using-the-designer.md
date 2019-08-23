---
title: 'Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: f47eb29bf9ae077555f352d10c667bac4ade9373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968326"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="1ac3f-102">Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="1ac3f-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="1ac3f-103">Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo při odstraňování stávajících řádků v <xref:System.Windows.Forms.DataGridView> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1ac3f-104">Nové řádky jsou zadány do speciálního řádku pro nové záznamy v dolní části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-104">New rows are entered in the special row for new records at the bottom of the control.</span></span> <span data-ttu-id="1ac3f-105">Když zaškrtnete přidávání řádků, řádek pro nové záznamy se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-105">When you disable row addition, the row for new records is not displayed.</span></span> <span data-ttu-id="1ac3f-106">Ovládací prvek lze následně nastavit jen pro čtení zakázáním odstranění řádků a úprav buňky.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-106">You can then make the control entirely read-only by disabling row deletion and cell editing.</span></span>

 <span data-ttu-id="1ac3f-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1ac3f-108">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1ac3f-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-prevent-row-addition-and-deletion"></a><span data-ttu-id="1ac3f-109">Prevence přidávání a odstraňování řádků</span><span class="sxs-lookup"><span data-stu-id="1ac3f-109">To prevent row addition and deletion</span></span>

- <span data-ttu-id="1ac3f-110">V <xref:System.Windows.Forms.DataGridView> pravém horním rohu ovládacího prvku klikněte na glyf inteligentních značek ((./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")![glyf inteligentních značek]) a zrušte zaškrtnutí políčka **Povolit přidávání** a **povolování odstraňování** .</span><span class="sxs-lookup"><span data-stu-id="1ac3f-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then clear the **Enable Adding** and **Enable Deleting** check boxes.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1ac3f-111">Chcete-li nastavit, aby byl ovládací prvek úplně jen pro čtení, zrušte zaškrtnutí políčka **Povolit úpravy** .</span><span class="sxs-lookup"><span data-stu-id="1ac3f-111">To make the control entirely read-only, clear the **Enable Editing** check box as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ac3f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ac3f-112">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1ac3f-113">Postupy: Vytvoření projektu model Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="1ac3f-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="1ac3f-114">Postupy: Přidat ovládací prvky do model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ac3f-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
