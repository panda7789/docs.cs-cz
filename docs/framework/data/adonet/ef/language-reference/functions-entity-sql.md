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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 11ce680f4a240c82b51b1651886e39d829976e84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functions-entity-sql"></a><span data-ttu-id="18b5f-102">Funkce (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="18b5f-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="18b5f-103">Entity SQL podporuje uživatelsky definované funkce, kanonické funkce a funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="18b5f-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="18b5f-104">Uživatelem definované funkce jsou určené v konceptuální model, nebo vložené v dotazu.</span><span class="sxs-lookup"><span data-stu-id="18b5f-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="18b5f-105">Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="18b5f-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="18b5f-106">Kanonické funkce předdefinovaných rozhraní Entity Framework a by měl být podporovaných poskytovateli data.</span><span class="sxs-lookup"><span data-stu-id="18b5f-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="18b5f-107">Příkazy SQL entity se nezdaří, pokud uživatel volá funkci, která není podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="18b5f-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="18b5f-108">Proto kanonické funkce jsou obecně doporučuje namísto úložiště specifické funkce, které jsou v oboru názvů specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="18b5f-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="18b5f-109">Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="18b5f-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="18b5f-110">Zprostředkovatele služby Microsoft SQL klienta spravovaný poskytuje sadu funkcí specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="18b5f-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="18b5f-111">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="18b5f-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18b5f-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18b5f-112">In This Section</span></span>  
 [<span data-ttu-id="18b5f-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="18b5f-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="18b5f-114">Řešení přetížení funkce</span><span class="sxs-lookup"><span data-stu-id="18b5f-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="18b5f-115">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="18b5f-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="18b5f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="18b5f-116">See Also</span></span>  
 [<span data-ttu-id="18b5f-117">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="18b5f-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
