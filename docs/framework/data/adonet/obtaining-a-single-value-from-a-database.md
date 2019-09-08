---
title: Získání jedné hodnoty z databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794747"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="e3696-102">Získání jedné hodnoty z databáze</span><span class="sxs-lookup"><span data-stu-id="e3696-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="e3696-103">Možná budete muset vrátit databázové informace, které jsou jednoduše jedinou hodnotou, nikoli ve formě tabulky nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e3696-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="e3696-104">Například můžete chtít vrátit výsledek agregační funkce, jako například Count (\*), Sum (price) nebo AVG (množství).</span><span class="sxs-lookup"><span data-stu-id="e3696-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="e3696-105">Objekt **Command** poskytuje schopnost vracet jednotlivé hodnoty pomocí metody **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="e3696-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="e3696-106">Metoda **ExecuteScalar** vrací jako skalární hodnotu hodnotu prvního sloupce prvního řádku sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="e3696-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="e3696-107">Následující příklad kódu vloží novou hodnotu do databáze pomocí <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="e3696-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="e3696-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.</span><span class="sxs-lookup"><span data-stu-id="e3696-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e3696-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3696-109">See also</span></span>

- [<span data-ttu-id="e3696-110">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="e3696-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e3696-111">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="e3696-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="e3696-112">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="e3696-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="e3696-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e3696-113">ADO.NET Overview</span></span>](ado-net-overview.md)
