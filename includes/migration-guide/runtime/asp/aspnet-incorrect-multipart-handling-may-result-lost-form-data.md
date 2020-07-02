---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621968"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="00df5-101">ASP.NET nesprávné zpracování více částí může způsobit ztrátu dat z formuláře.</span><span class="sxs-lookup"><span data-stu-id="00df5-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="00df5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="00df5-102">Details</span></span>

<span data-ttu-id="00df5-103">V aplikacích, které cílí na .NET Framework 4.7.2 a starších verzí, může ASP.Net nesprávně analyzovat hodnoty mezních hodnot v částech, takže během provádění žádosti nejsou dostupná data formuláře.</span><span class="sxs-lookup"><span data-stu-id="00df5-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="00df5-104">Aplikace, které cílí na .NET Framework 4,8 nebo novější verze správně analyzují data ze všech částí, takže hodnoty formulářů jsou k dispozici během provádění žádosti.</span><span class="sxs-lookup"><span data-stu-id="00df5-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00df5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="00df5-105">Suggestion</span></span>

<span data-ttu-id="00df5-106">Počínaje aplikacemi, které běží na .NET Framework 4,8, při cílení .NET Framework 4,8 nebo novějším pomocí <code>targetFrameworkVersion</code> elementu se výchozí chování změní na oddělovače pruhů.</span><span class="sxs-lookup"><span data-stu-id="00df5-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="00df5-107">Když cílíte na předchozí verze rozhraní nebo nepoužíváte <code>targetFrameworkVersion</code> , koncové oddělovače pro některé hodnoty se pořád vrátí. Toto chování je možné také explicitně řídit pomocí <code>appSetting</code> :</span><span class="sxs-lookup"><span data-stu-id="00df5-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="00df5-108">Name</span><span class="sxs-lookup"><span data-stu-id="00df5-108">Name</span></span>    | <span data-ttu-id="00df5-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="00df5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00df5-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="00df5-110">Scope</span></span>   |<span data-ttu-id="00df5-111">Není známo</span><span class="sxs-lookup"><span data-stu-id="00df5-111">Unknown</span></span>|
|<span data-ttu-id="00df5-112">Verze</span><span class="sxs-lookup"><span data-stu-id="00df5-112">Version</span></span>|<span data-ttu-id="00df5-113">4,8</span><span class="sxs-lookup"><span data-stu-id="00df5-113">4.8</span></span>|
|<span data-ttu-id="00df5-114">Typ</span><span class="sxs-lookup"><span data-stu-id="00df5-114">Type</span></span>|<span data-ttu-id="00df5-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="00df5-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00df5-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="00df5-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
