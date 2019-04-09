---
title: 'Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: ffb24468c81cb4ec9f41645f8888c2c4ba021609
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127159"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="3fd05-102">Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami</span><span class="sxs-lookup"><span data-stu-id="3fd05-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="3fd05-103">Můžete namapovat metodu klienta definované na třídu pro uživatelem definované funkce s použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="3fd05-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="3fd05-104">Všimněte si, že tělo metody vytvoří výraz, který zachycuje cílem volání metody a předá tento výraz, který se <xref:System.Data.Linq.DataContext> pro překlad a spuštění.</span><span class="sxs-lookup"><span data-stu-id="3fd05-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fd05-105">Přímé provádění dojde pouze v případě, že funkce je volána mimo dotazu.</span><span class="sxs-lookup"><span data-stu-id="3fd05-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="3fd05-106">Další informace najdete v tématu [jak: Volat uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="3fd05-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd05-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fd05-107">Example</span></span>  
 <span data-ttu-id="3fd05-108">Následující kód SQL představuje funkce vracející skalární uživatelem definované `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="3fd05-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="3fd05-109">Umožní mapování pro tento kód metodu klienta například následující:</span><span class="sxs-lookup"><span data-stu-id="3fd05-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3fd05-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fd05-110">See also</span></span>

- [<span data-ttu-id="3fd05-111">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="3fd05-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
