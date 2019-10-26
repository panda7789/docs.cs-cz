---
title: Další knihovny tříd a rozhraní API
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 4b47847e9d6e9424d4442d655c40a637383c7229
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847072"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="28ee6-102">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="28ee6-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="28ee6-103">.NET Framework se neustále vyvíjí.</span><span class="sxs-lookup"><span data-stu-id="28ee6-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="28ee6-104">Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě jsou nové funkce vydány mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="28ee6-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="28ee6-105">Toto téma obsahuje seznam projektů OOB, pro které poskytujeme dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="28ee6-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="28ee6-106">Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28ee6-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="28ee6-107">Například třída <xref:System.Text.CodePagesEncodingProvider> zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28ee6-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="28ee6-108">Toto téma obsahuje i tyto knihovny.</span><span class="sxs-lookup"><span data-stu-id="28ee6-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="28ee6-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="28ee6-109">OOB projects</span></span>
  
| <span data-ttu-id="28ee6-110">Project</span><span class="sxs-lookup"><span data-stu-id="28ee6-110">Project</span></span> | <span data-ttu-id="28ee6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="28ee6-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="28ee6-112">Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah.</span><span class="sxs-lookup"><span data-stu-id="28ee6-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="28ee6-113">Poskytuje obslužnou rutinu zpráv pro <xref:System.Net.Http.HttpClient> na základě rozhraní WinHTTP Windows.</span><span class="sxs-lookup"><span data-stu-id="28ee6-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="28ee6-114">Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.</span><span class="sxs-lookup"><span data-stu-id="28ee6-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="28ee6-115">Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="28ee6-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="28ee6-116">Knihovny specifické pro platformu</span><span class="sxs-lookup"><span data-stu-id="28ee6-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="28ee6-117">Project</span><span class="sxs-lookup"><span data-stu-id="28ee6-117">Project</span></span> | <span data-ttu-id="28ee6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="28ee6-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="28ee6-119">Rozšiřuje třídu <xref:System.Text.EncodingProvider> a zpřístupňuje kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="28ee6-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="28ee6-120">Privátní rozhraní API</span><span class="sxs-lookup"><span data-stu-id="28ee6-120">Private APIs</span></span>  

<span data-ttu-id="28ee6-121">Tato rozhraní API podporují infrastrukturu produktů a nejsou zamýšlená ani podporovaná pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="28ee6-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="28ee6-122">Vlastnost Microsoft. SqlServer. Server. SmiOrderProperty. Item</span><span class="sxs-lookup"><span data-stu-id="28ee6-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="28ee6-123">System. Exception. PrepForRemoting – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="28ee6-124">System. data. SqlTypes. SqlChars. Stream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="28ee6-125">System. data. SqlTypes. SqlStreamChars – konstruktor</span><span class="sxs-lookup"><span data-stu-id="28ee6-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="28ee6-126">System. data. SqlTypes. SqlStreamChars. CanSeek – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="28ee6-127">System. data. SqlTypes. SqlStreamChars. IsNull – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="28ee6-128">System. data. SqlTypes. SqlStreamChars. Length – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="28ee6-129">System. data. SqlTypes. SqlStreamChars. Close – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="28ee6-130">System. data. SqlTypes. SqlStreamChars. Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="28ee6-131">System. data. SqlTypes. SqlStreamChars. Flush – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="28ee6-132">System. data. SqlTypes. SqlStreamChars. Read – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="28ee6-133">System. data. SqlTypes. SqlStreamChars. Seek – Metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="28ee6-134">System. data. SqlTypes. SqlStreamChars. SetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="28ee6-135">System. data. SqlTypes. SqlStreamChars. Write – Metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="28ee6-136">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="28ee6-136">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="28ee6-137">System .NET. Connection. m\_pole WriteList</span><span class="sxs-lookup"><span data-stu-id="28ee6-137">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="28ee6-138">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="28ee6-138">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="28ee6-139">System .NET. Connection. m\_pole ConnectionList</span><span class="sxs-lookup"><span data-stu-id="28ee6-139">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="28ee6-140">System .NET. ConnectStream. Connection – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-140">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="28ee6-141">System .NET. CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="28ee6-141">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="28ee6-142">System .NET. CoreResponseData. m\_pole ResponseHeaders hostitele</span><span class="sxs-lookup"><span data-stu-id="28ee6-142">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="28ee6-143">System .NET. CoreResponseData. m\_pole StatusCode</span><span class="sxs-lookup"><span data-stu-id="28ee6-143">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="28ee6-144">Pole autoredirect pro System .NET. HttpWebRequest.\_</span><span class="sxs-lookup"><span data-stu-id="28ee6-144">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="28ee6-145">Pole System .NET. HttpWebRequest.\_CoreResponse</span><span class="sxs-lookup"><span data-stu-id="28ee6-145">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="28ee6-146">Pole System .NET. HttpWebRequest.\_HttpResponse</span><span class="sxs-lookup"><span data-stu-id="28ee6-146">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="28ee6-147">System .NET. PooledStream. NetworkStream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-147">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="28ee6-148">System .NET. ServicePoint. m\_pole ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="28ee6-148">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="28ee6-149">System .NET. Třída ServicePointManager. s\_pole ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="28ee6-149">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="28ee6-150">Pole System .NET. TlsStream. m_Worker</span><span class="sxs-lookup"><span data-stu-id="28ee6-150">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="28ee6-151">System .NET. Security. SslState. SslProtocol – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-151">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="28ee6-152">System. Windows. Diagnostics. VisualDiagnostics. s\_pole isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="28ee6-152">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="28ee6-153">System. Windows. Forms. Design. DataMemberFieldEditor – třída</span><span class="sxs-lookup"><span data-stu-id="28ee6-153">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="28ee6-154">System. Windows. Forms. Design. DataMemberListEditor – třída</span><span class="sxs-lookup"><span data-stu-id="28ee6-154">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="28ee6-155">System. XML. XmlReader. CreateSqlReader – metoda</span><span class="sxs-lookup"><span data-stu-id="28ee6-155">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="28ee6-156">ADODB. Rozhraní připojení</span><span class="sxs-lookup"><span data-stu-id="28ee6-156">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="28ee6-157">ADODB. Výčet EventReason</span><span class="sxs-lookup"><span data-stu-id="28ee6-157">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="28ee6-158">ADODB. Výčet EventStatus</span><span class="sxs-lookup"><span data-stu-id="28ee6-158">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="28ee6-159">stdole. Struktura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="28ee6-159">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="28ee6-160">stdole. Struktura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="28ee6-160">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="28ee6-161">stdole. Vlastnost IFont.Name</span><span class="sxs-lookup"><span data-stu-id="28ee6-161">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="28ee6-162">stdole. Rozhraní IFontDisp</span><span class="sxs-lookup"><span data-stu-id="28ee6-162">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="28ee6-163">stdole. IPicture. Handle – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-163">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="28ee6-164">stdole. IPictureDisp. Handle – vlastnost</span><span class="sxs-lookup"><span data-stu-id="28ee6-164">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="28ee6-165">stdole. Rozhraní StdFont</span><span class="sxs-lookup"><span data-stu-id="28ee6-165">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="28ee6-166">stdole. Rozhraní StdPicture</span><span class="sxs-lookup"><span data-stu-id="28ee6-166">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="28ee6-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28ee6-167">See also</span></span>

* [<span data-ttu-id="28ee6-168">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="28ee6-168">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
