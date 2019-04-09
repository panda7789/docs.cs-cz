---
title: 'Postupy: Určení, jestli je zablokovatelné zablokováno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 6a63862d35f2c40289ea6445eb3dab8a2abe4a61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197058"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>Postupy: Určení, jestli je zablokovatelné zablokováno
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
- [– postupy](base-elements-how-to-topics.md)
