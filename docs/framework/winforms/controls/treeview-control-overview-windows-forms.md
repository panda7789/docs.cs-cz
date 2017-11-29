---
title: "TreeView – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TreeView
helpviewer_keywords: TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee285a7db058cd88843eb3addf207fb5c446dfa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView – přehled ovládacího prvku (Windows Forms)
S Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek, můžete zobrazit hierarchii uzlů na uživatele, jako způsob souborů a složek, se zobrazí v levém podokně Průzkumník Windows funkce operačního systému Windows. Každý uzel ve stromovém zobrazení může obsahovat další uzly, nazývá *podřízené uzly*. Můžete zobrazit nadřazených uzlů nebo uzlů, které obsahují podřízené uzly jako rozbalit nebo sbalit. Zobrazení stromu s zaškrtnutí políček vedle uzly můžete také zobrazit nastavením zobrazení stromu <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> vlastnost `true`. Můžete programově poté zaškrtněte nebo zrušte uzly nastavením uzlu <xref:System.Windows.Forms.TreeNode.Checked%2A> vlastnost `true` nebo `false`.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti <xref:System.Windows.Forms.TreeView> řízení, představují <xref:System.Windows.Forms.TreeView.Nodes%2A> a <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Vlastnost obsahuje seznam nejvyšší úrovně uzlů ve stromovém zobrazení. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Vlastnost nastaví aktuálně vybraný uzel. Můžete zobrazit ikonami vedle uzly. Ovládací prvek používá bitové kopie z <xref:System.Windows.Forms.ImageList> s názvem ve stromovém zobrazení <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Vlastnost nastaví výchozí image pro uzly ve stromovém zobrazení. Další informace o zobrazení obrázků najdete v tématu [postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Pokud používáte [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], máte přístup k rozsáhlé knihovně standardní bitové kopie, které můžete použít s <xref:System.Windows.Forms.TreeView> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TreeView>  
 [TreeView – ovládací prvek](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Postupy: Nastavení ikon pro Windows Forms TreeView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Postupy: Přidání a odebrání uzlů pomocí ovládacího prvku Windows Forms TreeView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Postupy: iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Postupy: určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
