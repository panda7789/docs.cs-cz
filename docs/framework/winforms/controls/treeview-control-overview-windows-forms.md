---
title: Přehled ovládacího prvku TreeView
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 44b5e27273d122f38ea00e009302d427305977a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743219"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView – přehled ovládacího prvku (Windows Forms)

Pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.TreeView> můžete zobrazit hierarchii uzlů uživatelům, jako je například způsob zobrazení souborů a složek v levém podokně funkce Windows Explorer v operačním systému Windows. Každý uzel ve stromovém zobrazení může obsahovat další uzly označované jako *podřízené uzly*. Můžete zobrazit nadřazené uzly nebo uzly, které obsahují podřízené uzly, jako rozbalené nebo sbalené. Stromové zobrazení můžete zobrazit také zaškrtnutím políčka vedle uzlů nastavením vlastnosti <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> stromového zobrazení na hodnotu `true`. Pak můžete programově vybrat nebo vymazat uzly nastavením vlastnosti <xref:System.Windows.Forms.TreeNode.Checked%2A> uzlu na `true` nebo `false`.

## <a name="key-properties"></a>Klíčové vlastnosti

Klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.TreeView> jsou <xref:System.Windows.Forms.TreeView.Nodes%2A> a <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. Vlastnost <xref:System.Windows.Forms.TreeView.Nodes%2A> obsahuje seznam uzlů nejvyšší úrovně ve stromovém zobrazení. Vlastnost <xref:System.Windows.Forms.TreeView.SelectedNode%2A> nastaví aktuálně vybraný uzel. Vedle uzlů lze zobrazit ikony. Ovládací prvek používá obrázky z <xref:System.Windows.Forms.ImageList> pojmenované ve vlastnosti <xref:System.Windows.Forms.TreeView.ImageList%2A> stromového zobrazení. Vlastnost <xref:System.Windows.Forms.TreeView.ImageIndex%2A> nastaví výchozí obrázek pro uzly ve stromovém zobrazení. Další informace o zobrazení obrázků najdete v tématu [Postup: nastavení ikon pro ovládací prvek model Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md). Pokud používáte sadu Visual Studio 2005, máte přístup k velké knihovně standardních imagí, které lze použít s ovládacím prvkem <xref:System.Windows.Forms.TreeView>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TreeView>
- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Postupy: Určení uzlu TreeView označeného kliknutím](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
