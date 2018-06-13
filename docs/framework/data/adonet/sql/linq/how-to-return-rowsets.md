---
title: 'Postupy: vrácení sady řádků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: a2666b752d936e10d377113d5bf18111393df3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361134"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="90e2a-102">Postupy: vrácení sady řádků</span><span class="sxs-lookup"><span data-stu-id="90e2a-102">How to: Return Rowsets</span></span>
<span data-ttu-id="90e2a-103">Tento příklad vrací sadu řádků z databáze a zahrnuje vstupní parametr filtrovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="90e2a-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="90e2a-104">Při spuštění uložené procedury, jež vrací sadu řádků, je použít *výsledek* třídu, která ukládá vrátí z uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="90e2a-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="90e2a-105">Další informace najdete v tématu [analýza technologie LINQ to SQL zdrojový kód](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="90e2a-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90e2a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="90e2a-106">Example</span></span>  
 <span data-ttu-id="90e2a-107">V následujícím příkladu představuje uložené procedury, jež vrací řádky zákazníků a používá vstupní parametr vrátit pouze řádky tohoto seznamu "Praha" jako město zákazníka.</span><span class="sxs-lookup"><span data-stu-id="90e2a-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="90e2a-108">Příklad předpokládá Výčtový `CustomersByCityResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="90e2a-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90e2a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e2a-109">See Also</span></span>  
 [<span data-ttu-id="90e2a-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="90e2a-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="90e2a-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="90e2a-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
