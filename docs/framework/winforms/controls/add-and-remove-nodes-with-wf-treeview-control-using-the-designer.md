---
title: 'Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040076"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="7218b-102">Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7218b-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="7218b-103">Vzhledem k tomu <xref:System.Windows.Forms.TreeView> , že ovládací prvek model Windows Forms zobrazuje uzly hierarchickým způsobem, musíte při přidávání uzlu věnovat pozornost tomu, co je jeho nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="7218b-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="7218b-104">Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.TreeView> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7218b-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="7218b-105">Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7218b-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="7218b-106">Přidání nebo odebrání uzlů v Návrháři</span><span class="sxs-lookup"><span data-stu-id="7218b-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="7218b-107"><xref:System.Windows.Forms.TreeView> Vyberte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7218b-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="7218b-108">V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> .) vedle vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7218b-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="7218b-109">Zobrazí se **Editor TreeNode** .</span><span class="sxs-lookup"><span data-stu-id="7218b-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="7218b-110">Chcete-li přidat uzly, musí existovat kořenový uzel; Pokud neexistuje, musíte nejdřív přidat kořen kliknutím na tlačítko **Přidat root** .</span><span class="sxs-lookup"><span data-stu-id="7218b-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="7218b-111">Potom můžete přidat podřízené uzly tak, že vyberete kořen nebo kterýkoli jiný uzel a kliknete na tlačítko **Přidat podřízenou** položku.</span><span class="sxs-lookup"><span data-stu-id="7218b-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="7218b-112">Chcete-li odstranit uzly, vyberte uzel, který chcete odstranit, a klikněte na tlačítko **Odstranit** .</span><span class="sxs-lookup"><span data-stu-id="7218b-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="7218b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7218b-113">See also</span></span>

- [<span data-ttu-id="7218b-114">Ovládací prvek TreeView</span><span class="sxs-lookup"><span data-stu-id="7218b-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="7218b-115">Přehled ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="7218b-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="7218b-116">Postupy: Nastavení ikon pro ovládací prvek model Windows Forms TreeView</span><span class="sxs-lookup"><span data-stu-id="7218b-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="7218b-117">Postupy: Iterovat všemi uzly model Windows Forms ovládacího prvku TreeView</span><span class="sxs-lookup"><span data-stu-id="7218b-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="7218b-118">Postupy: Zjistit, který uzel TreeView byl kliknuto</span><span class="sxs-lookup"><span data-stu-id="7218b-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="7218b-119">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7218b-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
