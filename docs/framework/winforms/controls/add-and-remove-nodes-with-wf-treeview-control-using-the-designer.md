---
title: Přidání a odebrání uzlů pomocí ovládacího prvku TreeView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732249"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře

Vzhledem k tomu, že ovládací prvek model Windows Forms <xref:System.Windows.Forms.TreeView> zobrazuje uzly hierarchickým způsobem, je nutné při přidávání uzlu věnovat pozornost tomu, co je jeho nadřazený uzel.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.TreeView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Přidání nebo odebrání uzlů v Návrháři

1. Vyberte ovládací prvek <xref:System.Windows.Forms.TreeView>.

2. V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.TreeView.Nodes%2A>.

     Zobrazí se **Editor TreeNode** .

3. Chcete-li přidat uzly, musí existovat kořenový uzel; Pokud neexistuje, musíte nejdřív přidat kořen kliknutím na tlačítko **Přidat root** . Potom můžete přidat podřízené uzly tak, že vyberete kořen nebo kterýkoli jiný uzel a kliknete na tlačítko **Přidat podřízenou** položku.

4. Chcete-li odstranit uzly, vyberte uzel, který chcete odstranit, a klikněte na tlačítko **Odstranit** .

## <a name="see-also"></a>Viz také

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
