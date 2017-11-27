---
title: "Získání jednu hodnotu z databáze"
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
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 513310ddfb578f127ee70059dec386f207180907
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="16c1e-102">Získání jednu hodnotu z databáze</span><span class="sxs-lookup"><span data-stu-id="16c1e-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="16c1e-103">Může být nutné na návratový databáze informace, které je jednoduše jednu hodnotu, nikoli ve formě tabulky nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="16c1e-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="16c1e-104">Například můžete chtít vrátit výsledek agregační funkce jako je například počet (\*), výraz SUM(Price) nebo AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="16c1e-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="16c1e-105">**Příkaz** objekt poskytuje možnost vrácení jedné hodnoty pomocí **ExecuteScalar** metoda.</span><span class="sxs-lookup"><span data-stu-id="16c1e-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="16c1e-106">**ExecuteScalar** metoda vrátí jako skalární hodnotu, hodnotu první sloupec prvního řádku sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="16c1e-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="16c1e-107">Následující příklad kódu vloží novou hodnotu v databázi pomocí <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="16c1e-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="16c1e-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnota sloupce identity vloženého záznamu.</span><span class="sxs-lookup"><span data-stu-id="16c1e-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="16c1e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="16c1e-109">See Also</span></span>  
 [<span data-ttu-id="16c1e-110">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="16c1e-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="16c1e-111">Spouštění příkazu</span><span class="sxs-lookup"><span data-stu-id="16c1e-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="16c1e-112">Připojení DbConnection, DbCommand a dbexception –</span><span class="sxs-lookup"><span data-stu-id="16c1e-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="16c1e-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="16c1e-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
