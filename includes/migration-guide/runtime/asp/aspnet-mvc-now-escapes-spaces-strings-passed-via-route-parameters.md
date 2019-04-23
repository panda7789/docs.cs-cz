---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774252"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="c9bf1-101">ASP.NET MVC řídicí sekvence nyní mezery v řetězcích předaný prostřednictvím parametry trasy</span><span class="sxs-lookup"><span data-stu-id="c9bf1-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c9bf1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c9bf1-102">Details</span></span>|<span data-ttu-id="c9bf1-103">Aby bylo možné v souladu s RFC 2396 mezery v trasy cesty jsou nyní uvozeny řídicími znaky při naplňování parametry akce z trasy.</span><span class="sxs-lookup"><span data-stu-id="c9bf1-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="c9bf1-104">Tak že <code>/controller/action/some data</code> dříve odpovídá trase <code>/controller/action/{data}</code> a poskytují <code>some data</code> jako parametr data, se teď poskytují <code>some%20data</code> místo.</span><span class="sxs-lookup"><span data-stu-id="c9bf1-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="c9bf1-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c9bf1-105">Suggestion</span></span>|<span data-ttu-id="c9bf1-106">Kód by měl aktualizovat, aby unescape parametry řetězce z trasy.</span><span class="sxs-lookup"><span data-stu-id="c9bf1-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="c9bf1-107">V případě potřeby původní identifikátor URI lze přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c9bf1-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="c9bf1-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c9bf1-108">Scope</span></span>|<span data-ttu-id="c9bf1-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c9bf1-109">Minor</span></span>|
|<span data-ttu-id="c9bf1-110">Version</span><span class="sxs-lookup"><span data-stu-id="c9bf1-110">Version</span></span>|<span data-ttu-id="c9bf1-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c9bf1-111">4.5.2</span></span>|
|<span data-ttu-id="c9bf1-112">Type</span><span class="sxs-lookup"><span data-stu-id="c9bf1-112">Type</span></span>|<span data-ttu-id="c9bf1-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c9bf1-113">Runtime</span></span>|
|<span data-ttu-id="c9bf1-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c9bf1-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
