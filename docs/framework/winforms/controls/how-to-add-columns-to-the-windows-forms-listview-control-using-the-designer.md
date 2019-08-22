---
title: 'Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 10963fcb6d87ed74f73ecf4f1831a56eae5a392d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658460"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="75747-102">Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="75747-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>

<span data-ttu-id="75747-103">Ovládací prvek <xref:System.Windows.Forms.ListView> model Windows Forms může zobrazit více sloupců pro každou položku seznamu, pokud je v zobrazení **podrobností** .</span><span class="sxs-lookup"><span data-stu-id="75747-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="75747-104">Sloupce můžete použít k zobrazení několika typů informací o každé položce seznamu.</span><span class="sxs-lookup"><span data-stu-id="75747-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="75747-105">Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru.</span><span class="sxs-lookup"><span data-stu-id="75747-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="75747-106">Informace o naplnění sloupců po jejich vytvoření najdete v tématu [How to: Zobrazí podpoložky ve sloupcích s ovládacím prvkem](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)model Windows Forms ListView.</span><span class="sxs-lookup"><span data-stu-id="75747-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>

<span data-ttu-id="75747-107">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="75747-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="75747-108">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75747-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="75747-109">Přidání sloupců v Návrháři</span><span class="sxs-lookup"><span data-stu-id="75747-109">To add columns in the designer</span></span>

1. <span data-ttu-id="75747-110">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost ovládacího prvku na <xref:System.Windows.Forms.View.Details>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="75747-110">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

2. <span data-ttu-id="75747-111">V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> Studio.) vedle vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75747-111">In the **Properties** window, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>

     <span data-ttu-id="75747-112">Zobrazí se **Editor kolekce ColumnHeader** .</span><span class="sxs-lookup"><span data-stu-id="75747-112">The **ColumnHeader Collection Editor** appears.</span></span>

3. <span data-ttu-id="75747-113">Pomocí tlačítka **Přidat** přidejte nové sloupce.</span><span class="sxs-lookup"><span data-stu-id="75747-113">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="75747-114">Pak můžete vybrat záhlaví sloupce a nastavit jeho text (titulek sloupce), zarovnání textu a šířku.</span><span class="sxs-lookup"><span data-stu-id="75747-114">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>

## <a name="see-also"></a><span data-ttu-id="75747-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75747-115">See also</span></span>

- [<span data-ttu-id="75747-116">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="75747-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="75747-117">Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="75747-117">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="75747-118">Postupy: Zobrazit podpoložky ve sloupcích s ovládacím prvkem model Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="75747-118">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="75747-119">Postupy: Zobrazit ikony pro ovládací prvek model Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="75747-119">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="75747-120">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="75747-120">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
