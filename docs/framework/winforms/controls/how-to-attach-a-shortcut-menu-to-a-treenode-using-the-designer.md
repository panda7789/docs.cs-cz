---
title: 'Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 2700be06ceb4c20926d6af9c962799db4afc31da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.TreeView> zobrazí hierarchie uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně funkci Průzkumníka Windows v operačních systémech Windows. Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost, můžete zadat kontextové operace uživateli při jejich klikněte pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> součást s jednotlivé <xref:System.Windows.Forms.TreeNode> položek, můžete přidat vlastní úroveň funkce místní nabídky k vaší <xref:System.Windows.Forms.TreeView> ovládací prvky.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Přidružení místní nabídky k TreeNode v době návrhu  
  
1.  Přidat <xref:System.Windows.Forms.TreeView> řízení do svého formuláře a potom přidat uzly do <xref:System.Windows.Forms.TreeView> podle potřeby. Další informace najdete v tématu [postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Přidat <xref:System.Windows.Forms.ContextMenuStrip> součásti do svého formuláře a pak přidejte položky nabídky do místní nabídky, která představují úrovni uzlu operace, které chcete zpřístupnit v době běhu. Další informace najdete v tématu [postupy: přidání položek nabídky do ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Otevřete **TreeNodeEditor** dialogové okno pro <xref:System.Windows.Forms.TreeView> řídit, vyberte uzel pro úpravy a nastavit jeho <xref:System.Windows.Forms.ContextMenuStrip> vlastnost, která má místní nabídky, která jste přidali.  
  
4.  Když je tato vlastnost nastavena, zobrazí se při kliknete pravým tlačítkem na uzel v místní nabídce.  
  
     Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Přehled ovládacího prvku TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Ovládací prvek ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
