---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198401"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="08f00-101">Stav relace: Odebraná zastaralá api</span><span class="sxs-lookup"><span data-stu-id="08f00-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="08f00-102">Zastaralá nastavení API pro konfiguraci souborů cookie relace byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="08f00-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="08f00-103">Další informace naleznete [v tématu aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="08f00-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08f00-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="08f00-104">Version introduced</span></span>

<span data-ttu-id="08f00-105">3.0</span><span class="sxs-lookup"><span data-stu-id="08f00-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="08f00-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="08f00-106">Reason for change</span></span>

<span data-ttu-id="08f00-107">Tato změna vynucuje konzistenci mezi api pro konfiguraci funkcí, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="08f00-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08f00-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="08f00-108">Recommended action</span></span>

<span data-ttu-id="08f00-109">Migrujte použití odebraných api do jejich novějších náhrad.</span><span class="sxs-lookup"><span data-stu-id="08f00-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="08f00-110">Vezměme si `Startup.ConfigureServices`následující příklad v :</span><span class="sxs-lookup"><span data-stu-id="08f00-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(ServiceCollection services)
{
    services.AddSession(options =>
    {
        // Removed obsolete APIs
        options.CookieName = "SessionCookie";
        options.CookieDomain = "contoso.com";
        options.CookiePath = "/";
        options.CookieHttpOnly = true;
        options.CookieSecure = CookieSecurePolicy.Always;

        // new API
        options.Cookie.Name = "SessionCookie";
        options.Cookie.Domain = "contoso.com";
        options.Cookie.Path = "/";
        options.Cookie.HttpOnly = true;
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    });
}
```

#### <a name="category"></a><span data-ttu-id="08f00-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="08f00-111">Category</span></span>

<span data-ttu-id="08f00-112">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="08f00-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08f00-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="08f00-113">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure?displayProperty=fullName>

<!-- 

#### Affected APIs

- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieName`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure`

-->
