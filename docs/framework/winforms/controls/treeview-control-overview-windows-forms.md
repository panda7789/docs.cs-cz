---
title: TreeView – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 6326f8976e20b5b72e1b6690ab323c8581411156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView – přehled ovládacího prvku (Windows Forms)
S Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek, můžete zobrazit hierarchii uzlů na uživatele, jako způsob souborů a složek, se zobrazí v levém podokně Průzkumník Windows funkce operačního systému Windows. Každý uzel ve stromovém zobrazení může obsahovat další uzly, nazývá *podřízené uzly*. Můžete zobrazit nadřazených uzlů nebo uzlů, které obsahují podřízené uzly jako rozbalit nebo sbalit. Zobrazení stromu s zaškrtnutí políček vedle uzly můžete také zobrazit nastavením zobrazení stromu <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> vlastnost `true`. Můžete programově poté zaškrtněte nebo zrušte uzly nastavením uzlu <xref:System.Windows.Forms.TreeNode.Checked%2A> vlastnost `true` nebo `false`.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti <xref:System.Windows.Forms.TreeView> řízení, představují <xref:System.Windows.Forms.TreeView.Nodes%2A> a <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Vlastnost obsahuje seznam nejvyšší úrovně uzlů ve stromovém zobrazení. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Vlastnost nastaví aktuálně vybraný uzel. Můžete zobrazit ikonami vedle uzly. Ovládací prvek používá bitové kopie z <xref:System.Windows.Forms.ImageList> s názvem ve stromovém zobrazení <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Vlastnost nastaví výchozí image pro uzly ve stromovém zobrazení. Další informace o zobrazení obrázků najdete v tématu [postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít s <xref:System.Windows.Forms.TreeView> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TreeView>  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Postupy: Určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
