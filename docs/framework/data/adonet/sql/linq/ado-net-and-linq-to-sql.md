---
title: ADO.NET a LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: b47a46f9fd9ef3ef1935fa7a88c2e60fe80db09d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964131"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET a LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je součástí řady technologií ADO.NET. Vychází ze služeb poskytovaných modelem poskytovatele ADO.NET. Proto můžete kombinovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kód s existujícími aplikacemi ADO.NET a migrovat aktuální ADO.NET řešení do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Následující obrázek poskytuje podrobný pohled na vztah.  
  
 ![LINQ to SQL a ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Připojení  
 Existující připojení ADO.NET můžete při vytváření vytvořit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Data.Linq.DataContext> Tato dodaná připojení <xref:System.Data.Linq.DataContext> používají všechny operace proti (včetně dotazů). Pokud je připojení již otevřeno, ponechá ho v době, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kdy jste s ním skončili.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 K připojení můžete vždy přistupovat a uzavřít ho pomocí <xref:System.Data.Linq.DataContext.Connection%2A> vlastnosti, jako v následujícím kódu:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakce  
 Můžete dodat svou <xref:System.Data.Linq.DataContext> vlastní databázovou transakci, pokud vaše aplikace již transakci iniciovala a <xref:System.Data.Linq.DataContext> chcete, aby byla zahrnuta.  
  
 Upřednostňovanou metodou provádění transakcí s .NET Framework je použití <xref:System.Transactions.TransactionScope> objektu. Pomocí tohoto přístupu můžete provádět distribuované transakce, které fungují napříč databázemi a dalšími správci prostředků rezidentů v paměti. Rozsahy transakcí vyžadují, aby bylo možné spustit několik zdrojů. Propagují se na distribuované transakce pouze v případě, že je v rámci oboru transakce více připojení.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Tento přístup nelze použít pro všechny databáze. Připojení SqlClient například nemůže propagovat systémové transakce, když funguje na serveru s SQL Server 2000. Místo toho automaticky zařadí úplnou distribuovanou transakci pokaždé, když uvidí rozsah transakce, který se používá.  
  
## <a name="direct-sql-commands"></a>Přímé příkazy SQL  
 V době, kdy se můžete setkat s situacemi, <xref:System.Data.Linq.DataContext> kdy je schopnost dotazování nebo odeslání změn nedostatečná pro specializovanou úlohu, kterou chcete provést. V těchto případech můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu k vystavení příkazů SQL Database a převést výsledky dotazu na objekty.  
  
 Předpokládejme například, že data pro `Customer` třídu jsou rozložena do dvou tabulek (Customer1 a Customer2). Následující dotaz vrátí sekvenci `Customer` objektů:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda přijímá parametry. Následující kód provede parametrizovaný dotaz:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametry jsou vyjádřeny v textu dotazu pomocí stejného složeného zápisu `Console.WriteLine()` , který používá a. `String.Format()` `String.Format()`Převede řetězec dotazu, který zadáte, a nahradí parametry složené závorky s generovanými názvy parametrů `@p0`, například, `@p1` ..., `@p(n)`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Postupy: Opakované použití připojení mezi příkazem ADO.NET a DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
