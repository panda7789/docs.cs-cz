---
title: Výrazy inicializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 5d6656ab77f7ad0f7366a230d98b95cff5b2677b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854432"
---
# <a name="initialization-expressions"></a>Výrazy inicializace
Inicializační výraz inicializuje nový objekt. Většina inicializačních výrazů je podporovaná, včetně C# většiny nových Visual Basicch inicializačních výrazů 3,0 a 9,0. Následující typy lze inicializovat a vracet LINQ to Entitiesm dotazem:  
  
- Kolekce nula nebo více typových objektů entit nebo projekce komplexních typů, které jsou definovány v koncepčním modelu.  
  
- Typy CLR podporované Entity Framework.
  
- Vložené kolekce.  
  
- Anonymní typy.  
  
 V následujícím příkladu se v syntaxi výrazu dotazu zobrazuje příklad inicializace anonymního typu:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Následující příklad v syntaxi dotazu založeného na metodách ukazuje inicializaci anonymního typu:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Podporuje se i uživatelsky definovaná inicializace třídy. Inicializační C# vzor 3,0 a Visual Basic 9,0 je podporován a předpokládá, že metoda getter a setter vlastnosti je symetrická. Následující příklad v syntaxi výrazu dotazu ukazuje vlastní třídu, která je inicializována v dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 Následující příklad syntaxe dotazu založeného na metodách zobrazuje vlastní třídu, která je inicializována v dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy v dotazech LINQ to Entities](expressions-in-linq-to-entities-queries.md)
