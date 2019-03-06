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
ms.openlocfilehash: 08b7007911d15019c043a74e093ccc0fba072fd1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361613"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>Postupy: Získání zapisovatelné kopie zablokovatelného objektu jen pro čtení
Tento příklad ukazuje způsob použití <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření zapisovatelné kopie jen pro čtení <xref:System.Windows.Freezable>.  
  
 Po <xref:System.Windows.Freezable> objekt je označena jako jen pro čtení ("zmrazená"), nelze jej upravovat. Můžete však použít <xref:System.Windows.Freezable.Clone%2A> metodu pro vytvoření upravitelné klony zmrazených objektů.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří upravitelná klon zmrazené <xref:System.Windows.Media.SolidColorBrush> objektu.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [Témata s postupy](base-elements-how-to-topics.md)
