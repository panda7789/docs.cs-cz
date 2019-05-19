---
title: 'Postupy: Přidávání a odebírání položek pomocí ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 37660061140e38661a27f8f750604ae2609ac57c
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882294"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="32044-102">Postupy: Přidávání a odebírání položek pomocí ovládacího prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="32044-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="32044-103">Proces přidání položky do formulářů Windows <xref:System.Windows.Forms.ListView> ovládací prvek sestává především z zadáním položky a přiřazení vlastnosti k němu.</span><span class="sxs-lookup"><span data-stu-id="32044-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="32044-104">Přidávání a odebírání položek seznamu lze provést kdykoli.</span><span class="sxs-lookup"><span data-stu-id="32044-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="32044-105">Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="32044-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="32044-106">Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="32044-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32044-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="32044-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="32044-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="32044-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="32044-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="32044-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="32044-110">Chcete-li přidat nebo odebrat položky pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="32044-110">To add or remove items using the designer</span></span>  
  
1. <span data-ttu-id="32044-111">Vyberte <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="32044-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="32044-112">V **vlastnosti** okna, klikněte na tlačítko **tlačítko se třemi tečkami** (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle <xref:System.Windows.Forms.ListView.Items%2A> vlastnost .</span><span class="sxs-lookup"><span data-stu-id="32044-112">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="32044-113">**Editor kolekce ListViewItem** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="32044-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3. <span data-ttu-id="32044-114">Chcete-li přidat položku, klikněte na tlačítko **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="32044-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="32044-115">Potom můžete nastavit vlastnosti nové položky, jako <xref:System.Windows.Forms.ListView.Text%2A> a <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="32044-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4. <span data-ttu-id="32044-116">Odebrat položku, vyberte ho a klikněte **odebrat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="32044-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32044-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32044-117">See also</span></span>

- [<span data-ttu-id="32044-118">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="32044-118">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="32044-119">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="32044-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="32044-120">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="32044-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="32044-121">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="32044-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="32044-122">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="32044-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="32044-123">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="32044-123">How to: Group Items in a Windows Forms ListView Control</span></span>](how-to-group-items-in-a-windows-forms-listview-control.md)
