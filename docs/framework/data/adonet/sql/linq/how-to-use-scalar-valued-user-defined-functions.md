---
title: 'Postupy: použití uživatelem definovaných funkcí s skalární hodnotou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: dfe82fd50eb3eedeaff9082a4288901f72197795
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003234"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="dae57-102">Postupy: použití uživatelem definovaných funkcí s skalární hodnotou</span><span class="sxs-lookup"><span data-stu-id="dae57-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="dae57-103">Metodu klienta definovanou pro třídu lze namapovat na uživatelsky definovanou funkci pomocí atributu <xref:System.Data.Linq.Mapping.FunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dae57-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="dae57-104">Všimněte si, že tělo metody vytvoří výraz, který zachycuje záměr volání metody, a předá tento výraz <xref:System.Data.Linq.DataContext> pro účely překladu a provedení.</span><span class="sxs-lookup"><span data-stu-id="dae57-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dae57-105">K přímému provedení dojde pouze v případě, že je funkce volána mimo dotaz.</span><span class="sxs-lookup"><span data-stu-id="dae57-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="dae57-106">Další informace naleznete v tématu [How to: Calling User-Defined Functions inline](how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="dae57-106">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae57-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="dae57-107">Example</span></span>  
 <span data-ttu-id="dae57-108">Následující kód SQL prezentuje uživatelem definovanou funkci `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="dae57-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="dae57-109">Namapujete metodu klienta, například následující pro tento kód:</span><span class="sxs-lookup"><span data-stu-id="dae57-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="dae57-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dae57-110">See also</span></span>

- [<span data-ttu-id="dae57-111">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="dae57-111">User-Defined Functions</span></span>](user-defined-functions.md)
