---
title: Funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: f31f829b53160da5a043617b9aa999b398859f17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034161"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="f1776-102">Funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f1776-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="f1776-103">Entita SQL podporuje uživatelem definované funkce, kanonické funkce a funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f1776-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="f1776-104">Uživatelem definované funkce jsou určené v konceptuálním modelu nebo vložené v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f1776-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="f1776-105">Další informace najdete v tématu [uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f1776-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f1776-106">Kanonické funkce jsou předdefinovány v Entity Framework a poskytovateli dat by měla podporovat.</span><span class="sxs-lookup"><span data-stu-id="f1776-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="f1776-107">Příkazy SQL entity se nezdaří, pokud uživatel volá funkci, která není podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="f1776-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="f1776-108">Proto kanonické funkce se obecně doporučují prostřednictvím funkce specifické pro úložiště, které jsou v oboru názvů specifickým pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f1776-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="f1776-109">Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f1776-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="f1776-110">Spravovat zprostředkovatele klienta Microsoft SQL poskytuje sadu funkcí specifickým pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f1776-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="f1776-111">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f1776-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1776-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f1776-112">In This Section</span></span>  
 [<span data-ttu-id="f1776-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="f1776-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="f1776-114">Řešení přetížení funkce</span><span class="sxs-lookup"><span data-stu-id="f1776-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="f1776-115">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="f1776-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1776-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1776-116">See also</span></span>

- [<span data-ttu-id="f1776-117">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f1776-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
