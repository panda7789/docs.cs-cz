---
title: ADO.NET a technologie LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: b2be963862b6bd7a0cd5643245606763907a5b72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET a technologie LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodiny technologií. Je založena na služeb poskytovaných [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] zprostředkovatele modelu. Proto je možné kombinovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kód s existujícím [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikace a migrovat aktuální [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řešení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Následující obrázek poskytuje podrobný pohled relace.  
  
 ![Technologie LINQ to SQL a ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Připojení  
 Můžete zadat existující [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] připojení při vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Všechny operace proti <xref:System.Data.Linq.DataContext> (včetně dotazů) použít zadané připojení. Pokud připojení je již otevřeno, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ponechá ji jako je po dokončení s ním.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Kdykoli můžete získat přístup k připojení a zavřete ho sami pomocí <xref:System.Data.Linq.DataContext.Connection%2A> vlastnosti, jako v následujícím kódu:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakce  
 Můžete zadat vaše <xref:System.Data.Linq.DataContext> s vlastní transakcí databáze, když vaše aplikace již inicioval transakce a chcete, aby vaše <xref:System.Data.Linq.DataContext> zabývajících.  
  
 Upřednostňovaný způsob provádění transakcí pomocí [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] , je použít <xref:System.Transactions.TransactionScope> objektu. Když použijete tuto metodu, můžete provést distribuované transakce, které pracují mezi databází a jiným správcům rezidentní prostředků. Transakce obory vyžadovat několik prostředků ke spuštění. Jejich povýšení sami na distribuovaných transakcí jenom v případě, že je víc připojení v rámci oboru transakce.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Tuto metodu nelze použít pro všechny databáze. Například SqlClient připojení se nedá povýšit transakcí systému při funguje proti [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serveru. Místo toho je automaticky zapsán úplné a distribuované transakce vždy, když je detekována oboru transakce používá.  
  
## <a name="direct-sql-commands"></a>Přímé SQL příkazy  
 V některých případech se můžete setkat situacích kde schopnost <xref:System.Data.Linq.DataContext> dotazu nebo odeslání změn je nedostatečná pro speciální úlohu, kterou chcete provést. V těchto případech můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metoda vydávat příkazy SQL databázi a převedeno na objekty výsledků dotazu.  
  
 Například předpokládejme, že data `Customer` třída je rozdělena ve dvou tabulek (customer1 a customer2). Následující dotaz vrátí posloupnost `Customer` objekty:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tak dlouho, dokud shodovat s názvy sloupců v tabulkové výsledky sloupce vlastnosti třídy entity [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří vašich objektů mimo jakýkoli dotaz SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda přijímá parametry. Následující kód spustí parametrizovaného dotazu:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené zápisu používané `Console.WriteLine()` a `String.Format()`. `String.Format()` přebírá řetězec dotazu zadejte a nahradí složené braced parametry s generované názvy parametrů jako `@p0`, `@p1` ..., `@p(n)`.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
