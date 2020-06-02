---
title: Získání jedné hodnoty z databáze
description: Naučte se vracet jednu hodnotu v ADO.NET. Tento ukázkový kód vrátí hodnotu sloupce identity vloženého záznamu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286699"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="a655c-104">Získání jedné hodnoty z databáze</span><span class="sxs-lookup"><span data-stu-id="a655c-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="a655c-105">Možná budete muset vrátit databázové informace, které jsou jednoduše jedinou hodnotou, nikoli ve formě tabulky nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a655c-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="a655c-106">Například můžete chtít vrátit výsledek agregační funkce, jako například COUNT ( \* ), Sum (price) nebo AVG (množství).</span><span class="sxs-lookup"><span data-stu-id="a655c-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="a655c-107">Objekt **Command** poskytuje schopnost vracet jednotlivé hodnoty pomocí metody **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="a655c-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="a655c-108">Metoda **ExecuteScalar** vrací jako skalární hodnotu hodnotu prvního sloupce prvního řádku sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="a655c-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="a655c-109">Následující příklad kódu vloží novou hodnotu do databáze pomocí <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="a655c-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="a655c-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.</span><span class="sxs-lookup"><span data-stu-id="a655c-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a655c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a655c-111">See also</span></span>

- [<span data-ttu-id="a655c-112">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="a655c-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="a655c-113">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="a655c-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="a655c-114">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="a655c-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="a655c-115">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a655c-115">ADO.NET Overview</span></span>](ado-net-overview.md)
