---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394238"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="b12cb-101">Ověřování: Google + zastaralé a nahrazené</span><span class="sxs-lookup"><span data-stu-id="b12cb-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="b12cb-102">Google se zahájí [vypnutí](https://developers.google.com/+/api-shutdown) služby Google + Sign-in pro aplikace hned po 28. lednu 2019.</span><span class="sxs-lookup"><span data-stu-id="b12cb-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b12cb-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="b12cb-103">Change description</span></span>

<span data-ttu-id="b12cb-104">ASP.NET 4. x a ASP.NET Core používaly rozhraní API pro přihlašování Google + k ověřování uživatelů účtu Google ve službě Web Apps.</span><span class="sxs-lookup"><span data-stu-id="b12cb-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="b12cb-105">Ovlivněné balíčky NuGet jsou [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pro ASP.NET Core a [Microsoft. Owin. Security. Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pro `Microsoft.Owin` s ASP.NET webovými formuláři a MVC.</span><span class="sxs-lookup"><span data-stu-id="b12cb-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="b12cb-106">Rozhraní API pro nahrazení Google používají jiný zdroj dat a formát.</span><span class="sxs-lookup"><span data-stu-id="b12cb-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="b12cb-107">Rizika a řešení uvedená níže jsou k dispozici pro strukturální změny.</span><span class="sxs-lookup"><span data-stu-id="b12cb-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="b12cb-108">Aplikace by měly ověřit, že samotná data stále splňují jejich požadavky.</span><span class="sxs-lookup"><span data-stu-id="b12cb-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="b12cb-109">Například názvy, e-mailové adresy, odkazy na profily a profily profilů můžou poskytovat nepřesné odlišné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b12cb-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b12cb-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b12cb-110">Version introduced</span></span>

<span data-ttu-id="b12cb-111">Všechny verze.</span><span class="sxs-lookup"><span data-stu-id="b12cb-111">All versions.</span></span> <span data-ttu-id="b12cb-112">Tato změna je externě ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b12cb-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b12cb-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b12cb-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="b12cb-114">Owin s webovými formuláři ASP.NET a MVC</span><span class="sxs-lookup"><span data-stu-id="b12cb-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="b12cb-115">V případě `Microsoft.Owin` 3.1.0 a novějšího je [zde](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)popsaný dočasný dopad.</span><span class="sxs-lookup"><span data-stu-id="b12cb-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="b12cb-116">Aplikace by měly dokončit testování s rizikem, aby kontrolovaly změny ve formátu dat.</span><span class="sxs-lookup"><span data-stu-id="b12cb-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="b12cb-117">K dispozici jsou plány pro vydání `Microsoft.Owin` 4.0.1 s opravou.</span><span class="sxs-lookup"><span data-stu-id="b12cb-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="b12cb-118">Aplikace používající jakoukoli předchozí verzi by se měly aktualizovat na verzi 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="b12cb-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="b12cb-119">ASP.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="b12cb-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="b12cb-120">Zmírnění rizika v [Owin s webovými formuláři ASP.NET a MVC](#owin-with-aspnet-web-forms-and-mvc) se dá přizpůsobit ASP.NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="b12cb-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="b12cb-121">Opravy balíčků NuGet nejsou plánované, protože 1. x dosáhlo stavu [konce životnosti](https://dotnet.microsoft.com/platform/support-policy) .</span><span class="sxs-lookup"><span data-stu-id="b12cb-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="b12cb-122">ASP.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="b12cb-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="b12cb-123">U `Microsoft.AspNetCore.Authentication.Google` verze 2. x nahraďte existující volání `AddGoogle` v `Startup.ConfigureServices` následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b12cb-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

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

<span data-ttu-id="b12cb-124">Opravy z února 2,1 a 2,2 zahrnovaly předchozí znovu konfiguraci jako nové výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="b12cb-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="b12cb-125">Pro ASP.NET Core 2,0 není plánována žádná oprava, protože dosáhla [konce životnosti](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="b12cb-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="b12cb-126">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="b12cb-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="b12cb-127">Zmírnění rizika poskytnutého ASP.NET Core 2. x se dá použít i pro ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b12cb-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="b12cb-128">V budoucích verzích 3,0 verze Preview může být balíček `Microsoft.AspNetCore.Authentication.Google` odebraný.</span><span class="sxs-lookup"><span data-stu-id="b12cb-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="b12cb-129">Místo toho budou uživatelé přesměrováni na `Microsoft.AspNetCore.Authentication.OpenIdConnect`.</span><span class="sxs-lookup"><span data-stu-id="b12cb-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="b12cb-130">Následující kód ukazuje, jak nahradit `AddGoogle` s `AddOpenIdConnect` v `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="b12cb-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="b12cb-131">Tato náhrada se dá použít s ASP.NET Core 2,0 a novějším a dá se podle potřeby přizpůsobit pro ASP.NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="b12cb-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

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

#### <a name="category"></a><span data-ttu-id="b12cb-132">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b12cb-132">Category</span></span>

<span data-ttu-id="b12cb-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b12cb-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b12cb-134">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b12cb-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
