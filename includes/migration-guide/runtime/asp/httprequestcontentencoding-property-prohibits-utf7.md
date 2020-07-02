---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619918"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="28528-101">Vlastnost HttpRequest. ContentEncoding zakazuje UTF7.</span><span class="sxs-lookup"><span data-stu-id="28528-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="28528-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="28528-102">Details</span></span>

<span data-ttu-id="28528-103">Počínaje .NET Framework 4,5 je kódování UTF-7 v <xref:System.Web.HttpRequest?displayProperty=fullName> útvarech s zakázáno.</span><span class="sxs-lookup"><span data-stu-id="28528-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="28528-104">Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.</span><span class="sxs-lookup"><span data-stu-id="28528-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="28528-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="28528-105">Suggestion</span></span>

<span data-ttu-id="28528-106">V ideálním případě by se měly aplikace aktualizovat tak, aby nepoužívaly kódování UTF-7 v <xref:System.Web.HttpRequest?displayProperty=fullName> s.</span><span class="sxs-lookup"><span data-stu-id="28528-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="28528-107">Alternativně je možné obnovit starší chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atributu elementu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="28528-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="28528-108">Name</span><span class="sxs-lookup"><span data-stu-id="28528-108">Name</span></span>    | <span data-ttu-id="28528-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="28528-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="28528-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="28528-110">Scope</span></span>   |<span data-ttu-id="28528-111">Edge</span><span class="sxs-lookup"><span data-stu-id="28528-111">Edge</span></span>|
|<span data-ttu-id="28528-112">Verze</span><span class="sxs-lookup"><span data-stu-id="28528-112">Version</span></span>|<span data-ttu-id="28528-113">4.5</span><span class="sxs-lookup"><span data-stu-id="28528-113">4.5</span></span>|
|<span data-ttu-id="28528-114">Typ</span><span class="sxs-lookup"><span data-stu-id="28528-114">Type</span></span>|<span data-ttu-id="28528-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="28528-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="28528-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="28528-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
