---
title: Další knihovny tříd a rozhraní API
description: Prozkoumejte další knihovny tříd a rozhraní API v .NET, včetně projektů OOB (out-of-band), knihoven specifických pro platformu a privátních rozhraní API.
ms.date: 06/12/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 0b888d2f0e80685ba993682b2f3067cf8aee15bc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989741"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="76196-103">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="76196-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="76196-104">Tento článek obsahuje seznam .NET Framework rozhraní API, které byly buď vydány mimo pásmo, cílí na konkrétní platformu, nebo jsou privátní nebo interní typy.</span><span class="sxs-lookup"><span data-stu-id="76196-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="76196-105">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="76196-105">OOB projects</span></span>

<span data-ttu-id="76196-106">Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě některé .NET Framework funkce byly vydány mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="76196-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="76196-107">Project</span><span class="sxs-lookup"><span data-stu-id="76196-107">Project</span></span> | <span data-ttu-id="76196-108">Popis</span><span class="sxs-lookup"><span data-stu-id="76196-108">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="76196-109">Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah.</span><span class="sxs-lookup"><span data-stu-id="76196-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="76196-110">Poskytuje obslužnou rutinu zpráv pro <xref:System.Net.Http.HttpClient> založenou na rozhraní WinHTTP systému Windows.</span><span class="sxs-lookup"><span data-stu-id="76196-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="76196-111">Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.</span><span class="sxs-lookup"><span data-stu-id="76196-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="76196-112">Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="76196-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="76196-113">Knihovny specifické pro platformu</span><span class="sxs-lookup"><span data-stu-id="76196-113">Platform-specific libraries</span></span>

<span data-ttu-id="76196-114">Některé knihovny cílí na konkrétní platformy.</span><span class="sxs-lookup"><span data-stu-id="76196-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="76196-115"><xref:System.Text.CodePagesEncodingProvider>Třída například zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76196-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>
  
| <span data-ttu-id="76196-116">Project</span><span class="sxs-lookup"><span data-stu-id="76196-116">Project</span></span> | <span data-ttu-id="76196-117">Popis</span><span class="sxs-lookup"><span data-stu-id="76196-117">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="76196-118">Rozšiřuje <xref:System.Text.EncodingProvider> třídu tak, aby byly k dispozici kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows.</span><span class="sxs-lookup"><span data-stu-id="76196-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="76196-119">Privátní rozhraní API</span><span class="sxs-lookup"><span data-stu-id="76196-119">Private APIs</span></span>  

<span data-ttu-id="76196-120">Tato rozhraní API podporují infrastrukturu produktů a nejsou zamýšlená ani podporovaná pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="76196-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="76196-121">Vlastnost Microsoft. SqlServer. Server. SmiOrderProperty. Item</span><span class="sxs-lookup"><span data-stu-id="76196-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="76196-122">System. Exception. PrepForRemoting – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="76196-123">System. data. SqlTypes. SqlChars. Stream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="76196-124">System. data. SqlTypes. SqlStreamChars – konstruktor</span><span class="sxs-lookup"><span data-stu-id="76196-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="76196-125">System. data. SqlTypes. SqlStreamChars. CanSeek – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="76196-126">System. data. SqlTypes. SqlStreamChars. IsNull – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="76196-127">System. data. SqlTypes. SqlStreamChars. Length – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="76196-128">System. data. SqlTypes. SqlStreamChars. Close – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="76196-129">System. data. SqlTypes. SqlStreamChars. Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="76196-130">System. data. SqlTypes. SqlStreamChars. Flush – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="76196-131">System. data. SqlTypes. SqlStreamChars. Read – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="76196-132">System. data. SqlTypes. SqlStreamChars. Seek – Metoda</span><span class="sxs-lookup"><span data-stu-id="76196-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="76196-133">System. data. SqlTypes. SqlStreamChars. SetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="76196-134">System. data. SqlTypes. SqlStreamChars. Write – Metoda</span><span class="sxs-lookup"><span data-stu-id="76196-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="76196-135">System. IO. typu MemoryStream není. InternalGetOriginAndLength – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="76196-136">System .NET. ComNetOS – třída</span><span class="sxs-lookup"><span data-stu-id="76196-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="76196-137">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="76196-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="76196-138">System .NET. Connection. m \_ WriteList – pole</span><span class="sxs-lookup"><span data-stu-id="76196-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="76196-139">System .NET. Connection – třída</span><span class="sxs-lookup"><span data-stu-id="76196-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="76196-140">Pole System .NET. Connection. m \_ ConnectionList</span><span class="sxs-lookup"><span data-stu-id="76196-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="76196-141">System .NET. ConnectStream. Connection – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="76196-142">System .NET. CoreResponseData – třída</span><span class="sxs-lookup"><span data-stu-id="76196-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="76196-143">Pole System .NET. CoreResponseData. m \_ ResponseHeaders hostitele</span><span class="sxs-lookup"><span data-stu-id="76196-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="76196-144">System .NET. CoreResponseData. m \_ StatusCode – pole</span><span class="sxs-lookup"><span data-stu-id="76196-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="76196-145">System .NET. ExceptionHelper – třída</span><span class="sxs-lookup"><span data-stu-id="76196-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="76196-146">System .NET. HttpStatusDescription – třída</span><span class="sxs-lookup"><span data-stu-id="76196-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="76196-147">System .NET. HttpWebRequest. \_ Pole autoredirect</span><span class="sxs-lookup"><span data-stu-id="76196-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="76196-148">System .NET. HttpWebRequest. \_ Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="76196-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="76196-149">System .NET. HttpWebRequest. \_ Pole HttpResponse</span><span class="sxs-lookup"><span data-stu-id="76196-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="76196-150">System .NET. Logging – třída</span><span class="sxs-lookup"><span data-stu-id="76196-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="76196-151">System .NET. mail. MailAddressParser – třída</span><span class="sxs-lookup"><span data-stu-id="76196-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="76196-152">System .NET. mail. QuotedPairReader – třída</span><span class="sxs-lookup"><span data-stu-id="76196-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="76196-153">System .NET. MIME. MailBnfHelper – třída</span><span class="sxs-lookup"><span data-stu-id="76196-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="76196-154">System .NET. PooledStream. NetworkStream – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="76196-155">System .NET. RtcState – třída</span><span class="sxs-lookup"><span data-stu-id="76196-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="76196-156">System .NET. Security. SslState. SslProtocol – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="76196-157">Pole System .NET. ServicePoint. m \_ ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="76196-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="76196-158">System .NET. Třída ServicePointManager. CloseConnectionGroups – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="76196-159">Pole System .NET. Třída ServicePointManager. s \_ ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="76196-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="76196-160">System .NET. TlsStream. m_Worker – pole</span><span class="sxs-lookup"><span data-stu-id="76196-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="76196-161">System .NET. UnsafeNclNativeMethods – třída</span><span class="sxs-lookup"><span data-stu-id="76196-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="76196-162">System .NET. WebHeaderCollection. AddInternal – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="76196-163">System. ServiceModel. Channels. Message. BodyToString – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="76196-164">System. ServiceModel. Channels. Message. WriteStartHeaders – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="76196-165">Pole System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="76196-165">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="76196-166">System. Windows. Forms. Design. DataMemberFieldEditor – třída</span><span class="sxs-lookup"><span data-stu-id="76196-166">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="76196-167">System. Windows. Forms. Design. DataMemberListEditor – třída</span><span class="sxs-lookup"><span data-stu-id="76196-167">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="76196-168">System.Xml.XmlReader. CreateSqlReader – metoda</span><span class="sxs-lookup"><span data-stu-id="76196-168">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="76196-169">ADODB. Rozhraní připojení</span><span class="sxs-lookup"><span data-stu-id="76196-169">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="76196-170">ADODB. Výčet EventReason</span><span class="sxs-lookup"><span data-stu-id="76196-170">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="76196-171">ADODB. Výčet EventStatus</span><span class="sxs-lookup"><span data-stu-id="76196-171">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="76196-172">stdole. Struktura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="76196-172">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="76196-173">stdole. Struktura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="76196-173">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="76196-174">stdole. Vlastnost IFont.Name</span><span class="sxs-lookup"><span data-stu-id="76196-174">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="76196-175">stdole. Rozhraní IFontDisp</span><span class="sxs-lookup"><span data-stu-id="76196-175">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="76196-176">stdole. IPicture. Handle – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-176">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="76196-177">stdole. IPictureDisp. Handle – vlastnost</span><span class="sxs-lookup"><span data-stu-id="76196-177">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="76196-178">stdole. Rozhraní StdFont</span><span class="sxs-lookup"><span data-stu-id="76196-178">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="76196-179">stdole. Rozhraní StdPicture</span><span class="sxs-lookup"><span data-stu-id="76196-179">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="76196-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="76196-180">See also</span></span>

* [<span data-ttu-id="76196-181">.NET Framework a vzdálené verze</span><span class="sxs-lookup"><span data-stu-id="76196-181">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
