---
title: Možnosti použití LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: e84047843aff4044c75ba1b971a9e2f061e2e8d6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75633998"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Možnosti použití LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje všechny klíčové funkce, které byste očekávali jako vývojář SQL. Můžete zadávat dotazy na informace a vkládat, aktualizovat a odstraňovat informace z tabulek.  
  
## <a name="selecting"></a>Výběr  
 Výběr (*projekce*) se dosahuje pouhým zápisem dotazu LINQ ve vlastním programovacím jazyce a následným spuštěním tohoto dotazu, který načte výsledky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sám přeloží všechny nezbytné operace na nezbytné operace SQL, se kterými jste se seznámili. Další informace najdete v tématu [LINQ to SQL](index.md).  
  
 V následujícím příkladu se v okně konzoly načtou a zobrazují názvy společností zákazníků z Londýna.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Vkládání  
 Chcete-li spustit `Insert`SQL, stačí přidat objekty do objektového modelu, který jste vytvořili, a volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 V následujícím příkladu se do tabulky `Customers` přidá nový zákazník a informace o zákazníkovi pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizace  
 Chcete-li `Update` položku databáze, nejprve Načtěte položku a upravte ji přímo v objektovém modelu. Po úpravě objektu volejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v <xref:System.Data.Linq.DataContext>, aby se aktualizovala databáze.  
  
 V následujícím příkladu jsou načteni všichni zákazníci z Londýna. Pak se název města změní z "Londýn" na "Londýn-Metro". Nakonec je volána <xref:System.Data.Linq.DataContext.SubmitChanges%2A> k odeslání změn do databáze.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Odstraňování  
 Chcete-li `Delete` položku, odeberte položku z kolekce, do které patří, a poté zavoláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> potvrďte změnu.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nerozpoznají operace kaskádového odstranění. Pokud chcete odstranit řádek v tabulce, která má omezení proti, přečtěte si téma [Postup: odstranění řádků z databáze](how-to-delete-rows-from-the-database.md).  
  
 V následujícím příkladu je zákazník, který má `CustomerID` `98128`, načten z databáze. Po potvrzení, že byl řádek zákazníka načten, je volána <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> pro odebrání tohoto objektu z kolekce. Nakonec se zavolá <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, aby se odstranění předalo do databáze.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Začínáme](getting-started.md)
