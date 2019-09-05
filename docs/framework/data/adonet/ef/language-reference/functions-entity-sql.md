---
title: Funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250908"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="4594c-102">Funkce (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4594c-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="4594c-103">Entity SQL podporuje uživatelsky definované funkce, kanonické funkce a funkce specifické pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="4594c-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="4594c-104">Uživatelsky definované funkce jsou zadány v koncepčním modelu nebo vloženém v dotazu.</span><span class="sxs-lookup"><span data-stu-id="4594c-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="4594c-105">Další informace najdete v tématu [uživatelsky definované funkce](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4594c-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="4594c-106">Kanonické funkce jsou předdefinované v Entity Framework a měly by být podporovány poskytovateli dat.</span><span class="sxs-lookup"><span data-stu-id="4594c-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="4594c-107">Entity SQL příkazy selžou, pokud uživatel zavolá funkci, která není zprostředkovatelem podporována.</span><span class="sxs-lookup"><span data-stu-id="4594c-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="4594c-108">Kanonické funkce jsou proto obecně doporučovány přes funkce specifické pro úložiště, které jsou v oboru názvů specifického pro konkrétního zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="4594c-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="4594c-109">Další informace najdete v tématu [kanonické funkce](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4594c-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="4594c-110">Spravovaný zprostředkovatel klienta Microsoft SQL nabízí sadu funkcí specifických pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="4594c-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="4594c-111">Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4594c-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4594c-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4594c-112">In This Section</span></span>  
 [<span data-ttu-id="4594c-113">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="4594c-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="4594c-114">Řešení přetížení funkce</span><span class="sxs-lookup"><span data-stu-id="4594c-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="4594c-115">Agregační funkce</span><span class="sxs-lookup"><span data-stu-id="4594c-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="4594c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4594c-116">See also</span></span>

- [<span data-ttu-id="4594c-117">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4594c-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
