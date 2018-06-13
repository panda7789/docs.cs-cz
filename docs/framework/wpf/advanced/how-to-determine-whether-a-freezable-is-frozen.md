---
title: 'Postupy: Určení, zda je zablokovatelné zablokováno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: f6d20025d59a702357b12da9f5dc0f5887968143
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542750"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Postupy: Určení, zda je zablokovatelné zablokováno
Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Freezable> objekt nereaguje. Pokud se pokusíte změnit ukotvené <xref:System.Windows.Freezable> objektu, vyvolá <xref:System.InvalidOperationException>. Abyste se vyhnuli vyvolání výjimku, použijte <xref:System.Windows.Freezable.IsFrozen%2A> vlastnost <xref:System.Windows.Freezable> objektem pro určení, zda je pozastaveny.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush> a pak ho testů pomocí <xref:System.Windows.Freezable.IsFrozen%2A> vlastnosti k určení, zda je pozastaveny.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
