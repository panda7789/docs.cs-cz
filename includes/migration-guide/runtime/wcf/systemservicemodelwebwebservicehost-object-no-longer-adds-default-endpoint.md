---
ms.openlocfilehash: 57f68c10d5d1edc9b8deaca2f4fe7edda2dd69b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620068"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="59ec5-101">Objekt System. ServiceModel. Web. WebServiceHost už nepřidává výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="59ec5-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="59ec5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="59ec5-102">Details</span></span>

<span data-ttu-id="59ec5-103"><xref:System.ServiceModel.Web.WebServiceHost>Objekt již nepřidá výchozí koncový bod, pokud byl do kódu aplikace přidán explicitní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="59ec5-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="59ec5-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="59ec5-104">Suggestion</span></span>

<span data-ttu-id="59ec5-105">Pokud budou uživatelé muset být schopni se připojit k výchozímu koncovému bodu a Přidali jste do <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> , výchozí koncové body by se měly také přidat explicitně (pomocí <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="59ec5-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="59ec5-106">Name</span><span class="sxs-lookup"><span data-stu-id="59ec5-106">Name</span></span>    | <span data-ttu-id="59ec5-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="59ec5-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="59ec5-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="59ec5-108">Scope</span></span>   |<span data-ttu-id="59ec5-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="59ec5-109">Minor</span></span>|
|<span data-ttu-id="59ec5-110">Verze</span><span class="sxs-lookup"><span data-stu-id="59ec5-110">Version</span></span>|<span data-ttu-id="59ec5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="59ec5-111">4.5</span></span>|
|<span data-ttu-id="59ec5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="59ec5-112">Type</span></span>|<span data-ttu-id="59ec5-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="59ec5-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59ec5-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="59ec5-114">Affected APIs</span></span>

-<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li></ul>|
