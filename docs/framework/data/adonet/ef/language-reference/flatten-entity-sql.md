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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 44abbcf90ec2607824d75ce89284c356e6096af2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="23691-102">VYROVNÁNÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="23691-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="23691-103">Převede kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="23691-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="23691-104">Nová kolekce obsahuje všechny stejné prvky, jako původní kolekce, ale bez vnořené struktury.</span><span class="sxs-lookup"><span data-stu-id="23691-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23691-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23691-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="23691-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="23691-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="23691-107">Libovolný platný výraz, který vrátí kolekce hodnota kolekcí k vyrovnání do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="23691-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23691-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23691-108">Remarks</span></span>  
 <span data-ttu-id="23691-109">`FLATTEN`patří mezi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="23691-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="23691-110">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="23691-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="23691-111">V tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) přednost informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="23691-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23691-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="23691-112">Example</span></span>  
 <span data-ttu-id="23691-113">Následující dotaz Entity SQL používá `FLATTEN` operátor převést na kolekci plochou kolekce kolekcí.</span><span class="sxs-lookup"><span data-stu-id="23691-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="23691-114">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="23691-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="23691-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="23691-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="23691-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="23691-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="23691-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="23691-117">See Also</span></span>  
 [<span data-ttu-id="23691-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="23691-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
