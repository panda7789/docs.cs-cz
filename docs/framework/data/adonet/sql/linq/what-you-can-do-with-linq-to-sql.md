---
title: "Co můžete dělat s technologie LINQ to SQL"
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
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 70e783c0ad6b13097aaa1912f1338714a1f43f73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Co můžete dělat s technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje všechny klíčové funkce, které očekáváte jako vývojář SQL. Můžete dotazovat na informace a vložit, aktualizovat a odstranit informace z tabulky.  
  
## <a name="selecting"></a>Výběr  
 Výběr (*projekce*) se dosahuje právě zápis [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazu v vlastní programovací jazyk a spouštění tento dotaz pro načtení výsledky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]samotný přeloží všechny potřebné operace do potřebné operace SQL, které jste se seznámili s. Další informace najdete v tématu [technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 V následujícím příkladu jsou názvy společnosti zákazníků z Londýna načíst a zobrazí v okně konzoly.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Vkládání  
 K provedení SQL `Insert`, stačí přidat objekty do objektový model, který jste vytvořili a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 V následujícím příkladu se přidá nový zákazníka a informace o zákazníkovi, na `Customers` tabulky pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizace  
 K `Update` záznam databáze nejprve získání položky a upravit ho přímo v objektovém modelu. Po úpravě objektu volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> k aktualizaci databáze.  
  
 V následujícím příkladu jsou načteny všechny zákazníky, kteří jsou z Londýna. Potom název města, se změní z "Praha" na "Londýn – Metro". Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nazývá odešlete změny do databáze.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Odstranění  
 K `Delete` položku, odebrání položky z kolekce, do které patří a pak volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> potvrzení změn.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nerozpoznal kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, který má omezení u ní najdete v tématu [postupy: odstranění řádků z databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 V následujícím příkladu, zákazníkovi, který má `CustomerID` z `98128` se načítají z databáze. Potom po potvrzení, že byla načtena řádek zákazníka, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> nazývá odebrat tento objekt z kolekce. Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nazývá předávat odstranění do databáze.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
