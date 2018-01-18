---
title: "Formulovali spojení a dotazy smíšený produkt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formulovali spojení a dotazy smíšený produkt
Následující příklady ukazují, jak kombinují výsledky z více tabulek.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `From` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzule v jazyce C#) a vyberte všechny objednávky zákazníků v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `Where` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` klauzule v jazyce C#) Chcete-li filtrovat na více systémů stock `Products` jehož `Supplier` je ve Spojených státech amerických.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `From` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzule v jazyce C#) k filtrování pro zaměstnance v Praze tak, aby jejich teritoria.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá cizího klíče navigace ve `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) Chcete-li filtrovat páry zaměstnanců, kde jeden zaměstnanec sestavy na druhý a kde jsou obě zaměstnanci ze stejné `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] příkladu vypadá pro všechny zákazníky a objednávky, zajišťuje, že budou odpovídat objednávky zákazníků a zaručuje, že pro každý zákazník v tomto seznamu, jméno kontaktní osoby je k dispozici.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně spojení dvou tabulek a projekty výsledky z obou tabulek.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Příklad  
 Následující příklad explicitně spojí tři tabulky a projekty výsledky z každého z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak dosáhnout `LEFT OUTER JOIN` pomocí `DefaultIfEmpty()`. `DefaultIfEmpty()` Metoda vrátí hodnotu null, pokud není žádná `Order` pro `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Příklad  
 Následující příklad projekty `let` výraz výsledkem spojení.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `join` s složený klíč.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `join` kde jedné straně může mít hodnotu Null a druhý není.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
