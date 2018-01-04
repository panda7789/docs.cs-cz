---
title: "Postupy: Přidání ovládacího prvku na stránku záložky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e37a336ece07ae51d45446d5754a52eac113505d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
