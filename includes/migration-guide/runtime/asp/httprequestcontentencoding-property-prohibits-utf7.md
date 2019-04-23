---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803678"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="53dd0-101">Vlastnost HttpRequest.ContentEncoding zakazuje UTF7</span><span class="sxs-lookup"><span data-stu-id="53dd0-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="53dd0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="53dd0-102">Details</span></span>|<span data-ttu-id="53dd0-103">Počínaje .NET Framework 4.5, kódování UTF-7 je zakázáno v <xref:System.Web.HttpRequest?displayProperty=name>s "subjekty.</span><span class="sxs-lookup"><span data-stu-id="53dd0-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="53dd0-104">Data pro aplikace, které závisí na příchozích datech UTF-7, se nebudou v některých případech správně dekódovat.</span><span class="sxs-lookup"><span data-stu-id="53dd0-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="53dd0-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="53dd0-105">Suggestion</span></span>|<span data-ttu-id="53dd0-106">V ideálním případě by měl používat v kódování UTF-7 aktualizují aplikace <xref:System.Web.HttpRequest?displayProperty=name>s.</span><span class="sxs-lookup"><span data-stu-id="53dd0-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="53dd0-107">Alternativně lze obnovit starší chování pomocí <code>aspnet:AllowUtf7RequestContentEncoding</code> atribut [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="53dd0-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="53dd0-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="53dd0-108">Scope</span></span>|<span data-ttu-id="53dd0-109">Edge</span><span class="sxs-lookup"><span data-stu-id="53dd0-109">Edge</span></span>|
|<span data-ttu-id="53dd0-110">Version</span><span class="sxs-lookup"><span data-stu-id="53dd0-110">Version</span></span>|<span data-ttu-id="53dd0-111">4.5</span><span class="sxs-lookup"><span data-stu-id="53dd0-111">4.5</span></span>|
|<span data-ttu-id="53dd0-112">Type</span><span class="sxs-lookup"><span data-stu-id="53dd0-112">Type</span></span>|<span data-ttu-id="53dd0-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="53dd0-113">Runtime</span></span>|
|<span data-ttu-id="53dd0-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="53dd0-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
