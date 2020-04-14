---
ms.openlocfilehash: 7444ddbdd4a7c5f731fba8528ee2334374fc254e
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275097"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="a69d5-101">ASP.NET MVC nyní uniká mezery v řetězcích předávaných parametry trasy</span><span class="sxs-lookup"><span data-stu-id="a69d5-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a69d5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a69d5-102">Details</span></span>|<span data-ttu-id="a69d5-103">Aby bylo možné vyhovět RFC 2396, mezery v trasách trasy jsou nyní uvozeny při vyplnění parametrů akce z trasy.</span><span class="sxs-lookup"><span data-stu-id="a69d5-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="a69d5-104">Takže vzhledem <code>/controller/action/some data</code> k tomu, <code>/controller/action/{data}</code> že <code>some data</code> by dříve odpovídat postupu <code>some%20data</code> a poskytnout jako parametr data, bude nyní poskytovat místo.</span><span class="sxs-lookup"><span data-stu-id="a69d5-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="a69d5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="a69d5-105">Suggestion</span></span>|<span data-ttu-id="a69d5-106">Kód by měl být aktualizován na unescape parametry řetězce z trasy.</span><span class="sxs-lookup"><span data-stu-id="a69d5-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="a69d5-107">Pokud je potřeba původní identifikátor URI, lze <xref:System.Net.HttpWebRequest.RequestUri>k němu přistupovat pomocí . OriginalString API.</span><span class="sxs-lookup"><span data-stu-id="a69d5-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="a69d5-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a69d5-108">Scope</span></span>|<span data-ttu-id="a69d5-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="a69d5-109">Minor</span></span>|
|<span data-ttu-id="a69d5-110">Version</span><span class="sxs-lookup"><span data-stu-id="a69d5-110">Version</span></span>|<span data-ttu-id="a69d5-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="a69d5-111">4.5.2</span></span>|
|<span data-ttu-id="a69d5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="a69d5-112">Type</span></span>|<span data-ttu-id="a69d5-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a69d5-113">Runtime</span></span>|
|<span data-ttu-id="a69d5-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a69d5-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
