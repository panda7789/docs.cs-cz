---
title: "Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení"
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
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6925e9322063d68d0d7f8c8e048eed254cd14ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení
Tento příklad ukazuje způsob použití <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření zapisovatelné kopie jen pro čtení <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> objektu je označena jako jen pro čtení ("pozastaveny"), nelze jej upravovat. Můžete však použít <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření upravitelnými klon ukotvené objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří upravitelnými klon ukotvené <xref:System.Windows.Media.SolidColorBrush> objektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
