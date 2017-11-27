---
title: 'Postupy: dotaz na informace'
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
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0722f83c19c1eff43606afceeda484d72691eb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-information"></a>Postupy: dotaz na informace
Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používají stejnou syntaxi jako dotazy v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jediným rozdílem je, že objekty odkazovaný ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou namapované na elementy v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přeloží dotazy, které můžete psát na ekvivalentní dotazy SQL a odešle je server pro zpracování.  
  
 Některé funkce [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy může být nutné zvláštní pozornost v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace. Další informace najdete v tématu [dotazu koncepty](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz zobrazí seznam zákazníky z Londýna. V tomto příkladu `Customers` je tabulky v ukázkové databázi Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Dotaz na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
