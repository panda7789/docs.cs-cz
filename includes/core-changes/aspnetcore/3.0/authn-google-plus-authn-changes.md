---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394238"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="f570e-101">Ověřování: Google+ se zastaral a nahrazuje</span><span class="sxs-lookup"><span data-stu-id="f570e-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="f570e-102">Google začíná [vypínat](https://developers.google.com/+/api-shutdown) Přihlášení google+ pro aplikace již v lednu 28, 2019.</span><span class="sxs-lookup"><span data-stu-id="f570e-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f570e-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="f570e-103">Change description</span></span>

<span data-ttu-id="f570e-104">ASP.NET 4.x a ASP.NET Core používají k ověřování uživatelů účtu Google ve webových aplikacích přihlašovací api služby Google+.</span><span class="sxs-lookup"><span data-stu-id="f570e-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="f570e-105">Ovlivněné balíčky NuGet jsou [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pro ASP.NET Core a `Microsoft.Owin` [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pro ASP.NET webových formulářů a MVC.</span><span class="sxs-lookup"><span data-stu-id="f570e-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="f570e-106">Náhradní api Společnosti Google používají jiný zdroj a formát dat.</span><span class="sxs-lookup"><span data-stu-id="f570e-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="f570e-107">Níže uvedená opatření ke zmírnění rizik a řešení mj.</span><span class="sxs-lookup"><span data-stu-id="f570e-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="f570e-108">Aplikace by měly ověřit, že samotná data stále splňují jejich požadavky.</span><span class="sxs-lookup"><span data-stu-id="f570e-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="f570e-109">Například jména, e-mailové adresy, odkazy na profil a profilové fotografie mohou poskytovat nenápadně odlišné hodnoty než dříve.</span><span class="sxs-lookup"><span data-stu-id="f570e-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f570e-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="f570e-110">Version introduced</span></span>

<span data-ttu-id="f570e-111">Všechny verze.</span><span class="sxs-lookup"><span data-stu-id="f570e-111">All versions.</span></span> <span data-ttu-id="f570e-112">Tato změna je externí pro ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="f570e-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f570e-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f570e-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="f570e-114">Owin s ASP.NET webovými formuláři a MVC</span><span class="sxs-lookup"><span data-stu-id="f570e-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="f570e-115">Pro `Microsoft.Owin` 3.1.0 a novější je [zde](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)uvedeno dočasné zmírnění .</span><span class="sxs-lookup"><span data-stu-id="f570e-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="f570e-116">Aplikace by měly dokončit testování s zmírnění mů e-li zkontrolovat změny ve formátu dat.</span><span class="sxs-lookup"><span data-stu-id="f570e-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="f570e-117">Existují plány `Microsoft.Owin` na vydání 4.0.1 s opravou.</span><span class="sxs-lookup"><span data-stu-id="f570e-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="f570e-118">Aplikace používající jakoukoli předchozí verzi by se měly aktualizovat na verzi 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="f570e-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="f570e-119">ASP.NET jádro 1.x</span><span class="sxs-lookup"><span data-stu-id="f570e-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="f570e-120">Zmírnění v [Owin u ASP.NET Web Forms a MVC](#owin-with-aspnet-web-forms-and-mvc) lze přizpůsobit ASP.NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="f570e-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="f570e-121">Opravy balíčků NuGet nejsou plánovány, protože 1.x dosáhl [stavu konce životnosti.](https://dotnet.microsoft.com/platform/support-policy)</span><span class="sxs-lookup"><span data-stu-id="f570e-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="f570e-122">ASP.NET Jádro 2.x</span><span class="sxs-lookup"><span data-stu-id="f570e-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="f570e-123">Pro `Microsoft.AspNetCore.Authentication.Google` verzi 2.x nahraďte `AddGoogle` `Startup.ConfigureServices` stávající volání do aplikace následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="f570e-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="f570e-124">Opravy z února 2.1 a 2.2 začlenili předchozí rekonfiguraci jako nové výchozí.</span><span class="sxs-lookup"><span data-stu-id="f570e-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="f570e-125">Žádná oprava je plánována pro ASP.NET Core 2.0, protože dosáhl [konce životnosti](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="f570e-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="f570e-126">ASP.NET jádro 3.0</span><span class="sxs-lookup"><span data-stu-id="f570e-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="f570e-127">Zmírnění uvedené pro ASP.NET Core 2.x lze také použít pro ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f570e-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="f570e-128">V budoucích náhledech 3.0 může být `Microsoft.AspNetCore.Authentication.Google` balíček odstraněn.</span><span class="sxs-lookup"><span data-stu-id="f570e-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="f570e-129">Uživatelé by `Microsoft.AspNetCore.Authentication.OpenIdConnect` místo toho byli přesměrováni.</span><span class="sxs-lookup"><span data-stu-id="f570e-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="f570e-130">Následující kód ukazuje, `AddGoogle` jak `AddOpenIdConnect` `Startup.ConfigureServices`nahradit v .</span><span class="sxs-lookup"><span data-stu-id="f570e-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="f570e-131">Tato náhrada může být použita s ASP.NET Core 2.0 a novějším a může být podle potřeby přizpůsobena pro ASP.NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="f570e-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="f570e-132">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f570e-132">Category</span></span>

<span data-ttu-id="f570e-133">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f570e-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f570e-134">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f570e-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
