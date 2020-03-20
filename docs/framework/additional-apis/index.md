---
title: Další knihovny tříd a rozhraní API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155905"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="e58b2-102">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e58b2-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="e58b2-103">Rozhraní .NET Framework se neustále vyvíjí.</span><span class="sxs-lookup"><span data-stu-id="e58b2-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="e58b2-104">Chcete-li zlepšit vývoj napříč platformami a zavést nové funkce brzy, nové funkce jsou uvolněny mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="e58b2-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="e58b2-105">Toto téma uvádí projekty OOB, pro které poskytujeme dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="e58b2-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="e58b2-106">Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e58b2-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="e58b2-107"><xref:System.Text.CodePagesEncodingProvider> Například třída zpřístupňuje kódování znakové stránky pro aplikace UPW vyvinuté pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e58b2-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="e58b2-108">Toto téma obsahuje také tyto knihovny.</span><span class="sxs-lookup"><span data-stu-id="e58b2-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="e58b2-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="e58b2-109">OOB projects</span></span>
  
| <span data-ttu-id="e58b2-110">Project</span><span class="sxs-lookup"><span data-stu-id="e58b2-110">Project</span></span> | <span data-ttu-id="e58b2-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e58b2-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="e58b2-112">Poskytuje kolekce, které jsou bezpečné pro přístup z více vláken a zaručeně nikdy nezmění jejich obsah.</span><span class="sxs-lookup"><span data-stu-id="e58b2-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="e58b2-113">Poskytuje obslužnou rutinu zprávy založenou <xref:System.Net.Http.HttpClient> na rozhraní WinHTTP systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e58b2-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="e58b2-114">Poskytuje knihovnu vektorových typů, které mohou využívat hardwarovou akceleraci SIMD.</span><span class="sxs-lookup"><span data-stu-id="e58b2-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="e58b2-115">Knihovna Toku dat TPL poskytuje komponenty toku dat, které pomáhají zvýšit robustnost aplikací s podporou souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e58b2-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="e58b2-116">Knihovny specifické pro platformu</span><span class="sxs-lookup"><span data-stu-id="e58b2-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="e58b2-117">Project</span><span class="sxs-lookup"><span data-stu-id="e58b2-117">Project</span></span> | <span data-ttu-id="e58b2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e58b2-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="e58b2-119">Rozšiřuje třídu <xref:System.Text.EncodingProvider> tak, aby kódovací stránky byly dostupné pro aplikace, které cílí na univerzální platformu Windows.</span><span class="sxs-lookup"><span data-stu-id="e58b2-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="e58b2-120">Privátní api</span><span class="sxs-lookup"><span data-stu-id="e58b2-120">Private APIs</span></span>  

<span data-ttu-id="e58b2-121">Tato řešení API podporují infrastrukturu produktů a nejsou určena nebo podporována pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e58b2-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="e58b2-122">Vlastnost Microsoft.SqlServer.Server.SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="e58b2-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="e58b2-123">Metoda System.Exception.PrepForRemoting</span><span class="sxs-lookup"><span data-stu-id="e58b2-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="e58b2-124">Vlastnost System.Data.SqlTypes.SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="e58b2-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="e58b2-125">Konstruktor System.Data.SqlTypes.SqlStreamChars</span><span class="sxs-lookup"><span data-stu-id="e58b2-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="e58b2-126">Vlastnost System.Data.SqlTypes.SqlStreamChars.CanSeek</span><span class="sxs-lookup"><span data-stu-id="e58b2-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="e58b2-127">Vlastnost System.Data.SqlTypes.SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="e58b2-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="e58b2-128">Vlastnost System.Data.SqlTypes.SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="e58b2-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="e58b2-129">Metoda System.Data.SqlTypes.SqlStreamChars.Close</span><span class="sxs-lookup"><span data-stu-id="e58b2-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="e58b2-130">Metoda System.Data.SqlTypes.SqlStreamChars.Dispose</span><span class="sxs-lookup"><span data-stu-id="e58b2-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="e58b2-131">Metoda System.Data.SqlTypes.SqlStreamChars.Flush</span><span class="sxs-lookup"><span data-stu-id="e58b2-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="e58b2-132">Metoda System.Data.SqlTypes.SqlStreamChars.Read</span><span class="sxs-lookup"><span data-stu-id="e58b2-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="e58b2-133">Metoda System.Data.SqlTypes.SqlStreamChars.Seek</span><span class="sxs-lookup"><span data-stu-id="e58b2-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="e58b2-134">Metoda System.Data.SqlTypes.SqlStreamChars.SetLength</span><span class="sxs-lookup"><span data-stu-id="e58b2-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="e58b2-135">Metoda System.Data.SqlTypes.SqlStreamChars.Write</span><span class="sxs-lookup"><span data-stu-id="e58b2-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="e58b2-136">System.io.memorystream.internalGetOriginAndLength Metoda</span><span class="sxs-lookup"><span data-stu-id="e58b2-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="e58b2-137">Třída system.net.connection</span><span class="sxs-lookup"><span data-stu-id="e58b2-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="e58b2-138">Pole WriteList souboru\_System.Net.Connection.m</span><span class="sxs-lookup"><span data-stu-id="e58b2-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="e58b2-139">Třída System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="e58b2-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="e58b2-140">Pole System.Net.ConnectionGroup.m\_ConnectionList</span><span class="sxs-lookup"><span data-stu-id="e58b2-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="e58b2-141">Vlastnost System.Net.ConnectStream.Connection</span><span class="sxs-lookup"><span data-stu-id="e58b2-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="e58b2-142">Třída System.Net.CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="e58b2-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="e58b2-143">Pole Hlavičky odpovědí System.Net.CoreResponseData.m\_</span><span class="sxs-lookup"><span data-stu-id="e58b2-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="e58b2-144">Pole StatusCode System.Net.CoreResponseData.m\_</span><span class="sxs-lookup"><span data-stu-id="e58b2-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="e58b2-145">Systém.Net.HttpWebRequest. \_Pole Automatické přesměrování</span><span class="sxs-lookup"><span data-stu-id="e58b2-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="e58b2-146">Systém.Net.HttpWebRequest. \_Pole CoreResponse</span><span class="sxs-lookup"><span data-stu-id="e58b2-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="e58b2-147">Systém.Net.HttpWebRequest. \_Pole HttpResponse</span><span class="sxs-lookup"><span data-stu-id="e58b2-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="e58b2-148">Vlastnost System.Net.PooledStream.NetworkStream</span><span class="sxs-lookup"><span data-stu-id="e58b2-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="e58b2-149">Třída System.Net.RtcState</span><span class="sxs-lookup"><span data-stu-id="e58b2-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="e58b2-150">Pole System.Net.ServicePoint.m\_ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="e58b2-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="e58b2-151">Pole ServicePointTable systému.Net.ServicePointManager.s\_</span><span class="sxs-lookup"><span data-stu-id="e58b2-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="e58b2-152">Pole System.Net.TlsStream.m_Worker</span><span class="sxs-lookup"><span data-stu-id="e58b2-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="e58b2-153">Vlastnost System.Net.Security.SslState.SslProtocol</span><span class="sxs-lookup"><span data-stu-id="e58b2-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="e58b2-154">Metoda System.ServiceModel.Channels.Message.bodytostring</span><span class="sxs-lookup"><span data-stu-id="e58b2-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="e58b2-155">Metoda System.ServiceModel.Channels.Message.WriteStartHeaders</span><span class="sxs-lookup"><span data-stu-id="e58b2-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="e58b2-156">Pole System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="e58b2-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="e58b2-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="e58b2-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="e58b2-158">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="e58b2-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="e58b2-159">Metoda System.Xml.XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="e58b2-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="e58b2-160">Adodb. Rozhraní připojení</span><span class="sxs-lookup"><span data-stu-id="e58b2-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="e58b2-161">Adodb. Výčt usoudit událost</span><span class="sxs-lookup"><span data-stu-id="e58b2-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="e58b2-162">Adodb. Výčt u stavů událostí</span><span class="sxs-lookup"><span data-stu-id="e58b2-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="e58b2-163">stdole. Struktura DISPPARAMS</span><span class="sxs-lookup"><span data-stu-id="e58b2-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="e58b2-164">stdole. Struktura EXCEPINFO</span><span class="sxs-lookup"><span data-stu-id="e58b2-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="e58b2-165">stdole. vlastnost IFont.Name</span><span class="sxs-lookup"><span data-stu-id="e58b2-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="e58b2-166">stdole. Rozhraní IFontDisp</span><span class="sxs-lookup"><span data-stu-id="e58b2-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="e58b2-167">stdole. Vlastnost IPicture.Handle</span><span class="sxs-lookup"><span data-stu-id="e58b2-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="e58b2-168">stdole. Vlastnost IPictureDisp.Handle</span><span class="sxs-lookup"><span data-stu-id="e58b2-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="e58b2-169">stdole. Rozhraní StdFont</span><span class="sxs-lookup"><span data-stu-id="e58b2-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="e58b2-170">stdole. Rozhraní StdPicture</span><span class="sxs-lookup"><span data-stu-id="e58b2-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="e58b2-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="e58b2-171">See also</span></span>

* [<span data-ttu-id="e58b2-172">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="e58b2-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
