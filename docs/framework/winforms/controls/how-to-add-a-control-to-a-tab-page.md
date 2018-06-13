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
# <a name="how-to-add-a-control-to-a-tab-page"></a>Postupy: Přidání ovládacího prvku na stránku záložky
Můžete použít Windows Forms <xref:System.Windows.Forms.TabControl> zobrazíte další ovládací prvky způsobem uspořádány. Následující postup ukazuje, jak přidat tlačítko na první kartě. Informace o přidávání ikonu na popisek část stránky karty najdete v tématu [postupy: Změna vzhledu Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Přidání ovládacího prvku prostřednictvím kódu programu  
  
1.  Použití <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metoda kolekce vrácené <xref:System.Windows.Forms.Control.Controls%2A> vlastnost <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [Přehled ovládacího prvku TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Postupy: Změna vzhledu Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [Postupy: Zákaz karet](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
