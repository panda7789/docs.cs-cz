---
title: Přidání sloupců do ovládacího prvku ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744604"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="68619-102">Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="68619-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="68619-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> může zobrazit více sloupců pro každou položku seznamu, pokud je v zobrazení **podrobností** .</span><span class="sxs-lookup"><span data-stu-id="68619-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="68619-104">Sloupce můžete použít k zobrazení několika typů informací o každé položce seznamu.</span><span class="sxs-lookup"><span data-stu-id="68619-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="68619-105">Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru.</span><span class="sxs-lookup"><span data-stu-id="68619-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="68619-106">Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="68619-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="68619-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="68619-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="68619-108">Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="68619-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="68619-109">Přidání sloupců v Návrháři</span><span class="sxs-lookup"><span data-stu-id="68619-109">To add columns in the designer</span></span>

1. <span data-ttu-id="68619-110">V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.ListView.View%2A> ovládacího prvku na hodnotu <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="68619-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="68619-111">V okně **vlastnosti** klikněte na tlačítko se **třemi tečkami** (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="68619-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="68619-112">Zobrazí se **Editor kolekce ColumnHeader** .</span><span class="sxs-lookup"><span data-stu-id="68619-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="68619-113">Pomocí tlačítka **Přidat** přidejte nové sloupce.</span><span class="sxs-lookup"><span data-stu-id="68619-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="68619-114">Pak můžete vybrat záhlaví sloupce a nastavit jeho text (titulek sloupce), zarovnání textu a šířku.</span><span class="sxs-lookup"><span data-stu-id="68619-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="68619-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="68619-115">See also</span></span>

- [<span data-ttu-id="68619-116">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="68619-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="68619-117">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="68619-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="68619-118">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="68619-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="68619-119">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="68619-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="68619-120">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="68619-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
