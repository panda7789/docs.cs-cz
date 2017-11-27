---
title: "Postupy: Nastavení zablokovatelného režimu jen pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a>Postupy: Nastavení zablokovatelného režimu jen pro čtení
Tento příklad ukazuje, jak provádět <xref:System.Windows.Freezable> jen pro čtení voláním jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.  
  
 Nelze ukotvit <xref:System.Windows.Freezable> objektu, pokud je některého z následujících podmínek `true` o objektu:  
  
-   Má animovaný nebo data vázané vlastnosti.  
  
-   Obsahuje vlastnosti, které jsou nastaveny dynamické prostředek. Další informace o dynamické prostředky, najdete v článku [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.  
  
 Pokud tyto podmínky se `false` pro vaše <xref:System.Windows.Freezable> objektu a vy nemáte v úmyslu upravit, zvažte zmrazení mohla získat výhody výkonu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, který je typem <xref:System.Windows.Freezable> objektu.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
