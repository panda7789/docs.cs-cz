---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803218"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="ffe82-101">ASP.NET MVC nyní uniká mezery v řetězcích předávaných parametry trasy</span><span class="sxs-lookup"><span data-stu-id="ffe82-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ffe82-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ffe82-102">Details</span></span>|<span data-ttu-id="ffe82-103">Aby bylo možné vyhovět RFC 2396, mezery v trasách trasy jsou nyní uvozeny při vyplnění parametrů akce z trasy.</span><span class="sxs-lookup"><span data-stu-id="ffe82-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="ffe82-104">Takže vzhledem <code>/controller/action/some data</code> k tomu, <code>/controller/action/{data}</code> že <code>some data</code> by dříve odpovídat postupu <code>some%20data</code> a poskytnout jako parametr data, bude nyní poskytovat místo.</span><span class="sxs-lookup"><span data-stu-id="ffe82-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="ffe82-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="ffe82-105">Suggestion</span></span>|<span data-ttu-id="ffe82-106">Kód by měl být aktualizován na unescape parametry řetězce z trasy.</span><span class="sxs-lookup"><span data-stu-id="ffe82-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="ffe82-107">Pokud je potřeba původní identifikátor URI, lze <xref:System.Net.HttpWebRequest.RequestUri>k němu přistupovat pomocí . OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="ffe82-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="ffe82-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ffe82-108">Scope</span></span>|<span data-ttu-id="ffe82-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="ffe82-109">Minor</span></span>|
|<span data-ttu-id="ffe82-110">Version</span><span class="sxs-lookup"><span data-stu-id="ffe82-110">Version</span></span>|<span data-ttu-id="ffe82-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="ffe82-111">4.5.2</span></span>|
|<span data-ttu-id="ffe82-112">Typ</span><span class="sxs-lookup"><span data-stu-id="ffe82-112">Type</span></span>|<span data-ttu-id="ffe82-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ffe82-113">Runtime</span></span>|
|<span data-ttu-id="ffe82-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ffe82-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
