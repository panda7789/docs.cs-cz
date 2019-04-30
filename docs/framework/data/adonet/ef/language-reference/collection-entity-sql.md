---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 8cd440571726796ee3d2c91e0d2f6b50571e8e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785324"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="a1a06-102">KOLEKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a1a06-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="a1a06-103">KOLEKCE – klíčové slovo se používá jenom v definici vloženou funkci.</span><span class="sxs-lookup"><span data-stu-id="a1a06-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="a1a06-104">Kolekce funkcí jsou funkce, které pracují na kolekci hodnot a skalární výstup.</span><span class="sxs-lookup"><span data-stu-id="a1a06-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a06-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1a06-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="a1a06-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a1a06-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="a1a06-107">Výraz, který vrátí kolekci podporovaných typů, řádky nebo odkazy.</span><span class="sxs-lookup"><span data-stu-id="a1a06-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1a06-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1a06-108">Remarks</span></span>  
 <span data-ttu-id="a1a06-109">Další informace o klíčovém slově KOLEKCE najdete v tématu [definice typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a1a06-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1a06-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1a06-110">Example</span></span>  
 <span data-ttu-id="a1a06-111">Následující příklad ukazuje, jak pomocí klíčového slova KOLEKCE můžete deklarovat kolekce desetinná čísla jako argument pro vložená funkce dotazu.</span><span class="sxs-lookup"><span data-stu-id="a1a06-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="a1a06-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1a06-112">See also</span></span>

- [<span data-ttu-id="a1a06-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a1a06-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
