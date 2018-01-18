---
title: Funkce (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9008360a4af0a669a223a2e56ee5152b23c6ebe4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="functions-entity-sql"></a><span data-ttu-id="d5765-102">Funkce (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="d5765-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="d5765-103">Entity SQL podporuje uživatelsky definované funkce, kanonické funkce a funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d5765-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="d5765-104">Uživatelem definované funkce jsou určené v konceptuální model, nebo vložené v dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5765-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="d5765-105">Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d5765-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="d5765-106">Kanonické funkce předdefinovaných rozhraní Entity Framework a by měl být podporovaných poskytovateli data.</span><span class="sxs-lookup"><span data-stu-id="d5765-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="d5765-107">Příkazy SQL entity se nezdaří, pokud uživatel volá funkci, která není podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="d5765-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="d5765-108">Proto kanonické funkce jsou obecně doporučuje namísto úložiště specifické funkce, které jsou v oboru názvů specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d5765-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="d5765-109">Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d5765-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="d5765-110">Zprostředkovatele služby Microsoft SQL klienta spravovaný poskytuje sadu funkcí specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d5765-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="d5765-111">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d5765-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5765-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5765-112">In This Section</span></span>  
 [<span data-ttu-id="d5765-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="d5765-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="d5765-114">Řešení přetížení funkce</span><span class="sxs-lookup"><span data-stu-id="d5765-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="d5765-115">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="d5765-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="d5765-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5765-116">See Also</span></span>  
 [<span data-ttu-id="d5765-117">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d5765-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
