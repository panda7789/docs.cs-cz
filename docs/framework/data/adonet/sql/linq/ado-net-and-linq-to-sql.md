---
title: ADO.NET a LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979999"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET a LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí řady technologií ADO.NET. Vychází ze služeb poskytovaných modelem poskytovatele ADO.NET. Proto můžete v existujících aplikacích ADO.NET kombinovat kód [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a migrovat aktuální ADO.NET řešení do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Následující obrázek poskytuje podrobný pohled na vztah.  
  
 ![LINQ to SQL a ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Připojení  
 Při vytváření <xref:System.Data.Linq.DataContext>[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dodat existující připojení ADO.NET. Toto poskytnutá připojení se používají u všech operací proti <xref:System.Data.Linq.DataContext> (včetně dotazů). Pokud je připojení už otevřené, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ho po dokončení donechání.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 K připojení můžete vždy přistupovat a jeho zavřením pomocí vlastnosti <xref:System.Data.Linq.DataContext.Connection%2A>, jak je uvedeno v následujícím kódu:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakce  
 Svou <xref:System.Data.Linq.DataContext> můžete dodat s vlastní databázovou transakcí, pokud vaše aplikace už transakci iniciovala a chcete, aby se do <xref:System.Data.Linq.DataContext> podílely.  
  
 Upřednostňovanou metodou provádění transakcí s .NET Framework je použití objektu <xref:System.Transactions.TransactionScope>. Pomocí tohoto přístupu můžete provádět distribuované transakce, které fungují napříč databázemi a dalšími správci prostředků rezidentů v paměti. Rozsahy transakcí vyžadují, aby bylo možné spustit několik zdrojů. Propagují se na distribuované transakce pouze v případě, že je v rámci oboru transakce více připojení.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Tento přístup nelze použít pro všechny databáze. Připojení SqlClient například nemůže propagovat systémové transakce, když funguje na serveru s SQL Server 2000. Místo toho automaticky zařadí úplnou distribuovanou transakci pokaždé, když uvidí rozsah transakce, který se používá.  
  
## <a name="direct-sql-commands"></a>Přímé příkazy SQL  
 V době, kdy se můžete setkat s situacemi, kdy je schopnost <xref:System.Data.Linq.DataContext> dotazovat nebo odeslat změny nedostatečná pro specializovanou úlohu, kterou chcete provést. V těchto případech můžete použít metodu <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> k vystavení příkazů SQL pro databázi a převést výsledky dotazu na objekty.  
  
 Předpokládejme například, že data pro `Customer` třídy jsou rozložena do dvou tabulek (Customer1 a Customer2). Následující dotaz vrací sekvenci `Customer` objektů:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.  
  
### <a name="parameters"></a>Parametry  
 Metoda <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> akceptuje parametry. Následující kód provede parametrizovaný dotaz:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené notace, kterou používá `Console.WriteLine()` a `String.Format()`. `String.Format()` převezme řetězec dotazu, který zadáte, a nahradíte parametry složené závorky s generovanými názvy parametrů, jako je `@p0`, `@p1`..., `@p(n)`.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
- [Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
