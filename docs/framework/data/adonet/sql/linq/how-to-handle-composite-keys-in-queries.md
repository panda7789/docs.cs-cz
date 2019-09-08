---
title: 'Postupy: Zpracování složených klíčů v dotazech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: a6c6e7d1c1d29a049b50f4ea9d70ef5cd9e89a44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793579"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Postupy: Zpracování složených klíčů v dotazech
Některé operátory můžou mít jenom jeden argument. Pokud argument musí obsahovat více než jeden sloupec z databáze, je nutné vytvořit anonymní typ, který bude představovat kombinaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz, který vyvolá `GroupBy` operátor, který může mít pouze jeden `key` argument.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Stejná situace se týká spojení, jako v následujícím příkladu:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
