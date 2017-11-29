---
title: "VYROVNÁNÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 226f7fa14331ee8e2500ac91a665e86928e37f8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="53815-102">VYROVNÁNÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="53815-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="53815-103">Převede kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="53815-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="53815-104">Nová kolekce obsahuje všechny stejné prvky, jako původní kolekce, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="53815-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53815-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53815-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="53815-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="53815-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="53815-107">Libovolný platný výraz, který vrátí kolekce hodnota kolekcí k vyrovnání do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="53815-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53815-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53815-108">Remarks</span></span>  
 <span data-ttu-id="53815-109">`FLATTEN`patří mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="53815-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="53815-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="53815-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="53815-111">V tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) přednost informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="53815-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53815-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="53815-112">Example</span></span>  
 <span data-ttu-id="53815-113">Následující dotaz Entity SQL používá `FLATTEN` operátor převést na kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="53815-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="53815-114">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="53815-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="53815-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="53815-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="53815-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="53815-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="53815-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="53815-117">See Also</span></span>  
 [<span data-ttu-id="53815-118">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="53815-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
