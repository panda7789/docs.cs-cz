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
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040076"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Postupy: Přidávání a odebírání uzlů s ovládacím prvkem Windows Forms TreeView pomocí Návrháře

Vzhledem k tomu <xref:System.Windows.Forms.TreeView> , že ovládací prvek model Windows Forms zobrazuje uzly hierarchickým způsobem, musíte při přidávání uzlu věnovat pozornost tomu, co je jeho nadřazený uzel.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.TreeView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Přidání nebo odebrání uzlů v Návrháři

1. <xref:System.Windows.Forms.TreeView> Vyberte ovládací prvek.

2. V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> .) vedle vlastnosti.

     Zobrazí se **Editor TreeNode** .

3. Chcete-li přidat uzly, musí existovat kořenový uzel; Pokud neexistuje, musíte nejdřív přidat kořen kliknutím na tlačítko **Přidat root** . Potom můžete přidat podřízené uzly tak, že vyberete kořen nebo kterýkoli jiný uzel a kliknete na tlačítko **Přidat podřízenou** položku.

4. Chcete-li odstranit uzly, vyberte uzel, který chcete odstranit, a klikněte na tlačítko **Odstranit** .

## <a name="see-also"></a>Viz také:

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek model Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Iterovat všemi uzly model Windows Forms ovládacího prvku TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Zjistit, který uzel TreeView byl kliknuto](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
