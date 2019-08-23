---
title: 'Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 0d757e3c37f347014eb2ef90b4e61ddd205dd012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938671"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="318c9-102">Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami</span><span class="sxs-lookup"><span data-stu-id="318c9-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="318c9-103">Metodu klienta definovanou pro třídu lze namapovat na uživatelsky definovanou funkci pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="318c9-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="318c9-104">Všimněte si, že tělo metody vytvoří výraz, který zachycuje záměr volání metody, a předá tento výraz <xref:System.Data.Linq.DataContext> pro účely překladu a provedení.</span><span class="sxs-lookup"><span data-stu-id="318c9-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="318c9-105">K přímému provedení dojde pouze v případě, že je funkce volána mimo dotaz.</span><span class="sxs-lookup"><span data-stu-id="318c9-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="318c9-106">Další informace najdete v tématu [jak: Volání uživatelsky definovaných funkcí je](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)vloženo.</span><span class="sxs-lookup"><span data-stu-id="318c9-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="318c9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="318c9-107">Example</span></span>  
 <span data-ttu-id="318c9-108">Následující kód SQL prezentuje uživatelsky definovanou funkci `ReverseCustName()`s skalární hodnotou.</span><span class="sxs-lookup"><span data-stu-id="318c9-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="318c9-109">Namapujete metodu klienta, například následující pro tento kód:</span><span class="sxs-lookup"><span data-stu-id="318c9-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="318c9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="318c9-110">See also</span></span>

- [<span data-ttu-id="318c9-111">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="318c9-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
