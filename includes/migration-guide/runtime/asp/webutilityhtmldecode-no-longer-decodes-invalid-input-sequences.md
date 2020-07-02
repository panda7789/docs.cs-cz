---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619933"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="5ca12-101">WebUtility.HtmlDecode už nekóduje neplatné vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="5ca12-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="5ca12-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5ca12-102">Details</span></span>

<span data-ttu-id="5ca12-103">Ve výchozím nastavení metody dekódování již neprovádějí dekódování neplatné vstupní sekvence do neplatného řetězce UTF-16.</span><span class="sxs-lookup"><span data-stu-id="5ca12-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="5ca12-104">Namísto toho vracejí původní vstup.</span><span class="sxs-lookup"><span data-stu-id="5ca12-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5ca12-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="5ca12-105">Suggestion</span></span>

<span data-ttu-id="5ca12-106">Změna dekodéru výstupu by měla mít vliv, pouze pokud do řetězců ukládáte binární data namísto dat UTF-16.</span><span class="sxs-lookup"><span data-stu-id="5ca12-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="5ca12-107">Chcete-li toto chování explicitně řídit, nastavte <code>aspnet:AllowRelaxedUnicodeDecoding</code> atribut elementu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) na <code>true</code> , aby bylo možné povolit starší chování nebo <code>false</code> Povolit aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="5ca12-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="5ca12-108">Name</span><span class="sxs-lookup"><span data-stu-id="5ca12-108">Name</span></span>    | <span data-ttu-id="5ca12-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5ca12-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5ca12-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5ca12-110">Scope</span></span>   |<span data-ttu-id="5ca12-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="5ca12-111">Minor</span></span>|
|<span data-ttu-id="5ca12-112">Verze</span><span class="sxs-lookup"><span data-stu-id="5ca12-112">Version</span></span>|<span data-ttu-id="5ca12-113">4.5</span><span class="sxs-lookup"><span data-stu-id="5ca12-113">4.5</span></span>|
|<span data-ttu-id="5ca12-114">Typ</span><span class="sxs-lookup"><span data-stu-id="5ca12-114">Type</span></span>|<span data-ttu-id="5ca12-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5ca12-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5ca12-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5ca12-116">Affected APIs</span></span>

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
