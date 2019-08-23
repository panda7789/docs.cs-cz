---
title: 'Postupy: Použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 17ae74a430df4d4a4670c2390ce7b2ee25b67c7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938704"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="d2329-102">Postupy: Použití uložených procedur, které přijímají parametry</span><span class="sxs-lookup"><span data-stu-id="d2329-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d2329-103">mapuje výstupní parametry na referenční parametry a pro typy hodnot deklaruje parametr jako Nullable.</span><span class="sxs-lookup"><span data-stu-id="d2329-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="d2329-104">Příklad použití vstupního parametru v dotazu, který vrací sadu řádků, naleznete v tématu [How to: Vrátit sady řádků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="d2329-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2329-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2329-105">Example</span></span>  
 <span data-ttu-id="d2329-106">Následující příklad přijímá jeden vstupní parametr (ID zákazníka) a vrací výstupní parametr (celkový prodej tohoto zákazníka).</span><span class="sxs-lookup"><span data-stu-id="d2329-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="d2329-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2329-107">Example</span></span>  
 <span data-ttu-id="d2329-108">Tuto uloženou proceduru zavoláte takto:</span><span class="sxs-lookup"><span data-stu-id="d2329-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d2329-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2329-109">See also</span></span>

- [<span data-ttu-id="d2329-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="d2329-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [<span data-ttu-id="d2329-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="d2329-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="d2329-112">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="d2329-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="d2329-113">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="d2329-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
