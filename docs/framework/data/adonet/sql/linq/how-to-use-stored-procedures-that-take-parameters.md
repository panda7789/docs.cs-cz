---
title: 'Postupy: Použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 8dd463c895efcddfe288fe1dc8571981872d9d80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033603"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="42029-102">Postupy: Použití uložených procedur, které přijímají parametry</span><span class="sxs-lookup"><span data-stu-id="42029-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="42029-103">mapuje výstupní parametry k odkazování parametrů a typů hodnot deklaruje parametr jako s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="42029-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="42029-104">Příklad použití jako vstupní parametr v dotazu, který vrátí sadu řádků, naleznete v tématu [jak: Vrácení sad řádků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="42029-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42029-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="42029-105">Example</span></span>  
 <span data-ttu-id="42029-106">V následujícím příkladu má jeden vstupní parametr (ID zákazníka) a vrátí parametr out (celkový prodej daného zákazníka).</span><span class="sxs-lookup"><span data-stu-id="42029-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="42029-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="42029-107">Example</span></span>  
 <span data-ttu-id="42029-108">Tuto uloženou proceduru by volat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="42029-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="42029-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42029-109">See also</span></span>

- [<span data-ttu-id="42029-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="42029-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [<span data-ttu-id="42029-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="42029-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="42029-112">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="42029-112">Using Nullable Types</span></span>](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="42029-113">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="42029-113">Nullable Value Types</span></span>](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
