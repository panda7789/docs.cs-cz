---
title: "Postupy: Nastavení zablokovatelného režimu jen pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa6d3f7109e8258dff0a07556bc8572f6071c961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
