---
title: 'Postupy: Připojení místní nabídky k uzlu TreeView'
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
ms.openlocfilehash: f818cccb3103866af993f1aff527a9c1a7c82109
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294170"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Postupy: Připojení místní nabídky k uzlu TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek zobrazuje hierarchii uzlů, podobně jako u souborů a složek, na které se zobrazí v levém podokně Průzkumníka Windows. Tím, že nastavíte <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastností, můžete zadat kontextové operace uživateli při jejich pravým tlačítkem myši <xref:System.Windows.Forms.TreeView> ovládacího prvku. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> komponenty u jednotlivých <xref:System.Windows.Forms.TreeNode> položky, můžete přidat vlastní úroveň funkce místní nabídku pro váš <xref:System.Windows.Forms.TreeView> ovládacích prvků.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Přidružení místní nabídky k TreeNode prostřednictvím kódu programu  
  
1. Vytvořit instanci <xref:System.Windows.Forms.TreeView> ovládacím prvkem odpovídající nastavení vlastností, vytvoření kořenového <xref:System.Windows.Forms.TreeNode>a pak přidejte podřízené uzly.  
  
2. Vytvořit instanci <xref:System.Windows.Forms.ContextMenuStrip> komponenty a pak přidejte <xref:System.Windows.Forms.ToolStripMenuItem> pro každou operaci, kterou chcete zpřístupnit v době běhu.  
  
3. Nastavte <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> vlastnost odpovídající <xref:System.Windows.Forms.TreeNode> do místní nabídky, které vytvoříte.  
  
4. Pokud je tato vlastnost nastavena, zobrazí se při klepnutí pravým tlačítkem myši na uzel v místní nabídce.  
  
 Následující příklad kódu vytvoří základní <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ContextMenuStrip> přidruženou ke kořenovému adresáři <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>. Budete muset přizpůsobit možnosti nabídek na ty, které odpovídají <xref:System.Windows.Forms.TreeView> vyvíjíte. Kromě toho můžete napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> události pro tyto položky nabídky.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenuStrip>
- [TreeView – ovládací prvek](treeview-control-windows-forms.md)
