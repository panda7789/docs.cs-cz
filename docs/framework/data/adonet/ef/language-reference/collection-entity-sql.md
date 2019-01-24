---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506456"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="f5f61-102">KOLEKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f5f61-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="f5f61-103">KOLEKCE – klíčové slovo se používá jenom v definici vloženou funkci.</span><span class="sxs-lookup"><span data-stu-id="f5f61-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="f5f61-104">Kolekce funkcí jsou funkce, které pracují na kolekci hodnot a skalární výstup.</span><span class="sxs-lookup"><span data-stu-id="f5f61-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f61-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5f61-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="f5f61-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5f61-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="f5f61-107">Výraz, který vrátí kolekci podporovaných typů, řádky nebo odkazy.</span><span class="sxs-lookup"><span data-stu-id="f5f61-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5f61-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5f61-108">Remarks</span></span>  
 <span data-ttu-id="f5f61-109">Další informace o klíčovém slově KOLEKCE najdete v tématu [definice typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f5f61-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5f61-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5f61-110">Example</span></span>  
 <span data-ttu-id="f5f61-111">Následující příklad ukazuje, jak pomocí klíčového slova KOLEKCE můžete deklarovat kolekce desetinná čísla jako argument pro vložená funkce dotazu.</span><span class="sxs-lookup"><span data-stu-id="f5f61-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="f5f61-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5f61-112">See also</span></span>
- [<span data-ttu-id="f5f61-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f5f61-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
