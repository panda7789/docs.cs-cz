---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281334"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="c7844-101">Lokalizace: v middlewari pro lokalizaci požadavků byl odebrán zastaralý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c7844-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="c7844-102"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Konstruktor, který postrádá parametr, <xref:Microsoft.Extensions.Logging.ILoggerFactory> byl [v tomto potvrzení](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)označen jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="c7844-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="c7844-103">V ASP.NET Core 5,0 byl odebrán zastaralý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c7844-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="c7844-104">Diskuzi najdete v tématu [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="c7844-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c7844-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="c7844-105">Version introduced</span></span>

<span data-ttu-id="c7844-106">5.0</span><span class="sxs-lookup"><span data-stu-id="c7844-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c7844-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="c7844-107">Old behavior</span></span>

<span data-ttu-id="c7844-108">Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor existuje.</span><span class="sxs-lookup"><span data-stu-id="c7844-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c7844-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="c7844-109">New behavior</span></span>

<span data-ttu-id="c7844-110">Zastaralý `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` konstruktor neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c7844-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c7844-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="c7844-111">Reason for change</span></span>

<span data-ttu-id="c7844-112">Tato změna zajišťuje, že middleware lokalizace požadavků má vždycky přístup k protokolovacímu nástroje.</span><span class="sxs-lookup"><span data-stu-id="c7844-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c7844-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c7844-113">Recommended action</span></span>

<span data-ttu-id="c7844-114">Při ruční konstrukci instance třídy `RequestLocalizationMiddleware` předejte `ILoggerFactory` instanci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7844-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="c7844-115">Pokud `ILoggerFactory` v tomto kontextu není k dispozici platná instance, zvažte předání konstruktoru middleware <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instanci.</span><span class="sxs-lookup"><span data-stu-id="c7844-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="c7844-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c7844-116">Category</span></span>

<span data-ttu-id="c7844-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c7844-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7844-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c7844-118">Affected APIs</span></span>

[<span data-ttu-id="c7844-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="c7844-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
