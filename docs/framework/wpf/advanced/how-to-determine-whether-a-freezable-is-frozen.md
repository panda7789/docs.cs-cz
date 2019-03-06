---
title: 'Postupy: Určení, zda je zablokovatelné zablokováno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362510"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Postupy: Určení, zda je zablokovatelné zablokováno
Tento příklad ukazuje, jak určit, jestli <xref:System.Windows.Freezable> objektu je zmrazen. Pokud se pokusíte změnit zmrazený <xref:System.Windows.Freezable> objektu, vyvolá <xref:System.InvalidOperationException>. Abyste se vyhnuli vyvolání této výjimky, použijte <xref:System.Windows.Freezable.IsFrozen%2A> vlastnost <xref:System.Windows.Freezable> objektem pro určení, zda je zmrazen.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush> a poté jej ověří pomocí <xref:System.Windows.Freezable.IsFrozen%2A> a určí, zda je zmrazen.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [Přehled zablokovatelných objektů](freezable-objects-overview.md)
- [Témata s postupy](base-elements-how-to-topics.md)
