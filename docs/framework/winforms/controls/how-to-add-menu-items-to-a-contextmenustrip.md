---
title: 'Postupy: Přidání položek nabídky do ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: 88bf56ea21c4f120b9d745e7f8a31fed485fa192
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506235"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="8df1e-102">Postupy: Přidání položek nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8df1e-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="8df1e-103">Můžete přidat pouze jednu položku nebo více položek najednou <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8df1e-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="8df1e-104">Chcete-li přidat samostatnou položku nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8df1e-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="8df1e-105">Použití <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> způsob, jak přidat jednu položku nabídky <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8df1e-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="8df1e-106">Chcete-li přidat několik položek nabídky do ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8df1e-106">To add several menu items to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="8df1e-107">Použití <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> způsob, jak přidat několik položky nabídky <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8df1e-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8df1e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8df1e-108">See also</span></span>
- [<span data-ttu-id="8df1e-109">Ovládací prvek ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8df1e-109">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
