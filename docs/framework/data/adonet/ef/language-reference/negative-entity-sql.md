---
title: '- Příznivé (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319528"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="4c3f9-102">-(Negativní) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4c3f9-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="4c3f9-103">Vrátí záporné hodnoty číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c3f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c3f9-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c3f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4c3f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4c3f9-106">Libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4c3f9-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="4c3f9-107">Result Types</span></span>  
 <span data-ttu-id="4c3f9-108">Datový typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c3f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c3f9-109">Remarks</span></span>  
 <span data-ttu-id="4c3f9-110">Pokud je `expression` typ bez znaménka, typ výsledku bude podepsaný typ, který se nejvíce blíží typu `expression`.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="4c3f9-111">Například pokud je `expression` typu Byte, bude vrácena hodnota typu Int16.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c3f9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c3f9-112">Example</span></span>  
 <span data-ttu-id="4c3f9-113">Následující Entity SQL dotaz pomocí operátoru-aritmetické operace vrátí záporné hodnoty číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="4c3f9-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4c3f9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4c3f9-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="4c3f9-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4c3f9-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4c3f9-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4c3f9-117">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4c3f9-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="4c3f9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c3f9-118">See also</span></span>

- [<span data-ttu-id="4c3f9-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4c3f9-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
