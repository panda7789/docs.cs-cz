---
title: Inicializace výrazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 352bda826c3b872d06252e168abfb1129f178bf8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762205"
---
# <a name="initialization-expressions"></a>Inicializace výrazy
Výraz inicializace inicializuje nový objekt. Většina inicializace výrazy jsou podporovány, včetně většina nových C# 3.0 a Visual Basic 9.0 inicializace výrazů. Následující typy můžete inicializovat a vrácený LINQ entity dotazu:  
  
-   Kolekce nula nebo více objektů zadané entity nebo projekci komplexních typů, které jsou definované v konceptuálním modelu.  
  
-   Typy CLR nepodporuje [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Vložené kolekce.  
  
-   Anonymní typy.  
  
 Inicializace anonymní typ je znázorněno v následujícím příkladu v syntaxe výrazu dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Následující příklad v syntaxi dotazu na základě metod ukazuje inicializace anonymní typ:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Inicializace uživatelsky definované třídy, je také podporována. Inicializace vzor C# 3.0 a Visual Basic 9.0 je podporována a předpokládá, že se symetrické vlastnost getter a setter. Následující příklad v syntaxe výrazu dotazu ukazuje vlastní třídu inicializován v dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 V syntaxi dotazu na základě metod následující příklad ukazuje třídu vlastní inicializaci v dotazu:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
