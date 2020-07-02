---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619924"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="2143f-101">Ampersand – HttpUtility. JavaScriptStringEncode – řídicí znaky</span><span class="sxs-lookup"><span data-stu-id="2143f-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="2143f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2143f-102">Details</span></span>

<span data-ttu-id="2143f-103">Počínaje .NET Framework 4,5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> řídí znak ampersand ( &amp; ).</span><span class="sxs-lookup"><span data-stu-id="2143f-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2143f-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="2143f-104">Suggestion</span></span>

<span data-ttu-id="2143f-105">Pokud vaše aplikace závisí na předchozím chování této metody, můžete přidat nastavení ASPNET: JavaScriptDoNotEncodeAmpersand do [elementu ASP.NET appSettings](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2143f-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="2143f-106">Name</span><span class="sxs-lookup"><span data-stu-id="2143f-106">Name</span></span>    | <span data-ttu-id="2143f-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2143f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2143f-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2143f-108">Scope</span></span>   |<span data-ttu-id="2143f-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2143f-109">Minor</span></span>|
|<span data-ttu-id="2143f-110">Verze</span><span class="sxs-lookup"><span data-stu-id="2143f-110">Version</span></span>|<span data-ttu-id="2143f-111">4.5</span><span class="sxs-lookup"><span data-stu-id="2143f-111">4.5</span></span>|
|<span data-ttu-id="2143f-112">Typ</span><span class="sxs-lookup"><span data-stu-id="2143f-112">Type</span></span>|<span data-ttu-id="2143f-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2143f-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2143f-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2143f-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
