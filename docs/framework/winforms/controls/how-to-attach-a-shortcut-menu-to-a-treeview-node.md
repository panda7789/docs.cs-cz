---
title: 'Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 737e74184b0763ed84b4e585f2508d69944d0e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Postupy: Připojení místní nabídky (ShortCut Menu) k uzlu TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> zobrazí hierarchie uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně Průzkumníka Windows. Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnost, můžete zadat kontextové operace uživateli při jejich klikněte pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> součást s jednotlivé <xref:System.Windows.Forms.TreeNode> položek, můžete přidat vlastní úroveň funkce místní nabídky k vaší <xref:System.Windows.Forms.TreeView> ovládací prvky.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Přidružení místní nabídky k TreeNode prostřednictvím kódu programu  
  
1.  Vytváření instancí <xref:System.Windows.Forms.TreeView> řízení s odpovídající nastavení vlastností, vytvořte kořenové <xref:System.Windows.Forms.TreeNode>a poté přidejte podřízených uzlů.  
  
2.  Vytváření instancí <xref:System.Windows.Forms.ContextMenuStrip> součást a poté přidejte <xref:System.Windows.Forms.ToolStripMenuItem> pro každou operaci, kterou chcete zpřístupnit v době běhu.  
  
3.  Nastavte <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> vlastnost odpovídající <xref:System.Windows.Forms.TreeNode> do místní nabídky, které vytvoříte.  
  
4.  Když je tato vlastnost nastavena, zobrazí se při kliknete pravým tlačítkem na uzel v místní nabídce.  
  
 Následující příklad kódu vytvoří základní <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ContextMenuStrip> přidruženou ke kořenovému adresáři <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>. Budete muset přizpůsobit možnosti nabídky na ty, které nevejde <xref:System.Windows.Forms.TreeView> vyvíjíte. Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [Ovládací prvek TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
