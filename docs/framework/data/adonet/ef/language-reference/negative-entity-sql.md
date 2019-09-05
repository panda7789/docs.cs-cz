---
title: '- Příznivé (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: effd537bcd53052830f2195e18ca959b49d87255
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249928"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="6cfb2-102">-(Negativní) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6cfb2-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="6cfb2-103">Vrátí záporné hodnoty číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cfb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cfb2-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6cfb2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6cfb2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6cfb2-106">Libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6cfb2-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="6cfb2-107">Result Types</span></span>  
 <span data-ttu-id="6cfb2-108">Datový typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cfb2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cfb2-109">Remarks</span></span>  
 <span data-ttu-id="6cfb2-110">Pokud `expression` je typ bez znaménka, typ výsledku bude podepsaný typ, který se nejvíce blíží `expression`typu.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="6cfb2-111">Například pokud `expression` je typu Byte, bude vrácena hodnota typu Int16.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cfb2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cfb2-112">Example</span></span>  
 <span data-ttu-id="6cfb2-113">Následující Entity SQL dotaz pomocí operátoru-aritmetické operace vrátí záporné hodnoty číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="6cfb2-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6cfb2-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6cfb2-116">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="6cfb2-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6cfb2-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="6cfb2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cfb2-118">See also</span></span>

- [<span data-ttu-id="6cfb2-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6cfb2-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
