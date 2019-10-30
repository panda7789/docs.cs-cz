---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039909"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="aa4e6-102">KOLEKCE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aa4e6-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="aa4e6-103">Klíčové slovo COLLECTION se používá pouze v definici vložené funkce.</span><span class="sxs-lookup"><span data-stu-id="aa4e6-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="aa4e6-104">Funkce kolekce jsou funkce, které pracují s kolekcí hodnot a tvoří skalární výstup.</span><span class="sxs-lookup"><span data-stu-id="aa4e6-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa4e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa4e6-105">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="aa4e6-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="aa4e6-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="aa4e6-107">Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.</span><span class="sxs-lookup"><span data-stu-id="aa4e6-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa4e6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa4e6-108">Remarks</span></span>  
 <span data-ttu-id="aa4e6-109">Další informace o klíčovém slově COLLECTION naleznete v tématu [definice typů](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="aa4e6-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa4e6-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa4e6-110">Example</span></span>  
 <span data-ttu-id="aa4e6-111">Následující příklad ukazuje, jak použít klíčové slovo COLLECTION k deklaraci kolekce desetinných míst jako argumentu pro vloženou funkci dotazu.</span><span class="sxs-lookup"><span data-stu-id="aa4e6-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="aa4e6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa4e6-112">See also</span></span>

- [<span data-ttu-id="aa4e6-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="aa4e6-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
