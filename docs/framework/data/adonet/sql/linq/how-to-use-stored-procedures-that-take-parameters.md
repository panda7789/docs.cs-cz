---
title: "Postupy: pomocí uložených procedur, které provést parametry"
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
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28f389d7128283501291bc3220cfde3815cc0713
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="96d60-102">Postupy: pomocí uložených procedur, které provést parametry</span><span class="sxs-lookup"><span data-stu-id="96d60-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="96d60-103">mapuje výstupní parametry tak, aby odkazovaly parametry a u typů hodnot deklaruje parametr jako s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="96d60-103"> maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="96d60-104">Příklad použití vstupní parametr v dotazu, který vrací sadu řádků, naleznete v části [postupy: vrácení sady řádků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="96d60-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96d60-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="96d60-105">Example</span></span>  
 <span data-ttu-id="96d60-106">V následujícím příkladu má jeden vstupní parametr (ID zákazníka) a vrátí parametr typu out (celkový prodej tohoto zákazníka).</span><span class="sxs-lookup"><span data-stu-id="96d60-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="96d60-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="96d60-107">Example</span></span>  
 <span data-ttu-id="96d60-108">Tuto uloženou proceduru by volání následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="96d60-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="96d60-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="96d60-109">See Also</span></span>  
 [<span data-ttu-id="96d60-110">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="96d60-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="96d60-111">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="96d60-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="96d60-112">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="96d60-112">Using Nullable Types</span></span>](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="96d60-113">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="96d60-113">Nullable Value Types</span></span>](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
