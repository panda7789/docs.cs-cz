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
ms.openlocfilehash: 2853b1e02e1223cbb2b6dff4acbddb0a41d882cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629953"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení
Tento příklad ukazuje způsob použití <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření zapisovatelné kopie jen pro čtení <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> objekt je označena jako jen pro čtení ("zmrazená"), nelze jej upravovat. Můžete však použít <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření upravitelné klony zmrazených objektů.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří upravitelná klon zmrazené <xref:System.Windows.Media.SolidColorBrush> objektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
