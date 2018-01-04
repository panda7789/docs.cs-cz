---
title: "Postupy: použití funkce vracející skalární uživatelem definované"
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
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a70d46362ef8b2be0533a1530c79124c464375af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="8e23b-102">Postupy: použití funkce vracející skalární uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="8e23b-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="8e23b-103">Můžete namapovat metodu klienta definované na třídu pro uživatelsky definované funkce pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8e23b-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="8e23b-104">Všimněte si, že tělo metoda vytvoří výraz, který zachycuje záměr volání metody a předá tento výraz, který má <xref:System.Data.Linq.DataContext> pro překlad a spouštění.</span><span class="sxs-lookup"><span data-stu-id="8e23b-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e23b-105">Přímé provádění dojde pouze v případě, že je tato funkce volána mimo dotazu.</span><span class="sxs-lookup"><span data-stu-id="8e23b-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="8e23b-106">Další informace najdete v tématu [postup: vložené funkce Call User-Defined](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="8e23b-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e23b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e23b-107">Example</span></span>  
 <span data-ttu-id="8e23b-108">Následující kód SQL představuje skalární uživatelem definované funkce vracející `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="8e23b-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="8e23b-109">By mapování pro tento kód metodu klienta například následující:</span><span class="sxs-lookup"><span data-stu-id="8e23b-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8e23b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e23b-110">See Also</span></span>  
 [<span data-ttu-id="8e23b-111">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="8e23b-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
