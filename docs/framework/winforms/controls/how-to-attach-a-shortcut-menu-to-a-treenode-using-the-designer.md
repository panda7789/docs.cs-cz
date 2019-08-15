---
title: 'Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040450"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Postupy: Připojení místní nabídky k TreeNode pomocí Návrháře
Ovládací prvek <xref:System.Windows.Forms.TreeView> model Windows Forms zobrazí hierarchii uzlů podobný souborům a složkám zobrazeným v levém podokně funkce Průzkumník Windows v operačních systémech Windows. Nastavením <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> vlastnosti můžete uživateli poskytnout operace závislé na <xref:System.Windows.Forms.TreeView> ovládacím prvku, když na něj klikne pravým tlačítkem. Tím, že přidružíte <xref:System.Windows.Forms.ContextMenuStrip> komponentu k jednotlivým <xref:System.Windows.Forms.TreeNode> položkám, můžete přidat přizpůsobenou úroveň funkcí <xref:System.Windows.Forms.TreeView> místní nabídky ovládacím prvkům.

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Přidružení místní nabídky ke prvku TreeNode v době návrhu

1. Přidejte do formuláře <xref:System.Windows.Forms.TreeView> ovládacíprvekapřidejte<xref:System.Windows.Forms.TreeView> uzly podle potřeby. Další informace najdete v tématu [jak: Přidávání a odebírání uzlů s ovládacím prvkem](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)model Windows Forms TreeView

2. <xref:System.Windows.Forms.ContextMenuStrip> Přidejte komponentu do formuláře a pak přidejte položky nabídky do místní nabídky, která představuje operace na úrovni uzlu, které chcete zpřístupnit v době běhu. Další informace najdete v tématu [jak: Přidejte položky nabídky do ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).

3. Znovu otevřete dialogové okno **TreeNodeEditor** pro <xref:System.Windows.Forms.TreeView> ovládací prvek, vyberte uzel, který chcete upravit, a nastavte jeho <xref:System.Windows.Forms.ContextMenuStrip> vlastnost na místní nabídku, kterou jste přidali.

4. Při nastavení této vlastnosti se místní nabídka zobrazí po kliknutí pravým tlačítkem myši na uzel.

     Navíc budete chtít napsat kód pro zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událostí pro tyto položky nabídky.

## <a name="see-also"></a>Viz také:

- [Ovládací prvek TreeView](treeview-control-windows-forms.md)
- [Přehled ovládacího prvku TreeView](treeview-control-overview-windows-forms.md)
- [Ovládací prvek ContextMenuStrip](contextmenustrip-control.md)
