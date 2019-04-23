---
title: ADO.NET a LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 10e60ebd71c4615354c25d3a61a04e9d12d7c800
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167190"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET a LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řady technologií. Je založen na služby poskytované [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] modelu poskytovatele. Proto můžete kombinovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kódu s existujícím [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikací a migrovat aktuální [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řešení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Následující obrázek poskytuje podrobný pohled vztahu.  
  
 ![Technologie LINQ to SQL a ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Připojení  
 Můžete zadat existující [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] připojení při vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Všechny operace s <xref:System.Data.Linq.DataContext> (včetně dotazů) použijte tento připojení k dispozici. Pokud už je připojení otevřeno, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] opustí to tak je, když jste hotovi s ním.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Vždy můžete získat přístup k připojení a zavřete ho sami pomocí <xref:System.Data.Linq.DataContext.Connection%2A> vlastnost, stejně jako v následujícím kódu:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakce  
 Můžete zadat vaše <xref:System.Data.Linq.DataContext> s vlastní databázové transakci, pokud vaše aplikace už zahájila transakce a chcete, aby vaše <xref:System.Data.Linq.DataContext> zapojit.  
  
 Preferovanou metodu provádění transakcí pomocí [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] , je použít <xref:System.Transactions.TransactionScope> objektu. Pomocí tohoto přístupu můžete provést distribuované transakce, které fungují s databází a jiných prostředků rezidentní. Obory transakce vyžadovat několik prostředků ke spuštění. Se zvýšit úroveň sami na distribuované transakce pouze v případě, že existuje více připojení v rámci oboru transakce.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Tento přístup nelze použít pro všechny databáze. Například SqlClient připojení nelze povýšit systému transakcích, když bude fungovat s [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serveru. Místo toho automaticky nezvládnou úplné, distribuované transakci pokaždé, když vidí oboru transakce se používají.  
  
## <a name="direct-sql-commands"></a>Příkazy jazyka SQL s přímým přístupem  
 V některých případech může nastat situace, kdy schopnost <xref:System.Data.Linq.DataContext> dotazování a odesílání není dostatečná pro specializované úlohu chcete provést změny. V těchto případech můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu vydávat příkazy SQL na databázi a proveďte převod na objekty výsledků dotazu.  
  
 Například předpokládejme, že data `Customer` třídy se pak rozdělí více než dvě tabulky (customer1 a customer2). Následující dotaz vrátí sekvenci `Customer` objekty:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Za předpokladu, názvy sloupců v tabulkové výsledky odpovídají sloupec vlastnosti vaší entity třídy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo jakýkoli dotaz SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda přijímá parametry. Následující kód provede parametrizovaného dotazu:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametry jsou vyjádřeny v textu dotazu pomocí stejné složených zápisu používají `Console.WriteLine()` a `String.Format()`. `String.Format()` řetězec dotazu, zadejte a nahradí složených braced parametry s generované názvy parametrů, jako `@p0`, `@p1` ..., `@p(n)`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
