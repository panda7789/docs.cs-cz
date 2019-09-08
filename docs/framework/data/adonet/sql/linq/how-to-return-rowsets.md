---
title: 'Postupy: Vrácení sad řádků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 5ec188e0345140297062d0a10dfbbc4a294bbb7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781605"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="d3405-102">Postupy: Vrácení sad řádků</span><span class="sxs-lookup"><span data-stu-id="d3405-102">How to: Return Rowsets</span></span>
<span data-ttu-id="d3405-103">Tento příklad vrátí sadu řádků z databáze a obsahuje vstupní parametr pro filtrování výsledku.</span><span class="sxs-lookup"><span data-stu-id="d3405-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="d3405-104">Když spustíte uloženou proceduru, která vrací sadu řádků, použijete *výslednou* třídu, která ukládá návraty z uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="d3405-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="d3405-105">Další informace najdete v tématu [analýza zdrojového kódu LINQ to SQL](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="d3405-105">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3405-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3405-106">Example</span></span>  
 <span data-ttu-id="d3405-107">Následující příklad představuje uloženou proceduru, která vrací řádky zákazníků, a používá vstupní parametr, který vrátí pouze řádky, které uvádějí "Londýn" jako město zákazníka.</span><span class="sxs-lookup"><span data-stu-id="d3405-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="d3405-108">Příklad předpokládá vyčíslitelné `CustomersByCityResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="d3405-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d3405-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3405-109">See also</span></span>

- [<span data-ttu-id="d3405-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="d3405-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="d3405-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="d3405-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
