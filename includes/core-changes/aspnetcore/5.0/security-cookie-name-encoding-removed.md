---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401975"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="80dac-101">Zabezpečení: odebrání kódování názvu souboru cookie</span><span class="sxs-lookup"><span data-stu-id="80dac-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="80dac-102">[Standard souborů cookie protokolu HTTP](https://tools.ietf.org/html/rfc6265#section-4.1.1) umožňuje pouze konkrétní znaky v názvech souborů cookie a hodnotách.</span><span class="sxs-lookup"><span data-stu-id="80dac-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="80dac-103">Pro podporu nepovolených znaků ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="80dac-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="80dac-104">Při vytváření souboru cookie odpovědi se zakóduje.</span><span class="sxs-lookup"><span data-stu-id="80dac-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="80dac-105">Dekóduje při čtení souboru cookie žádosti.</span><span class="sxs-lookup"><span data-stu-id="80dac-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="80dac-106">V ASP.NET Core 5,0 se toto chování kódování změnilo v reakci na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80dac-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="80dac-107">Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="80dac-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="80dac-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="80dac-108">Version introduced</span></span>

<span data-ttu-id="80dac-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="80dac-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="80dac-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="80dac-110">Old behavior</span></span>

<span data-ttu-id="80dac-111">Názvy souborů cookie odpovědí jsou zakódovány.</span><span class="sxs-lookup"><span data-stu-id="80dac-111">Response cookie names are encoded.</span></span> <span data-ttu-id="80dac-112">Název souboru cookie žádosti je dekódovat.</span><span class="sxs-lookup"><span data-stu-id="80dac-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="80dac-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="80dac-113">New behavior</span></span>

<span data-ttu-id="80dac-114">Bylo odebráno kódování a dekódování názvů souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="80dac-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="80dac-115">Pro předchozí [podporované verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ASP.NET Core tým plánuje zmírnit problémy s dekódováním na místě.</span><span class="sxs-lookup"><span data-stu-id="80dac-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="80dac-116">Kromě toho volání <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> s neplatným názvem souboru cookie vyvolá výjimku typu <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="80dac-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="80dac-117">Kódování a dekódování hodnot souborů cookie zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="80dac-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="80dac-118">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="80dac-118">Reason for change</span></span>

<span data-ttu-id="80dac-119">Byl zjištěn problém ve [více webových rozhraních](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span><span class="sxs-lookup"><span data-stu-id="80dac-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="80dac-120">Kódování a dekódování může útočníkovi umožnit obejít funkci zabezpečení nazvanou [předpony souborů cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) pomocí zfalšovaných rezervovaných předpon, jako jsou `__Host-` například zakódované hodnoty `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="80dac-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="80dac-121">Útok vyžaduje sekundární zneužití pro vložení zfalšovaných souborů cookie, jako je například zranitelnost mezi lokalitami (XSS), na webu.</span><span class="sxs-lookup"><span data-stu-id="80dac-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="80dac-122">Tyto předpony se ve výchozím nastavení nepoužívají v ASP.NET Core `Microsoft.Owin` knihoven nebo šablonách.</span><span class="sxs-lookup"><span data-stu-id="80dac-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="80dac-123">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="80dac-123">Recommended action</span></span>

<span data-ttu-id="80dac-124">Pokud přesouváte projekty na ASP.NET Core 5,0 nebo novější, ujistěte se, že názvy jejich souborů cookie odpovídají [požadavkům specifikace tokenů](https://tools.ietf.org/html/rfc2616#section-2.2): znaky ASCII bez ovládacích prvků a oddělovačů `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="80dac-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="80dac-125">Použití jiných znaků než ASCII v názvech souborů cookie nebo jiných hlaviček protokolu HTTP může způsobit výjimku ze serveru nebo nesprávně Trip klientovi.</span><span class="sxs-lookup"><span data-stu-id="80dac-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="80dac-126">Kategorie</span><span class="sxs-lookup"><span data-stu-id="80dac-126">Category</span></span>

<span data-ttu-id="80dac-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="80dac-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80dac-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="80dac-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
