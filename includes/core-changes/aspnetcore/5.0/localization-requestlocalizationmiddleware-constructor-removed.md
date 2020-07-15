---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309139"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="03b92-101">Lokalizace: v middlewari pro lokalizaci požadavků byl odebrán zastaralý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="03b92-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="03b92-102"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Konstruktor, který postrádá parametr, <xref:Microsoft.Extensions.Logging.ILoggerFactory> byl [v tomto potvrzení](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)označen jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="03b92-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="03b92-103">V ASP.NET Core 5,0 byl odebrán zastaralý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="03b92-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="03b92-104">Diskuzi najdete v tématu [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="03b92-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03b92-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="03b92-105">Version introduced</span></span>

<span data-ttu-id="03b92-106">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="03b92-106">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="03b92-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="03b92-107">Old behavior</span></span>

<span data-ttu-id="03b92-108">Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor existuje.</span><span class="sxs-lookup"><span data-stu-id="03b92-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="03b92-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="03b92-109">New behavior</span></span>

<span data-ttu-id="03b92-110">Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="03b92-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="03b92-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="03b92-111">Reason for change</span></span>

<span data-ttu-id="03b92-112">Tato změna zajišťuje, že middleware lokalizace požadavků má vždycky přístup k protokolovacímu nástroje.</span><span class="sxs-lookup"><span data-stu-id="03b92-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03b92-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="03b92-113">Recommended action</span></span>

<span data-ttu-id="03b92-114">Při ruční konstrukci instance třídy `RequestLocalizationMiddleware` předejte `ILoggerFactory` instanci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="03b92-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="03b92-115">Pokud `ILoggerFactory` v tomto kontextu není k dispozici platná instance, zvažte předání konstruktoru middleware <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instanci.</span><span class="sxs-lookup"><span data-stu-id="03b92-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="03b92-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="03b92-116">Category</span></span>

<span data-ttu-id="03b92-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="03b92-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03b92-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="03b92-118">Affected APIs</span></span>

[<span data-ttu-id="03b92-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="03b92-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
