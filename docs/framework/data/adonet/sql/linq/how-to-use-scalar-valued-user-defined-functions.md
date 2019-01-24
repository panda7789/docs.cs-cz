---
title: 'Postupy: Použití funkce vracející skalární uživatelem definované'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 33c6ae89184b90ba69cc9c3c01f0b1ec9d7ff1cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661682"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="95151-102">Postupy: Použití funkce vracející skalární uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="95151-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="95151-103">Můžete namapovat metodu klienta definované na třídu pro uživatelem definované funkce s použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="95151-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="95151-104">Všimněte si, že tělo metody vytvoří výraz, který zachycuje cílem volání metody a předá tento výraz, který se <xref:System.Data.Linq.DataContext> pro překlad a spuštění.</span><span class="sxs-lookup"><span data-stu-id="95151-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95151-105">Přímé provádění dojde pouze v případě, že funkce je volána mimo dotazu.</span><span class="sxs-lookup"><span data-stu-id="95151-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="95151-106">Další informace najdete v tématu [jak: Volat uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="95151-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95151-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="95151-107">Example</span></span>  
 <span data-ttu-id="95151-108">Následující kód SQL představuje funkce vracející skalární uživatelem definované `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="95151-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="95151-109">Umožní mapování pro tento kód metodu klienta například následující:</span><span class="sxs-lookup"><span data-stu-id="95151-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="95151-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95151-110">See also</span></span>
- [<span data-ttu-id="95151-111">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="95151-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
