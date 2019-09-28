---
title: 'Postupy: Použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: c2b657f704d072b987578be5520a58d007ecac37
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353017"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="bb51c-102">Postupy: Použití uložených procedur, které přijímají parametry</span><span class="sxs-lookup"><span data-stu-id="bb51c-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="bb51c-103">mapuje výstupní parametry na referenční parametry a pro typy hodnot deklaruje parametr jako Nullable.</span><span class="sxs-lookup"><span data-stu-id="bb51c-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="bb51c-104">Příklad použití vstupního parametru v dotazu, který vrací sadu řádků, naleznete v tématu [How na: Vrátí sady řádků @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="bb51c-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb51c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb51c-105">Example</span></span>  
 <span data-ttu-id="bb51c-106">Následující příklad přijímá jeden vstupní parametr (ID zákazníka) a vrací výstupní parametr (celkový prodej tohoto zákazníka).</span><span class="sxs-lookup"><span data-stu-id="bb51c-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bb51c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb51c-107">Example</span></span>  
 <span data-ttu-id="bb51c-108">Tuto uloženou proceduru zavoláte takto:</span><span class="sxs-lookup"><span data-stu-id="bb51c-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bb51c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb51c-109">See also</span></span>

- [<span data-ttu-id="bb51c-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="bb51c-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="bb51c-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="bb51c-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="bb51c-112">Použití typů hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="bb51c-112">Using Nullable Value Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="bb51c-113">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="bb51c-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
