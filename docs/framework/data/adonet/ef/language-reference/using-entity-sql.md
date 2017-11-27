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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c506484908d6b0ffe3a11e33b51d0bcc2d27c25c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-entity-sql"></a><span data-ttu-id="00100-102">POMOCÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="00100-102">USING (Entity SQL)</span></span>
<span data-ttu-id="00100-103">Určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="00100-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00100-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00100-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="00100-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="00100-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="00100-106">Určuje alias kratší ke kvalifikaci v oboru názvů s.</span><span class="sxs-lookup"><span data-stu-id="00100-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="00100-107">Libovolný platný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="00100-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00100-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="00100-108">Example</span></span>  
 <span data-ttu-id="00100-109">Následující dotaz Entity SQL pomocí operátoru USING zadejte oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="00100-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="00100-110">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="00100-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="00100-111">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="00100-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="00100-112">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="00100-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="00100-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="00100-113">See Also</span></span>  
 [<span data-ttu-id="00100-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="00100-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="00100-115">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="00100-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
