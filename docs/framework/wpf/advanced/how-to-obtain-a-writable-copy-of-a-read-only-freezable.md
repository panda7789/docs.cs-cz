---
title: 'Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
