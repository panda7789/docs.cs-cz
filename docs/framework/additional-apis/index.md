---
title: Další knihovny tříd a rozhraní API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: e1e2af584c73b1c0b2548cdd3fcbd8517dfa330d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429335"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="ffcfb-102">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ffcfb-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="ffcfb-103">The .NET Framework is constantly evolving.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="ffcfb-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span><span class="sxs-lookup"><span data-stu-id="ffcfb-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="ffcfb-105">This topic lists the OOB projects that we provide documentation for.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="ffcfb-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="ffcfb-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="ffcfb-108">This topic lists these libraries as well.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="ffcfb-109">OOB projects</span><span class="sxs-lookup"><span data-stu-id="ffcfb-109">OOB projects</span></span>
  
| <span data-ttu-id="ffcfb-110">Project</span><span class="sxs-lookup"><span data-stu-id="ffcfb-110">Project</span></span> | <span data-ttu-id="ffcfb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ffcfb-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="ffcfb-112">Provides collections that are thread safe and guaranteed to never change their contents.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="ffcfb-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="ffcfb-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="ffcfb-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="ffcfb-116">Platform-specific libraries</span><span class="sxs-lookup"><span data-stu-id="ffcfb-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="ffcfb-117">Project</span><span class="sxs-lookup"><span data-stu-id="ffcfb-117">Project</span></span> | <span data-ttu-id="ffcfb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ffcfb-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="ffcfb-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="ffcfb-120">Private APIs</span><span class="sxs-lookup"><span data-stu-id="ffcfb-120">Private APIs</span></span>  

<span data-ttu-id="ffcfb-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span><span class="sxs-lookup"><span data-stu-id="ffcfb-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="ffcfb-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="ffcfb-123">System.Exception.PrepForRemoting Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="ffcfb-124">System.Data.SqlTypes.SqlChars.Stream Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="ffcfb-125">System.Data.SqlTypes.SqlStreamChars Constructor</span><span class="sxs-lookup"><span data-stu-id="ffcfb-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="ffcfb-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="ffcfb-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="ffcfb-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="ffcfb-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="ffcfb-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="ffcfb-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="ffcfb-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="ffcfb-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="ffcfb-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="ffcfb-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="ffcfb-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="ffcfb-137">System.Net.Connection Class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="ffcfb-138">System.Net.Connection.m\_WriteList Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="ffcfb-139">System.Net.ConnectionGroup Class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="ffcfb-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="ffcfb-141">System.Net.ConnectStream.Connection Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="ffcfb-142">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="ffcfb-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="ffcfb-144">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="ffcfb-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="ffcfb-146">System.Net.HttpWebRequest.\_CoreResponse Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="ffcfb-147">System.Net.HttpWebRequest.\_HttpResponse Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="ffcfb-148">System.Net.PooledStream.NetworkStream Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="ffcfb-149">System.Net.RtcState class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="ffcfb-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="ffcfb-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="ffcfb-152">System.Net.TlsStream.m_Worker Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="ffcfb-153">System.Net.Security.SslState.SslProtocol Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="ffcfb-154">System.ServiceModel.Channels.Message.BodyToString Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="ffcfb-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="ffcfb-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="ffcfb-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="ffcfb-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="ffcfb-158">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="ffcfb-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="ffcfb-159">System.Xml.XmlReader.CreateSqlReader Method</span><span class="sxs-lookup"><span data-stu-id="ffcfb-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="ffcfb-160">adodb.Connection Interface</span><span class="sxs-lookup"><span data-stu-id="ffcfb-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="ffcfb-161">adodb.EventReason Enum</span><span class="sxs-lookup"><span data-stu-id="ffcfb-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="ffcfb-162">adodb.EventStatus Enum</span><span class="sxs-lookup"><span data-stu-id="ffcfb-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="ffcfb-163">stdole.DISPPARAMS Structure</span><span class="sxs-lookup"><span data-stu-id="ffcfb-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="ffcfb-164">stdole.EXCEPINFO Structure</span><span class="sxs-lookup"><span data-stu-id="ffcfb-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="ffcfb-165">stdole.IFont.Name Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="ffcfb-166">stdole.IFontDisp Interface</span><span class="sxs-lookup"><span data-stu-id="ffcfb-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="ffcfb-167">stdole.IPicture.Handle Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="ffcfb-168">stdole.IPictureDisp.Handle Property</span><span class="sxs-lookup"><span data-stu-id="ffcfb-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="ffcfb-169">stdole.StdFont Interface</span><span class="sxs-lookup"><span data-stu-id="ffcfb-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="ffcfb-170">stdole.StdPicture Interface</span><span class="sxs-lookup"><span data-stu-id="ffcfb-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="ffcfb-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffcfb-171">See also</span></span>

* [<span data-ttu-id="ffcfb-172">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="ffcfb-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
