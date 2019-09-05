---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 0e611add4ce3f20e42bb01b0bf0392bbe81ec548
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251202"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="0e8d3-102">KOLEKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0e8d3-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="0e8d3-103">Klíčové slovo COLLECTION se používá pouze v definici vložené funkce.</span><span class="sxs-lookup"><span data-stu-id="0e8d3-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="0e8d3-104">Funkce kolekce jsou funkce, které pracují s kolekcí hodnot a tvoří skalární výstup.</span><span class="sxs-lookup"><span data-stu-id="0e8d3-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8d3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e8d3-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="0e8d3-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0e8d3-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="0e8d3-107">Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.</span><span class="sxs-lookup"><span data-stu-id="0e8d3-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e8d3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e8d3-108">Remarks</span></span>  
 <span data-ttu-id="0e8d3-109">Další informace o klíčovém slově COLLECTION naleznete v tématu [definice typů](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0e8d3-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e8d3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e8d3-110">Example</span></span>  
 <span data-ttu-id="0e8d3-111">Následující příklad ukazuje, jak použít klíčové slovo COLLECTION k deklaraci kolekce desetinných míst jako argumentu pro vloženou funkci dotazu.</span><span class="sxs-lookup"><span data-stu-id="0e8d3-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="0e8d3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e8d3-112">See also</span></span>

- [<span data-ttu-id="0e8d3-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0e8d3-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
