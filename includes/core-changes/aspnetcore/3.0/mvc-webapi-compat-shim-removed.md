---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393941"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="3a648-101">MVC: překrytí kompatibility webového rozhraní API se odebralo.</span><span class="sxs-lookup"><span data-stu-id="3a648-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="3a648-102">Počínaje verzí ASP.NET Core 3,0 není balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3a648-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a648-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="3a648-103">Change description</span></span>

<span data-ttu-id="3a648-104">Balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) poskytuje částečnou kompatibilitu v ASP.NET Core s webovým rozhraním API 2 ASP.NET 4. x pro zjednodušení migrace stávajících implementací webového rozhraní API na ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a648-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="3a648-105">Aplikace, které používají WebApiCompatShim, ale netěží z funkcí souvisejících s rozhraním API, které se dodávají v posledních ASP.NET Core verzích.</span><span class="sxs-lookup"><span data-stu-id="3a648-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="3a648-106">Mezi tyto funkce patří vylepšené generování specifikace Open API, standardizované zpracování chyb a generování kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="3a648-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="3a648-107">Aby se zajistilo lepší zaměření na úsilí rozhraní API v 3,0, odebral se WebApiCompatShim.</span><span class="sxs-lookup"><span data-stu-id="3a648-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="3a648-108">Stávající aplikace, které používají WebApiCompatShim, by se měly migrovat na novější model `[ApiController]`.</span><span class="sxs-lookup"><span data-stu-id="3a648-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a648-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3a648-109">Version introduced</span></span>

<span data-ttu-id="3a648-110">3.0</span><span class="sxs-lookup"><span data-stu-id="3a648-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a648-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="3a648-111">Reason for change</span></span>

<span data-ttu-id="3a648-112">Překrytí kompatibility webového rozhraní API je nástroj pro migraci.</span><span class="sxs-lookup"><span data-stu-id="3a648-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="3a648-113">Omezuje přístup uživatelů k novým funkcím přidaným v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a648-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a648-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3a648-114">Recommended action</span></span>

<span data-ttu-id="3a648-115">Odeberte použití tohoto překrytí a přímo se migrujte na podobné funkce v ASP.NET Core samotné.</span><span class="sxs-lookup"><span data-stu-id="3a648-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="3a648-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3a648-116">Category</span></span>

<span data-ttu-id="3a648-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a648-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a648-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3a648-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
