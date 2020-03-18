---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393906"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="1496e-101">Ověřování: Podpis OAuthHandler ExchangeCodeAsync byl změněn.</span><span class="sxs-lookup"><span data-stu-id="1496e-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="1496e-102">V ASP.NET jádrem 3.0 `OAuthHandler.ExchangeCodeAsync` byl podpis změněn z:</span><span class="sxs-lookup"><span data-stu-id="1496e-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="1496e-103">Do:</span><span class="sxs-lookup"><span data-stu-id="1496e-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="1496e-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="1496e-104">Version introduced</span></span>

<span data-ttu-id="1496e-105">3.0</span><span class="sxs-lookup"><span data-stu-id="1496e-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1496e-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="1496e-106">Old behavior</span></span>

<span data-ttu-id="1496e-107">Řetězce `code` `redirectUri` a byly předány jako samostatné argumenty.</span><span class="sxs-lookup"><span data-stu-id="1496e-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1496e-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="1496e-108">New behavior</span></span>

<span data-ttu-id="1496e-109">`Code`a `RedirectUri` jsou `OAuthCodeExchangeContext` vlastnosti, které `OAuthCodeExchangeContext` lze nastavit prostřednictvím konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1496e-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="1496e-110">Nový `OAuthCodeExchangeContext` typ je jediným argumentem předanou společnosti `OAuthHandler.ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="1496e-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1496e-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="1496e-111">Reason for change</span></span>

<span data-ttu-id="1496e-112">Tato změna umožňuje další parametry, které mají být poskytnuty v nenarušující způsobem.</span><span class="sxs-lookup"><span data-stu-id="1496e-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="1496e-113">Není třeba vytvářet nové `ExchangeCodeAsync` přetížení.</span><span class="sxs-lookup"><span data-stu-id="1496e-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1496e-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1496e-114">Recommended action</span></span>

<span data-ttu-id="1496e-115">Vytvořte `OAuthCodeExchangeContext` s `code` příslušnými `redirectUri` a hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1496e-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="1496e-116">Musí <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> být poskytnuta instance.</span><span class="sxs-lookup"><span data-stu-id="1496e-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="1496e-117">Tato `OAuthCodeExchangeContext` jedna instance může `OAuthHandler.ExchangeCodeAsync` být předána namísto více argumentů.</span><span class="sxs-lookup"><span data-stu-id="1496e-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="1496e-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1496e-118">Category</span></span>

<span data-ttu-id="1496e-119">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1496e-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1496e-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1496e-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
