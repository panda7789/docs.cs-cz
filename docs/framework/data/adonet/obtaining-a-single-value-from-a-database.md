---
title: Získání jedné hodnoty z databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: e362a71f902739663961099cf2f43dff90b4743c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711457"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="8f47b-102">Získání jedné hodnoty z databáze</span><span class="sxs-lookup"><span data-stu-id="8f47b-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="8f47b-103">Možná bude nutné k vrácení databáze informace, které jsou pouze jednu hodnotu, nikoli ve formě tabulky nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="8f47b-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="8f47b-104">Například můžete chtít vrátit výsledek agregační funkce, jako je počet (\*), výraz SUM(Price) nebo AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="8f47b-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="8f47b-105">**Příkaz** objekt, který poskytuje schopnost vrátit jednu hodnotu pomocí **ExecuteScalar** metody.</span><span class="sxs-lookup"><span data-stu-id="8f47b-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="8f47b-106">**ExecuteScalar** metoda vrátí hodnotu jako skalární hodnota, hodnota první sloupec prvního řádku sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8f47b-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="8f47b-107">Následující příklad kódu vloží novou hodnotu v databázi pomocí <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="8f47b-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="8f47b-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.</span><span class="sxs-lookup"><span data-stu-id="8f47b-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8f47b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f47b-109">See also</span></span>
- [<span data-ttu-id="8f47b-110">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="8f47b-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="8f47b-111">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="8f47b-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="8f47b-112">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="8f47b-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="8f47b-113">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8f47b-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
