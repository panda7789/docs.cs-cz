---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198401"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="9c545-101">Stav relace: odebrané zastaralé rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9c545-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="9c545-102">Odebrala se zastaralá rozhraní API pro konfiguraci souborů cookie relací.</span><span class="sxs-lookup"><span data-stu-id="9c545-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="9c545-103">Další informace najdete v tématu [ASPNET/oznámení # 257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="9c545-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9c545-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9c545-104">Version introduced</span></span>

<span data-ttu-id="9c545-105">3.0</span><span class="sxs-lookup"><span data-stu-id="9c545-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9c545-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9c545-106">Reason for change</span></span>

<span data-ttu-id="9c545-107">Tato změna vynutila konzistenci napříč rozhraními API pro konfiguraci funkcí, které používají soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="9c545-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9c545-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9c545-108">Recommended action</span></span>

<span data-ttu-id="9c545-109">Migrujte využití odebraných rozhraní API na jejich novější náhrady.</span><span class="sxs-lookup"><span data-stu-id="9c545-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="9c545-110">Vezměte v úvahu následující příklad v `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="9c545-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="9c545-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9c545-111">Category</span></span>

<span data-ttu-id="9c545-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c545-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9c545-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9c545-113">Affected APIs</span></span>

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
