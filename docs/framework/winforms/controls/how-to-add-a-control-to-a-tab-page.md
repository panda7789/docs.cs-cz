---
title: 'Postupy: Přidání ovládacího prvku na stránku záložky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526693"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="f3ed2-102">Postupy: Přidání ovládacího prvku na stránku záložky</span><span class="sxs-lookup"><span data-stu-id="f3ed2-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="f3ed2-103">Můžete použít Windows Forms <xref:System.Windows.Forms.TabControl> zobrazíte další ovládací prvky způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="f3ed2-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="f3ed2-104">Následující postup ukazuje, jak přidat tlačítko na první kartě. Informace o přidávání ikonu na popisek část stránky karty najdete v tématu [postupy: Změna vzhledu Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f3ed2-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="f3ed2-105">Přidání ovládacího prvku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="f3ed2-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="f3ed2-106">Použití <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metoda kolekce vrácené <xref:System.Windows.Forms.Control.Controls%2A> vlastnost <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="f3ed2-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ed2-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3ed2-107">See Also</span></span>  
 [<span data-ttu-id="f3ed2-108">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="f3ed2-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="f3ed2-109">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="f3ed2-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="f3ed2-110">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="f3ed2-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="f3ed2-111">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="f3ed2-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="f3ed2-112">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="f3ed2-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
