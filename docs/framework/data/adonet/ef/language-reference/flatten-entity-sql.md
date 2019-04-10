---
title: Sloučit (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304569"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="03638-102">Sloučit (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="03638-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="03638-103">Převede kolekci kolekcí plochá kolekce.</span><span class="sxs-lookup"><span data-stu-id="03638-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="03638-104">Nová kolekce obsahuje stejné prvky jako původní kolekce, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="03638-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03638-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03638-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="03638-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="03638-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="03638-107">Libovolný platný výraz, který vrátí kolekci hodnota kolekce k shrnout do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="03638-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03638-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03638-108">Remarks</span></span>  
 `FLATTEN` <span data-ttu-id="03638-109">je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="03638-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="03638-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="03638-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="03638-111">Zobrazit [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) prioritu informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="03638-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03638-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="03638-112">Example</span></span>  
 <span data-ttu-id="03638-113">Následující dotaz Entity SQL používá `FLATTEN` operátor převést kolekci plochá kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="03638-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="03638-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="03638-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="03638-115">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="03638-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="03638-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="03638-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="03638-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03638-117">See also</span></span>

- [<span data-ttu-id="03638-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="03638-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
