---
title: Možnosti použití LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: efb7b86c3add99e596e6798c8267c09689899d56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923926"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Možnosti použití LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje všechny klíčové funkce, které očekáváte jako vývojář SQL. Můžete dotazovat na informace a vložit, aktualizovat a odstranit informace z tabulky.  
  
## <a name="selecting"></a>Výběr  
 Výběr (*projekce*) můžete vytvořit jenom zápis [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazování v programovacím jazyce a pak spouštějící tento dotaz k načtení výsledků. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] samotný přeloží všechny potřebné operace do nezbytné úkony SQL, které znáte. Další informace najdete v tématu [technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 V následujícím příkladu se názvy společností zákazníků z Londýna načte a zobrazí v okně konzoly.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Vložení  
 K provedení SQL `Insert`, stačí přidat objekty do modelu objektu, který jste vytvořili a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 V následujícím příkladu nového zákazníka a informace o zákazníkovi, přidá se do `Customers` tabulky s použitím <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizace  
 K `Update` položky databáze, nejdřív načíst položku a upravte jej přímo v objektovém modelu. Poté, co jste změnili objektu, volejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> aktualizaci databáze.  
  
 V následujícím příkladu jsou načteny všechny zákazníky, kteří jsou z Londýna. Potom název města, se změní z "Londýn" na "Londýn – Metro". Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána k odeslání změn do databáze.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Odstraňuje se  
 K `Delete` některou položku, odeberte položku z kolekce, do které patří a poté zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> potvrzení změn.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operace kaskádové odstranění nebyl rozpoznán. Pokud chcete odstranit řádek v tabulce, která má omezení pro to, najdete v článku [jak: Odstranit řádky z databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 V následujícím příkladu zákazníka, který má `CustomerID` z `98128` je načtena z databáze. Po potvrzení, že se načetla řádku zákazníka, pak <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> je volána k odebrání objektu z kolekce. Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána k předávání odstranění do databáze.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Začínáme](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
