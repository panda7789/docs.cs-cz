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
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053247"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="3f22b-102">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f22b-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="3f22b-103">.NET Framework se neustále vyvíjí.</span><span class="sxs-lookup"><span data-stu-id="3f22b-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="3f22b-104">Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě jsou nové funkce vydány mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="3f22b-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="3f22b-105">Toto téma obsahuje seznam projektů OOB, pro které poskytujeme dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3f22b-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="3f22b-106">Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f22b-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="3f22b-107"><xref:System.Text.CodePagesEncodingProvider> Třída například zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f22b-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="3f22b-108">Toto téma obsahuje i tyto knihovny.</span><span class="sxs-lookup"><span data-stu-id="3f22b-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="3f22b-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="3f22b-109">OOB projects</span></span>
  
| <span data-ttu-id="3f22b-110">Project</span><span class="sxs-lookup"><span data-stu-id="3f22b-110">Project</span></span> | <span data-ttu-id="3f22b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3f22b-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="3f22b-112">Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah.</span><span class="sxs-lookup"><span data-stu-id="3f22b-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="3f22b-113">Poskytuje obslužnou rutinu zpráv <xref:System.Net.Http.HttpClient> pro založenou na rozhraní WinHTTP systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3f22b-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="3f22b-114">Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.</span><span class="sxs-lookup"><span data-stu-id="3f22b-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="3f22b-115">Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="3f22b-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="3f22b-116">Knihovny pro konkrétní platformu</span><span class="sxs-lookup"><span data-stu-id="3f22b-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="3f22b-117">Project</span><span class="sxs-lookup"><span data-stu-id="3f22b-117">Project</span></span> | <span data-ttu-id="3f22b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3f22b-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="3f22b-119"><xref:System.Text.EncodingProvider> Rozšiřuje třídu tak, aby byly k dispozici kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="3f22b-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="3f22b-120">Privátní rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f22b-120">Private APIs</span></span>  

<span data-ttu-id="3f22b-121">Tato rozhraní API podporují infrastrukturu produktů a nejsou zamýšlená ani podporovaná pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="3f22b-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="3f22b-122">Název rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f22b-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="3f22b-123">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="3f22b-123">System.Net.Connection Class</span></span>](connection.md) |
| [<span data-ttu-id="3f22b-124">System .NET. Connection. m\_WriteList – pole</span><span class="sxs-lookup"><span data-stu-id="3f22b-124">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md) |
| [<span data-ttu-id="3f22b-125">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="3f22b-125">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md) |
| [<span data-ttu-id="3f22b-126">Pole System .NET. Connection. m\_ConnectionList</span><span class="sxs-lookup"><span data-stu-id="3f22b-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md) |
| [<span data-ttu-id="3f22b-127">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="3f22b-127">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md) |
| [<span data-ttu-id="3f22b-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="3f22b-129">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="3f22b-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md) |
| [<span data-ttu-id="3f22b-131">System .NET. HttpWebRequest. \_Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="3f22b-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="3f22b-132">System.Net.HttpWebRequest.\_HttpResponse Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md) |
| [<span data-ttu-id="3f22b-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md) |
| [<span data-ttu-id="3f22b-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md) |
| [<span data-ttu-id="3f22b-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="3f22b-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="3f22b-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="3f22b-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md) |
| [<span data-ttu-id="3f22b-137">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="3f22b-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="3f22b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f22b-138">See also</span></span>

- [<span data-ttu-id="3f22b-139">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="3f22b-139">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
