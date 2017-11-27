---
title: "Začínáme"
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
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c6db401f710c470ea890a7a7ac090fabef5d64c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started"></a>Začínáme
Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro přístup k SQL databáze stejně, jako by přístup kolekci v paměti.  
  
 Například `nw` je vytvořen objekt v následujícím kódu pro představují `Northwind` databáze, `Customers` je cílová tabulka, řádky jsou filtrovány pro `Customers` z `London`a řetězec pro `CompanyName` je vybrána pro načtení.  
  
 Když se spustí smyčky, kolekce `CompanyName` je načíst hodnoty.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Mezi další příklady, včetně vložení a aktualizace, najdete v tématu [co jste můžete provést pomocí technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).  
  
 Zkuste některé kurzy tak, aby měl praktických zkušeností, použití a návody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. V tématu [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
 Nakonec, zjistěte, jak začít pracovat na vlastních [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu čtení [obvyklé kroky pro použití technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [Úvod do LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [Technologie LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
