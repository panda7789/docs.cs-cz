---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619927"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="1b2e8-101">ASP.NET MVC teď řídí mezery v řetězcích předaných přes parametry směrování.</span><span class="sxs-lookup"><span data-stu-id="1b2e8-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="1b2e8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1b2e8-102">Details</span></span>

<span data-ttu-id="1b2e8-103">Aby bylo možné odpovídat specifikaci RFC 2396, jsou nyní při naplňování parametrů akce z trasy řídicí prostory v cestách tras.</span><span class="sxs-lookup"><span data-stu-id="1b2e8-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="1b2e8-104">Takže, zatímco <code>/controller/action/some data</code> by dřív odpovídal trase <code>/controller/action/{data}</code> a poskytovala <code>some data</code> jako datový parametr, teď <code>some%20data</code> místo toho poskytne.</span><span class="sxs-lookup"><span data-stu-id="1b2e8-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1b2e8-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="1b2e8-105">Suggestion</span></span>

<span data-ttu-id="1b2e8-106">Kód by měl být aktualizován na parametry řetězce z trasy.</span><span class="sxs-lookup"><span data-stu-id="1b2e8-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="1b2e8-107">Pokud je nutný původní identifikátor URI, lze k němu přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri> . Rozhraní OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="1b2e8-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="1b2e8-108">Name</span><span class="sxs-lookup"><span data-stu-id="1b2e8-108">Name</span></span>    | <span data-ttu-id="1b2e8-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1b2e8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b2e8-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1b2e8-110">Scope</span></span>   |<span data-ttu-id="1b2e8-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="1b2e8-111">Minor</span></span>|
|<span data-ttu-id="1b2e8-112">Verze</span><span class="sxs-lookup"><span data-stu-id="1b2e8-112">Version</span></span>|<span data-ttu-id="1b2e8-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1b2e8-113">4.5.2</span></span>|
|<span data-ttu-id="1b2e8-114">Typ</span><span class="sxs-lookup"><span data-stu-id="1b2e8-114">Type</span></span>|<span data-ttu-id="1b2e8-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1b2e8-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b2e8-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1b2e8-116">Affected APIs</span></span>

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
