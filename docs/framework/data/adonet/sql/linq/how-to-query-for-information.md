---
title: 'Postupy: Dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: aedf89f1e570b34d31050fabb91842cefe351488
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162839"
---
# <a name="how-to-query-for-information"></a>Postupy: Dotaz na informace
Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používají stejnou syntaxi jako dotazy v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jediným rozdílem je, že objekty odkazuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou mapovány na prvky v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy, které zápisu do odpovídající dotazy SQL a odesílá je do serveru pro zpracování.  
  
 Některé funkce [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazů může být nutné zvláštní pozornost v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikací. Další informace najdete v tématu [koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz vyzve k zadání seznam zákazníků z Londýna. V tomto příkladu `Customers` je tabulky v ukázkové databázi Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
