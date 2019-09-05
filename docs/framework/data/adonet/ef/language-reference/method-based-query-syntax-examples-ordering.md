---
title: 'Příklady syntaxe dotazů založených na volání metody: Řazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 8da335bc2b45153aa00cd28f1a6baf58d11020ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250111"
---
# <a name="method-based-query-syntax-examples-ordering"></a>Příklady syntaxe dotazů založených na volání metody: Řazení
Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.ThenBy%2A> metodu pro dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazu založeného na metodách. Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Příklad  
 Následující příklad v syntaxi dotazu založeného na metodách <xref:System.Linq.Queryable.OrderBy%2A> používá <xref:System.Linq.Queryable.ThenBy%2A> a vrátí seznam kontaktů seřazené podle příjmení a pak podle křestního jména.  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.OrderBy%2A> metody a <xref:System.Linq.Queryable.ThenByDescending%2A> k prvnímu řazení podle ceníkové ceny a pak provede sestupné řazení názvů produktů.  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
