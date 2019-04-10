---
title: '- (Negativní) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 6e5512546faeaa9760dcf135165a999a6f95322b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311003"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="9ca0e-102">-(Záporné) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9ca0e-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="9ca0e-103">Vrátí negativní hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca0e-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ca0e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9ca0e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9ca0e-106">Libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9ca0e-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="9ca0e-107">Result Types</span></span>  
 <span data-ttu-id="9ca0e-108">Datový typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ca0e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ca0e-109">Remarks</span></span>  
 <span data-ttu-id="9ca0e-110">Pokud `expression` je typ bez znaménka typu výsledku bude typ se znaménkem, který nejlépe odpovídá typu `expression`.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="9ca0e-111">Například pokud `expression` je typu Byte, hodnota typu Int16 bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ca0e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ca0e-112">Example</span></span>  
 <span data-ttu-id="9ca0e-113">Pomocí následujícího dotazu Entity SQL-aritmetického operátoru vrátit negativní hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="9ca0e-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9ca0e-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9ca0e-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="9ca0e-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9ca0e-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9ca0e-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9ca0e-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="9ca0e-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="9ca0e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ca0e-118">See also</span></span>

- [<span data-ttu-id="9ca0e-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9ca0e-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
