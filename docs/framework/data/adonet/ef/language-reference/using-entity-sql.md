---
title: "POMOCÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d1a47102c7057918c981b53f920afef09b20afad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="using-entity-sql"></a><span data-ttu-id="41e82-102">POMOCÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="41e82-102">USING (Entity SQL)</span></span>
<span data-ttu-id="41e82-103">Určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="41e82-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e82-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="41e82-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="41e82-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="41e82-106">Určuje alias kratší ke kvalifikaci v oboru názvů s.</span><span class="sxs-lookup"><span data-stu-id="41e82-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="41e82-107">Libovolný platný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="41e82-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41e82-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e82-108">Example</span></span>  
 <span data-ttu-id="41e82-109">Následující dotaz Entity SQL pomocí operátoru USING zadejte oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="41e82-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="41e82-110">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="41e82-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="41e82-111">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="41e82-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="41e82-112">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="41e82-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="41e82-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="41e82-113">See Also</span></span>  
 [<span data-ttu-id="41e82-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="41e82-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="41e82-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="41e82-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
