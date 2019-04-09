---
title: 'Postupy: Vrácení sad řádků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 599ad6f722251003ab56547ce050cbd0e8da831d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168711"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="ac8f1-102">Postupy: Vrácení sad řádků</span><span class="sxs-lookup"><span data-stu-id="ac8f1-102">How to: Return Rowsets</span></span>
<span data-ttu-id="ac8f1-103">V tomto příkladu vrátí sadu řádků z databáze a zahrnuje vstupní parametr a filtrovat výsledky.</span><span class="sxs-lookup"><span data-stu-id="ac8f1-103">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="ac8f1-104">Při spouštění uložené procedury, která vrací sadu řádků, je použít *výsledek* třída, která obsahuje tato vrátí hodnotu z úložné procedury.</span><span class="sxs-lookup"><span data-stu-id="ac8f1-104">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="ac8f1-105">Další informace najdete v tématu [analýza LINQ to SQL zdrojový kód](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="ac8f1-105">For more information, see [Analyzing LINQ to SQL Source Code](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8f1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac8f1-106">Example</span></span>  
 <span data-ttu-id="ac8f1-107">Následující příklad představuje uloženou proceduru, která vrací řádky zákazníků a vrátit pouze řádky tohoto seznamu "Londýn" jako název města zákazníka pomocí vstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="ac8f1-107">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="ac8f1-108">Příklad předpokládá Výčtový objekt `CustomersByCityResult` třídy.</span><span class="sxs-lookup"><span data-stu-id="ac8f1-108">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac8f1-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac8f1-109">See also</span></span>

- [<span data-ttu-id="ac8f1-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="ac8f1-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [<span data-ttu-id="ac8f1-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="ac8f1-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
