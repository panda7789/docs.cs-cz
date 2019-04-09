---
title: < (Menší než) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 0373dc2d066252d76cd3d4408790404ca70ab701
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105167"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="f63f1-102">\< (Méně než) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f63f1-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="f63f1-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu menší, než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="f63f1-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63f1-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f63f1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f63f1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f63f1-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="f63f1-106">Any valid expression.</span></span> <span data-ttu-id="f63f1-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="f63f1-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f63f1-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f63f1-108">Result Types</span></span>  
 `true` <span data-ttu-id="f63f1-109">Pokud levý výraz má hodnotu menší, než pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f63f1-109">if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f63f1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f63f1-110">Example</span></span>  
 <span data-ttu-id="f63f1-111">Následující dotaz Entity SQL používá < – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu menší, než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="f63f1-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="f63f1-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f63f1-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f63f1-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="f63f1-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f63f1-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f63f1-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f63f1-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f63f1-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="f63f1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f63f1-116">See also</span></span>

- [<span data-ttu-id="f63f1-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f63f1-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
