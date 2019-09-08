---
title: Možnosti použití LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 8baf361ba66ba33927121ae20edcc6c12964c21c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792095"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Možnosti použití LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje všechny klíčové funkce, které byste očekávali jako vývojář SQL. Můžete zadávat dotazy na informace a vkládat, aktualizovat a odstraňovat informace z tabulek.  
  
## <a name="selecting"></a>Výběr  
 Výběr (*projekce*) se dosahuje pouhým zápisem [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazu ve vlastním programovacím jazyce a následným spuštěním tohoto dotazu, který načte výsledky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sám sebe převede všechny nezbytné operace na nezbytné operace SQL, se kterými jste se seznámili. Další informace najdete v tématu [LINQ to SQL](index.md).  
  
 V následujícím příkladu se v okně konzoly načtou a zobrazují názvy společností zákazníků z Londýna.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Vkládání  
 Chcete-li spustit `Insert`SQL, stačí přidat objekty do objektového modelu, který jste vytvořili, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> a zavolat <xref:System.Data.Linq.DataContext>na.  
  
 V následujícím příkladu je nový zákazník a informace o zákazníkovi přidány do `Customers` tabulky pomocí. <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Doplnění  
 K `Update` položce databáze nejprve Načtěte položku a upravte ji přímo v objektovém modelu. Po úpravě objektu zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> na, aby se aktualizovala databáze.  
  
 V následujícím příkladu jsou načteni všichni zákazníci z Londýna. Pak se název města změní z "Londýn" na "Londýn-Metro". <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Nakonec je volána k odeslání změn do databáze.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Odstraňuje  
 Na `Delete` položku, odeberte položku z kolekce, do které patří, a potom zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> na k potvrzení změny.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nerozpozná operace kaskádového odstranění. Pokud chcete odstranit řádek v tabulce s omezeními, přečtěte si téma [How to: Odstraní řádky z databáze](how-to-delete-rows-from-the-database.md).  
  
 V následujícím příkladu je zákazník, který `CustomerID` je z `98128` databáze načten. Po potvrzení, že se řádek zákazníka načetl, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> se pak zavolá, aby se tento objekt odebral z kolekce. Nakonec se <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volá, aby se odstranění předalo do databáze.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Začínáme](getting-started.md)
