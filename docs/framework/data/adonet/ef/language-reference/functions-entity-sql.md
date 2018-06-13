---
title: Funkce (entita SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: 6c8a44a4e347ffabd665847f02bfafe267a14103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760294"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="f896a-102">Funkce (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f896a-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="f896a-103">Entity SQL podporuje uživatelsky definované funkce, kanonické funkce a funkce specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f896a-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="f896a-104">Uživatelem definované funkce jsou určené v konceptuální model, nebo vložené v dotazu.</span><span class="sxs-lookup"><span data-stu-id="f896a-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="f896a-105">Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f896a-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f896a-106">Kanonické funkce předdefinovaných rozhraní Entity Framework a by měl být podporovaných poskytovateli data.</span><span class="sxs-lookup"><span data-stu-id="f896a-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="f896a-107">Příkazy SQL entity se nezdaří, pokud uživatel volá funkci, která není podporována zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="f896a-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="f896a-108">Proto kanonické funkce jsou obecně doporučuje namísto úložiště specifické funkce, které jsou v oboru názvů specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f896a-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="f896a-109">Další informace najdete v tématu [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f896a-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="f896a-110">Zprostředkovatele služby Microsoft SQL klienta spravovaný poskytuje sadu funkcí specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f896a-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="f896a-111">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f896a-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f896a-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f896a-112">In This Section</span></span>  
 [<span data-ttu-id="f896a-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="f896a-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="f896a-114">Řešení přetížení funkce</span><span class="sxs-lookup"><span data-stu-id="f896a-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="f896a-115">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="f896a-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="f896a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f896a-116">See Also</span></span>  
 [<span data-ttu-id="f896a-117">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f896a-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
