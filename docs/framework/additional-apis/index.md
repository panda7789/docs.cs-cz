---
title: Další knihovny tříd a rozhraní API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 84e2d07275194683661a75e422847bbe0ebf1383
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198364"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="653fd-102">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="653fd-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="653fd-103">Rozhraní .NET Framework se neustále vyvíjí.</span><span class="sxs-lookup"><span data-stu-id="653fd-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="653fd-104">Zlepšení vývoje napříč platformami a již v rané fázi zavedení nových funkcí, jsou vydávány nové funkce mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="653fd-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="653fd-105">Toto téma obsahuje seznam projektů OOB, které zajišťuje dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="653fd-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="653fd-106">Kromě toho některé knihovny cílit na konkrétní platformy nebo implementace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="653fd-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="653fd-107">Například <xref:System.Text.CodePagesEncodingProvider> třídy zpřístupní kódování znakových stránek aplikací pro UWP vyvinuté pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="653fd-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="653fd-108">Toto téma obsahuje také tyto knihovny.</span><span class="sxs-lookup"><span data-stu-id="653fd-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="653fd-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="653fd-109">OOB projects</span></span>
  
| <span data-ttu-id="653fd-110">Projekt</span><span class="sxs-lookup"><span data-stu-id="653fd-110">Project</span></span> | <span data-ttu-id="653fd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="653fd-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="653fd-112">Obsahuje kolekce, které jsou vlákna bezpečné a zaručené nikdy nezmění jejich obsah.</span><span class="sxs-lookup"><span data-stu-id="653fd-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="653fd-113">Poskytuje obslužné rutiny zpráv pro <xref:System.Net.Http.HttpClient> podle WinHTTP rozhraní Windows.</span><span class="sxs-lookup"><span data-stu-id="653fd-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="653fd-114">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="653fd-114">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="653fd-115">Poskytuje knihovnu vektorové typy, které můžete využít výhod SIMD hardwarové akcelerace.</span><span class="sxs-lookup"><span data-stu-id="653fd-115">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="653fd-116">Knihovna TPL datového toku poskytuje součásti toku dat a pomáhá tak zvýšit odolnost aplikace pro práci s souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="653fd-116">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="653fd-117">Knihovny pro konkrétní platformu</span><span class="sxs-lookup"><span data-stu-id="653fd-117">Platform-specific libraries</span></span>
  
| <span data-ttu-id="653fd-118">Projekt</span><span class="sxs-lookup"><span data-stu-id="653fd-118">Project</span></span> | <span data-ttu-id="653fd-119">Popis</span><span class="sxs-lookup"><span data-stu-id="653fd-119">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="653fd-120">Rozšiřuje <xref:System.Text.EncodingProvider> třídy pro zpřístupnění kódování znakových stránek pro aplikace, které cílí univerzální platformu Windows.</span><span class="sxs-lookup"><span data-stu-id="653fd-120">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="653fd-121">Soukromé rozhraní API</span><span class="sxs-lookup"><span data-stu-id="653fd-121">Private APIs</span></span>  

<span data-ttu-id="653fd-122">Tato rozhraní API podporují produktovou infrastrukturu a nejsou určené nebo podporované pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="653fd-122">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="653fd-123">Název rozhraní API</span><span class="sxs-lookup"><span data-stu-id="653fd-123">API Name</span></span> |
| -------- |
| [<span data-ttu-id="653fd-124">Třída System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="653fd-124">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="653fd-125">System.Net.Connection.m\_WriteList pole</span><span class="sxs-lookup"><span data-stu-id="653fd-125">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="653fd-126">Třída System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="653fd-126">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="653fd-127">System.Net.ConnectionGroup.m\_ConnectionList pole</span><span class="sxs-lookup"><span data-stu-id="653fd-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="653fd-128">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="653fd-128">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="653fd-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="653fd-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="653fd-130">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="653fd-130">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="653fd-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span><span class="sxs-lookup"><span data-stu-id="653fd-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="653fd-132">System.Net.HttpWebRequest. \_CoreResponse pole</span><span class="sxs-lookup"><span data-stu-id="653fd-132">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="653fd-133">System.Net.HttpWebRequest.\_HttpResponse Field</span><span class="sxs-lookup"><span data-stu-id="653fd-133">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="653fd-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="653fd-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="653fd-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="653fd-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="653fd-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="653fd-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="653fd-137">Třída System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="653fd-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="653fd-138">Třída System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="653fd-138">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="653fd-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="653fd-139">See also</span></span>

- [<span data-ttu-id="653fd-140">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="653fd-140">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
