---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393941"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="5bd69-101">MVC: Překrytí kompatibility webového rozhraní byla odstraněna.</span><span class="sxs-lookup"><span data-stu-id="5bd69-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="5bd69-102">Počínaje ASP.NET Core 3.0, balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5bd69-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5bd69-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5bd69-103">Change description</span></span>

<span data-ttu-id="5bd69-104">Balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) poskytuje částečnou kompatibilitu v ASP.NET Core s ASP.NET 4.x Web API 2 pro zjednodušení migrace existujících implementací webového rozhraní API pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bd69-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="5bd69-105">Aplikace používající WebApiCompatShim však nemají prospěch z funkcí souvisejících s rozhraním API, které jsou dodávány v posledních ASP.NET vydánícore.</span><span class="sxs-lookup"><span data-stu-id="5bd69-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="5bd69-106">Mezi tyto funkce patří vylepšené generování specifikace Open API, standardizované zpracování chyb a generování kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd69-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="5bd69-107">Chcete-li lépe zaměřit úsilí rozhraní API v 3.0, WebApiCompatShim byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="5bd69-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="5bd69-108">Existující aplikace používající WebApiCompatShim by `[ApiController]` měly migrovat na novější model.</span><span class="sxs-lookup"><span data-stu-id="5bd69-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5bd69-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="5bd69-109">Version introduced</span></span>

<span data-ttu-id="5bd69-110">3.0</span><span class="sxs-lookup"><span data-stu-id="5bd69-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5bd69-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="5bd69-111">Reason for change</span></span>

<span data-ttu-id="5bd69-112">Překrytí kompatibility webového rozhraní API byl nástroj pro migraci.</span><span class="sxs-lookup"><span data-stu-id="5bd69-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="5bd69-113">Omezuje přístup uživatelů k novým funkcím přidaným v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bd69-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5bd69-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5bd69-114">Recommended action</span></span>

<span data-ttu-id="5bd69-115">Odeberte použití této překrytí a migrujte přímo na podobné funkce v ASP.NET samotnéjádro.</span><span class="sxs-lookup"><span data-stu-id="5bd69-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="5bd69-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5bd69-116">Category</span></span>

<span data-ttu-id="5bd69-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bd69-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5bd69-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5bd69-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
