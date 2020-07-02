---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621967"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="e9178-101">ASP.NET parametr ValidationContext. member není NULL při použití vlastních DataAnnotations. ValidationAttribute</span><span class="sxs-lookup"><span data-stu-id="e9178-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="e9178-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e9178-102">Details</span></span>

<span data-ttu-id="e9178-103">V .NET Framework 4.7.2 a starších verzích při použití vlastní vlastnost se <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> vrátí `null` .</span><span class="sxs-lookup"><span data-stu-id="e9178-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="e9178-104">Ve verzi .NET Framework 4,8 před aktualizací z října 2019 vrátí název člena.</span><span class="sxs-lookup"><span data-stu-id="e9178-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="e9178-105">Počínaje [.NET Framework říjen 2019 Preview se souhrnem kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 vrátí `null` ve výchozím nastavení, ale můžete se přihlásit a místo toho vrátit název člena.</span><span class="sxs-lookup"><span data-stu-id="e9178-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e9178-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="e9178-106">Suggestion</span></span>

<span data-ttu-id="e9178-107">Přidejte následující nastavení do souboru *web.config* , aby vlastnost vrátila název člena v [.NET Framework říjnu 2019 Preview kumulativní kvality](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pro .NET Framework 4,8 a novější verze:</span><span class="sxs-lookup"><span data-stu-id="e9178-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="e9178-108">Ve verzi .NET Framework 4,8 před aktualizací z října 2019 je přidáním tohoto souboru do *web.config* obnoven předchozí chování a vrátí se vlastnost `null` .</span><span class="sxs-lookup"><span data-stu-id="e9178-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="e9178-109">Name</span><span class="sxs-lookup"><span data-stu-id="e9178-109">Name</span></span>    | <span data-ttu-id="e9178-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e9178-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e9178-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e9178-111">Scope</span></span>   |<span data-ttu-id="e9178-112">Není známo</span><span class="sxs-lookup"><span data-stu-id="e9178-112">Unknown</span></span>|
|<span data-ttu-id="e9178-113">Verze</span><span class="sxs-lookup"><span data-stu-id="e9178-113">Version</span></span>|<span data-ttu-id="e9178-114">4,8</span><span class="sxs-lookup"><span data-stu-id="e9178-114">4.8</span></span>|
|<span data-ttu-id="e9178-115">Typ</span><span class="sxs-lookup"><span data-stu-id="e9178-115">Type</span></span>|<span data-ttu-id="e9178-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e9178-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9178-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e9178-117">Affected APIs</span></span>

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
