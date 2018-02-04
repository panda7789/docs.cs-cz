---
title: "Protokoly zasílání zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 75a39fa1d0301a48cec7ad61c968ee3fc82d189c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="messaging-protocols"></a><span data-ttu-id="76759-102">Protokoly zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-102">Messaging Protocols</span></span>
<span data-ttu-id="76759-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanál zásobníku využívá kódování a přenos kanály transformace reprezentace interní zprávy do jeho přenosový formát a odesílat je pomocí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="76759-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="76759-104">Nejběžnější přenos používá funkční spolupráce při webové služby, je HTTP, a nejběžnější kódování používá webové služby jsou na základě XML SOAP 1.1, SOAP 1.2 a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="76759-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="76759-105">Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podrobnosti implementace pro následující protokoly zaměstnaní <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="76759-105">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="76759-106">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="76759-106">Specification/document</span></span>|<span data-ttu-id="76759-107">Odkaz</span><span class="sxs-lookup"><span data-stu-id="76759-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="76759-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="76759-108">HTTP 1.1</span></span>|<span data-ttu-id="76759-109">http://www.ietf.org/rfc/rfc2616.txt</span><span class="sxs-lookup"><span data-stu-id="76759-109">http://www.ietf.org/rfc/rfc2616.txt</span></span>|  
|<span data-ttu-id="76759-110">SOAP 1.1 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="76759-110">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="76759-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span><span class="sxs-lookup"><span data-stu-id="76759-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="76759-112">SOAP 1.2 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="76759-112">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="76759-113">http://www.w3.org/TR/soap12-part2/, Section 7</span><span class="sxs-lookup"><span data-stu-id="76759-113">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="76759-114">Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace podrobnosti pro následující protokoly <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívají.</span><span class="sxs-lookup"><span data-stu-id="76759-114">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="76759-115">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="76759-115">Specification/Document</span></span>|<span data-ttu-id="76759-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="76759-116">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="76759-117">XML</span><span class="sxs-lookup"><span data-stu-id="76759-117">XML</span></span>|<span data-ttu-id="76759-118">http://www.w3.org/TR/REC-xml</span><span class="sxs-lookup"><span data-stu-id="76759-118">http://www.w3.org/TR/REC-xml</span></span>|  
|<span data-ttu-id="76759-119">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="76759-119">SOAP 1.1</span></span>|<span data-ttu-id="76759-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span><span class="sxs-lookup"><span data-stu-id="76759-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span></span>|  
|<span data-ttu-id="76759-121">SOAP 1.2 jádra</span><span class="sxs-lookup"><span data-stu-id="76759-121">SOAP 1.2 Core</span></span>|<span data-ttu-id="76759-122">http://www.w3.org/TR/soap12-part1/</span><span class="sxs-lookup"><span data-stu-id="76759-122">http://www.w3.org/TR/soap12-part1/</span></span>|  
|<span data-ttu-id="76759-123">Adresování WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="76759-123">WS-Addressing 2004/08</span></span>|<span data-ttu-id="76759-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span><span class="sxs-lookup"><span data-stu-id="76759-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span></span>|  
|<span data-ttu-id="76759-125">W3C webových služeb adresování 1.0 – základní</span><span class="sxs-lookup"><span data-stu-id="76759-125">W3C Web Services Addressing 1.0 - Core</span></span>|<span data-ttu-id="76759-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span><span class="sxs-lookup"><span data-stu-id="76759-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span></span>|  
|<span data-ttu-id="76759-127">W3C webových služeb adresování 1.0 - vazby protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="76759-127">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|<span data-ttu-id="76759-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span><span class="sxs-lookup"><span data-stu-id="76759-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span></span>|  
|<span data-ttu-id="76759-129">W3C webových služeb adresování 1.0 - vazby WSDL</span><span class="sxs-lookup"><span data-stu-id="76759-129">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|<span data-ttu-id="76759-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span><span class="sxs-lookup"><span data-stu-id="76759-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span></span>|  
<span data-ttu-id="76759-131">W3C webových služeb adresování 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="76759-131">W3C Web Services Addressing 1.0 - Metadata</span></span>|<span data-ttu-id="76759-132">http://www.w3.org/TR/ws-addr-metadata/</span><span class="sxs-lookup"><span data-stu-id="76759-132">http://www.w3.org/TR/ws-addr-metadata/</span></span>|  
|<span data-ttu-id="76759-133">Vazba SOAP1.1 WSDL</span><span class="sxs-lookup"><span data-stu-id="76759-133">WSDL SOAP1.1 Binding</span></span>|<span data-ttu-id="76759-134">http://www.w3.org/TR/wsdl/</span><span class="sxs-lookup"><span data-stu-id="76759-134">http://www.w3.org/TR/wsdl/</span></span>|  
|<span data-ttu-id="76759-135">Vazba SOAP1.2 WSDL</span><span class="sxs-lookup"><span data-stu-id="76759-135">WSDL SOAP1.2 Binding</span></span>|<span data-ttu-id="76759-136">http://www.w3.org/Submission/wsdl11soap12/</span><span class="sxs-lookup"><span data-stu-id="76759-136">http://www.w3.org/Submission/wsdl11soap12/</span></span>|  
  
 <span data-ttu-id="76759-137">Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace podrobnosti pro následující protokoly <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívá.</span><span class="sxs-lookup"><span data-stu-id="76759-137">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="76759-138">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="76759-138">Specification/document</span></span>|<span data-ttu-id="76759-139">Odkaz</span><span class="sxs-lookup"><span data-stu-id="76759-139">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="76759-140">XOP</span><span class="sxs-lookup"><span data-stu-id="76759-140">XOP</span></span>|<span data-ttu-id="76759-141">http://www.w3.org/TR/xop10/</span><span class="sxs-lookup"><span data-stu-id="76759-141">http://www.w3.org/TR/xop10/</span></span>|  
|<span data-ttu-id="76759-142">MTOM + SOAP 1.2 vazby</span><span class="sxs-lookup"><span data-stu-id="76759-142">MTOM + SOAP 1.2 Binding</span></span>|<span data-ttu-id="76759-143">http://www.w3.org/TR/soap12-mtom/</span><span class="sxs-lookup"><span data-stu-id="76759-143">http://www.w3.org/TR/soap12-mtom/</span></span>|  
|<span data-ttu-id="76759-144">MTOM SOAP 1.1 vazby</span><span class="sxs-lookup"><span data-stu-id="76759-144">MTOM SOAP 1.1 Binding</span></span>|<span data-ttu-id="76759-145">http://www.w3.org/Submission/soap11mtom10/</span><span class="sxs-lookup"><span data-stu-id="76759-145">http://www.w3.org/Submission/soap11mtom10/</span></span>|  
|<span data-ttu-id="76759-146">Výraz WS-zásad MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-146">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="76759-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="76759-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="76759-148">Následující obory názvů XML a přidružené předpony se používají v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="76759-148">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="76759-149">Předpona</span><span class="sxs-lookup"><span data-stu-id="76759-149">Prefix</span></span>|<span data-ttu-id="76759-150">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="76759-150">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="76759-151">s11</span><span class="sxs-lookup"><span data-stu-id="76759-151">s11</span></span>|<span data-ttu-id="76759-152">http://schemas.xmlsoap.org/soap/envelope</span><span class="sxs-lookup"><span data-stu-id="76759-152">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="76759-153">s12</span><span class="sxs-lookup"><span data-stu-id="76759-153">s12</span></span>|<span data-ttu-id="76759-154">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="76759-154">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="76759-155">wsa</span><span class="sxs-lookup"><span data-stu-id="76759-155">wsa</span></span>|<span data-ttu-id="76759-156">http://www.w3.org/2004/08/addressing</span><span class="sxs-lookup"><span data-stu-id="76759-156">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="76759-157">wsam</span><span class="sxs-lookup"><span data-stu-id="76759-157">wsam</span></span>|<span data-ttu-id="76759-158">http://www.w3.org/2007/05/addressing/metadata</span><span class="sxs-lookup"><span data-stu-id="76759-158">http://www.w3.org/2007/05/addressing/metadata</span></span>|  
|<span data-ttu-id="76759-159">wsap</span><span class="sxs-lookup"><span data-stu-id="76759-159">wsap</span></span>|<span data-ttu-id="76759-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span><span class="sxs-lookup"><span data-stu-id="76759-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span></span>|  
|<span data-ttu-id="76759-161">wsa10</span><span class="sxs-lookup"><span data-stu-id="76759-161">wsa10</span></span>|<span data-ttu-id="76759-162">http://www.w3.org/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="76759-162">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="76759-163">wsaw10</span><span class="sxs-lookup"><span data-stu-id="76759-163">wsaw10</span></span>|<span data-ttu-id="76759-164">http://www.w3.org/2006/05/addressing/wsdl</span><span class="sxs-lookup"><span data-stu-id="76759-164">http://www.w3.org/2006/05/addressing/wsdl</span></span>|  
|<span data-ttu-id="76759-165">XOP</span><span class="sxs-lookup"><span data-stu-id="76759-165">xop</span></span>|<span data-ttu-id="76759-166">http://www.w3.org/2004/08/xop/include</span><span class="sxs-lookup"><span data-stu-id="76759-166">http://www.w3.org/2004/08/xop/include</span></span>|  
|<span data-ttu-id="76759-167">xmime</span><span class="sxs-lookup"><span data-stu-id="76759-167">xmime</span></span>|<span data-ttu-id="76759-168">http://www.w3.org/2004/06/xmlmime</span><span class="sxs-lookup"><span data-stu-id="76759-168">http://www.w3.org/2004/06/xmlmime</span></span><br /><br /> <span data-ttu-id="76759-169">http://www.w3.org/2005/05/xmlmime</span><span class="sxs-lookup"><span data-stu-id="76759-169">http://www.w3.org/2005/05/xmlmime</span></span>|  
<span data-ttu-id="76759-170">dp</span><span class="sxs-lookup"><span data-stu-id="76759-170">dp</span></span>|<span data-ttu-id="76759-171">http://schemas.microsoft.com/net/2006/06/duplex</span><span class="sxs-lookup"><span data-stu-id="76759-171">http://schemas.microsoft.com/net/2006/06/duplex</span></span>|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="76759-172">SOAP 1.1 a SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="76759-172">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="76759-173">Obálky a zpracování modelu</span><span class="sxs-lookup"><span data-stu-id="76759-173">Envelope and Processing Model</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-174">implementuje zpracování obálky protokolu SOAP 1.1 Basic Profile 1.1 (základní parametr 11) a základní profil 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="76759-174">implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="76759-175">SOAP 1.2 obálky zpracování je implementována následující část SOAP12-1.</span><span class="sxs-lookup"><span data-stu-id="76759-175">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="76759-176">Tato část popisuje některé volby implementace provedenou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s ohledem na základní parametr 11 a část SOAP12-1.</span><span class="sxs-lookup"><span data-stu-id="76759-176">This section explains certain implementation choices taken by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="76759-177">Zpracování povinnou hlavičku</span><span class="sxs-lookup"><span data-stu-id="76759-177">Mandatory Header Processing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-178">dodržuje pravidla pro zpracování hlavičky označena `mustUnderstand` popsané v protokolu SOAP 1.1 a SOAP 1.2 specifikace, s následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="76759-178">follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="76759-179">Zprávu, která přejde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál zásobníku zpracovává jednotlivé kanály nakonfiguroval prvky přidružené vazeb, například, kódování textu zprávy, zabezpečení, spolehlivé zasílání zpráv a transakce.</span><span class="sxs-lookup"><span data-stu-id="76759-179">A message that enters the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="76759-180">Každý kanál rozpozná hlavičky z přidružených oboru názvů a označí je jako rozumí.</span><span class="sxs-lookup"><span data-stu-id="76759-180">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="76759-181">Jakmile zprávu zadá dispečera, přečte operaci formátování záhlaví očekávanou odpovídající kontrakt zprávy nebo operaci a značky, které jim rozumím jim.</span><span class="sxs-lookup"><span data-stu-id="76759-181">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="76759-182">Pak dispečera ověřuje, zda nejsou žádné zbývající hlavičky rozumí ale označen jako `mustUnderstand` a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="76759-182">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="76759-183">Zprávy, které obsahují `mustUnderstand` hlavičky, které jsou zaměřeny na příjemce nejsou zpracovávány kód příjemce aplikace.</span><span class="sxs-lookup"><span data-stu-id="76759-183">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="76759-184">Například vrstvený zpracování umožňuje oddělení mezi infrastruktury vrstvy a aplikaci vrstvy protokolu SOAP uzlu:</span><span class="sxs-lookup"><span data-stu-id="76759-184">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="76759-185">B1111: Hlavičky, které nejsou rozumí se zjistí po zpracovává zprávy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zásobník kanál infrastruktury, ale předtím, než je zpracován aplikací</span><span class="sxs-lookup"><span data-stu-id="76759-185">B1111: Headers that are not understood are detected after the message is processed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="76759-186">`mustUnderstand` Hodnota hlavičky se liší mezi SOAP 1.1 a SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="76759-186">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="76759-187">Basic Profile 1.1 vyžaduje, aby `mustUnderstand` hodnota být 0 nebo 1 pro zprávy SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="76759-187">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="76759-188">SOAP 1.2 umožňuje 0, 1, `false`, a `true` hodnoty, ale doporučuje emitování kanonický reprezentace `xs:boolean` hodnoty (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="76759-188">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="76759-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vysílá `mustUnderstand` hodnoty 0 a 1 pro verze protokolu SOAP 1.1 a SOAP 1.2 obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="76759-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="76759-190">přijímá prostor celou hodnotu `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="76759-190"> accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="76759-191">Chyb SOAP</span><span class="sxs-lookup"><span data-stu-id="76759-191">SOAP Faults</span></span>  
 <span data-ttu-id="76759-192">Následuje seznam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-konkrétní implementace chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="76759-192">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="76759-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrátí následující kódy chyb protokolu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, a `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="76759-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="76759-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrátí následující kódy chyb protokolu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, a `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="76759-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="76759-195">Vazba HTTP</span><span class="sxs-lookup"><span data-stu-id="76759-195">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="76759-196">SOAP 1.1 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="76759-196">SOAP 1.1 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-197">implementuje vazby SOAP1.1 HTTP následující specifikace Basic Profile 1.1 oddíl 3.4 objasnění následující:</span><span class="sxs-lookup"><span data-stu-id="76759-197">implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="76759-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby neimplementuje přesměrování požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="76759-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="76759-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienti podporují soubory cookie protokolu HTTP v souladu s 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="76759-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="76759-200">SOAP 1.2 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="76759-200">SOAP 1.2 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-201">jak je popsáno v protokolu SOAP 1.2 část 2 (SOAP12Part2) specifikace s následující objasnění, implementuje vazby protokolu SOAP 1.2 HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-201">implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="76759-202">Parametr volitelné akce pro zavedená SOAP 1.2 `application/soap+xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="76759-202">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="76759-203">Tento parametr je užitečné k optimalizaci odesílání zpráv bez nutnosti analyzovat do těla protokolu SOAP zprávy při adresování WS nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="76759-203">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="76759-204">R2221: `application/soap+xml` parametr akce, pokud jsou k dispozici na vyžádání SOAP 1.2, musí odpovídat `soapAction` atributu u `wsoap12:operation` prvku v odpovídající vazby WSDL.</span><span class="sxs-lookup"><span data-stu-id="76759-204">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="76759-205">R2222: `application/soap+xml` parametr akce, pokud jsou k dispozici na zprávu protokolu SOAP 1.2 musí odpovídat `wsa:Action` při použití služby WS-Addressing 2004/08 nebo WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="76759-205">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="76759-206">Když WS-Addressing je zakázána a příchozí požadavek neobsahuje parametr akce, zprávy `Action` považuje za není zadaný.</span><span class="sxs-lookup"><span data-stu-id="76759-206">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="76759-207">Adresování WS</span><span class="sxs-lookup"><span data-stu-id="76759-207">WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-208">implementuje 3 verze WS adresování:</span><span class="sxs-lookup"><span data-stu-id="76759-208">implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="76759-209">Adresování WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="76759-209">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="76759-210">Adresování 1.0 jádra (ADDR10-jader) a vazbu (ADDR10 protokolu SOAP) SOAP W3C webové služby</span><span class="sxs-lookup"><span data-stu-id="76759-210">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="76759-211">Adresování WS 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="76759-211">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="76759-212">Odkazy na koncový bod</span><span class="sxs-lookup"><span data-stu-id="76759-212">Endpoint References</span></span>  
 <span data-ttu-id="76759-213">Všechny verze WS-Addressing který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje pomocí koncového bodu odkazy popisují koncové body.</span><span class="sxs-lookup"><span data-stu-id="76759-213">All versions of WS-Addressing that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="76759-214">Odkazy na koncový bod a adresování WS verze</span><span class="sxs-lookup"><span data-stu-id="76759-214">Endpoint References and WS-Addressing Versions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-215">implementuje číslo infrastruktury protokolů, které používají služby WS-Addressing, zejména `EndpointReference` elementu a `W3C.WsAddressing.EndpointReferenceType` – třída (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="76759-215">implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="76759-216">podporuje použití buď verzi WS-Addressing s ostatními protokoly infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="76759-216"> supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="76759-217">Koncové body podporovat jednu verzi WS-Addressing na jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-217"> endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="76759-218">Pro R3111, obor názvů pro `EndpointReference` element nebo typ použitý v zprávy se vyměňují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncového bodu musí odpovídat verzi WS adresování implementované tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-218">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="76759-219">Například pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje koncový bod protokolu WS-ReliableMessaging `AcksTo` hlavička bodem uvnitř `CreateSequenceResponse` používá verzi WS-Addressing, `EncodingBinding` element určuje pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-219">For example, if a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="76759-220">Odkazy na koncový bod a Metadata</span><span class="sxs-lookup"><span data-stu-id="76759-220">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="76759-221">Různé scénáře vyžadují komunikaci metadata nebo odkaz na metadata pro daný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-221">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="76759-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] využívá mechanismy popsána ve specifikaci WS-MetadataExchange (MEX) část 6 Zahrnout metadata pro koncový bod odkazy hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="76759-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="76759-223">Zvažte scénář, kde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba vyžaduje, aby ověření pomocí tokenu zabezpečení kontrolní výrazy Markup Language (SAML) vydaný vydavatel tokenu v http://sts.fabrikam123.com. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Koncový bod popisuje tento požadavek ověřování pomocí `sp:IssuedToken` kontrolní výraz s vnořeným `sp:Issuer` assertion odkazující na vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="76759-223">Consider a scenario where a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="76759-224">Klientských aplikací, které přístup `sp:Issuer` assertion muset vědět, jak ke komunikaci s koncovým bodem tokenu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="76759-224">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="76759-225">Klient musí vědět, metadata o vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="76759-225">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="76759-226">Pomocí rozšíření koncový bod odkaz metadata definovaná v MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje odkaz na metadata vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="76759-226">Using the endpoint reference metadata extensions defined in MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a reference to the token issuer metadata.</span></span>  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a><span data-ttu-id="76759-227">Adresování hlavičky zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-227">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="76759-228">Hlavičky zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-228">Message Headers</span></span>  
 <span data-ttu-id="76759-229">Pro obě verze WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá následující záhlaví zprávy podle specifikace `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, a `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="76759-229">For both WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="76759-230">B3211: pro všechny verze WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ctí, ale nevytváří předinstalované, WS-Addressing hlavičky zpráv `wsa:FaultTo` a `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="76759-230">B3211: For all WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="76759-231">Aplikace, které spolupracují s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace můžete přidat tyto zprávy hlavičky a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jejich zpracování odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="76759-231">Applications that interact with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can add these message headers and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="76759-232">Odkaz na parametry a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76759-232">Reference Parameters and Properties</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-233">implementuje zpracování parametrů odkaz na koncový bod a p – referenční informace</span><span class="sxs-lookup"><span data-stu-id="76759-233">implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="76759-234">vlastnosti v souladu s příslušnými specifikace.</span><span class="sxs-lookup"><span data-stu-id="76759-234">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="76759-235">B3221: Pokud nakonfigurovaná pro použití služby WS-Addressing 2004/08 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body nerozlišují mezi zpracování vlastnosti odkazu a odkaz na parametry.</span><span class="sxs-lookup"><span data-stu-id="76759-235">B3221: When configured to use WS-Addressing 2004/08, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="76759-236">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-236">Message Exchange Patterns</span></span>  
 <span data-ttu-id="76759-237">Pořadí zpráv zahrnutých v operaci volání webové služby se označuje jako *vzorce výměny zpráv*.</span><span class="sxs-lookup"><span data-stu-id="76759-237">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="76759-238">podporuje jednosměrné, požadavku a odpovědi a duplexní zprávu výměna vzory.</span><span class="sxs-lookup"><span data-stu-id="76759-238"> supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="76759-239">Tato část vysvětluje, WS-Addressing požadavky na zpracování v závislosti na vzorce výměny zpráv používá zpráv.</span><span class="sxs-lookup"><span data-stu-id="76759-239">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="76759-240">V této části žadatel odešle první zprávy a příjemce obdrží první zprávu.</span><span class="sxs-lookup"><span data-stu-id="76759-240">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="76759-241">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-241">One-Way Message</span></span>  
 <span data-ttu-id="76759-242">Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod je nakonfigurován pro podporu zprávy s dané `Action` sledovat jednosměrného vzor, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod dodržuje následující požadavky a chování.</span><span class="sxs-lookup"><span data-stu-id="76759-242">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="76759-243">Pokud není uvedeno jinak, chování a pravidla platí pro obě verze WS-Addressing podporované v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="76759-243">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="76759-244">R3311: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`a hlavičky pro všechny parametry odkaz určeného odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-244">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="76759-245">Když se používá WS-Addressing 2004/08 a [Vlastnosti odkazu] jsou určené odkaz na koncový bod odpovídající hlavičky musí být přidaný do zprávy příliš.</span><span class="sxs-lookup"><span data-stu-id="76759-245">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="76759-246">B3312: Žadatel může zahrnovat `MessageID`, `ReplyTo`, a `FaultTo` hlavičky.</span><span class="sxs-lookup"><span data-stu-id="76759-246">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="76759-247">Příjemce infrastruktury je bude ignorovat a se předají do aplikace.</span><span class="sxs-lookup"><span data-stu-id="76759-247">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="76759-248">R3313: Když se používá protokol HTTP a odesílání žádné zprávy na větev odpověď HTTP, musíte odeslat odpovídající počítač s prázdným textem zprávy a HTTP 202 stavový kód HTTP odpovědi.</span><span class="sxs-lookup"><span data-stu-id="76759-248">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="76759-249">Pokud přenos HTTP je používán a kontrakt operaci deklaruje zprávu jednosměrné, odpověď HTTP pořád můžou použít pro odesílání zpráv infrastruktury – například může odesílat spolehlivé zasílání zpráv `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-249">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="76759-250">B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér neodesílá zprávu o chybě v odpovědi na zprávu jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="76759-250">B3314: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="76759-251">Požadavek a odpověď</span><span class="sxs-lookup"><span data-stu-id="76759-251">Request-Reply</span></span>  
 <span data-ttu-id="76759-252">Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod je nakonfigurován pro zprávu s danou `Action` podle vzoru požadavku a odpovědi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod řídí chování a požadavky uvedené níže.</span><span class="sxs-lookup"><span data-stu-id="76759-252">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="76759-253">Pokud není uvedeno jinak, chování a pravidla platí pro obě verze WS-Addressing podporované v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="76759-253">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="76759-254">R3321: Žadatel musí zahrnovat v požadavku `wsa:To`, `wsa:Action`, `wsa:MessageID`, tak i hlaviček pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-254">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="76759-255">R3322: Pokud je použita WS-Addressing 2004/08, `ReplyTo` musí také obsahovat žádosti.</span><span class="sxs-lookup"><span data-stu-id="76759-255">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="76759-256">R3323: Pokud se používá WS-Addressing 1.0 a `ReplyTo` není přítomný v požadavku, odkaz na výchozí koncový bod s rovno "http://www.w3.org/2005/08/addressing/anonymous" [address] vlastnost se používá.</span><span class="sxs-lookup"><span data-stu-id="76759-256">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="76759-257">R3324: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`, a `wsa:RelatesTo` hlavičky v odpovědi, jakož i hlavičky pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného `ReplyTo` odkaz na koncový bod v požadavek.</span><span class="sxs-lookup"><span data-stu-id="76759-257">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="76759-258">Webové služby adresování chyb</span><span class="sxs-lookup"><span data-stu-id="76759-258">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="76759-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vytváří následující chyb definované WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="76759-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="76759-260">Kód</span><span class="sxs-lookup"><span data-stu-id="76759-260">Code</span></span>|<span data-ttu-id="76759-261">příčina</span><span class="sxs-lookup"><span data-stu-id="76759-261">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="76759-262">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="76759-262">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="76759-263">Zpráva dorazila po uplynutí `ReplyTo` , se liší od navázána pro tento kanál adresu; neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.</span><span class="sxs-lookup"><span data-stu-id="76759-263">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="76759-264">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="76759-264">wsa:ActionNotSupported</span></span>|<span data-ttu-id="76759-265">kanály infrastruktury nebo dispečera přiřazené ke koncovému bodu nerozpoznávají zadaná v akci `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="76759-265">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="76759-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vytváří následující chyb definované WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="76759-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="76759-267">Kód</span><span class="sxs-lookup"><span data-stu-id="76759-267">Code</span></span>|<span data-ttu-id="76759-268">příčina</span><span class="sxs-lookup"><span data-stu-id="76759-268">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="76759-269">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="76759-269">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="76759-270">Duplicitní `wsa:To`, `wsa:ReplyTo`, `wsa:From` nebo `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="76759-270">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="76759-271">Duplicitní `wsa:RelatesTo` se stejným `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="76759-271">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="76759-272">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="76759-272">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="76759-273">Požadovaná hlavička Addressing nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="76759-273">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="76759-274">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="76759-274">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="76759-275">Zpráva dorazila po uplynutí `ReplyTo` která se liší od navázána pro tento kanál adresu.</span><span class="sxs-lookup"><span data-stu-id="76759-275">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="76759-276">Neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.</span><span class="sxs-lookup"><span data-stu-id="76759-276">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="76759-277">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="76759-277">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="76759-278">Zadaná v akci `Action` hlavička nebyla rozpoznána infrastruktury kanály nebo dispečera přiřazené ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="76759-278">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="76759-279">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="76759-279">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="76759-280">Kanál RM odešle tato porucha zpět, označující koncový bod nezpracuje pořadí na základě zkoumání `CreateSequence` zprávu o adrese hlavičky.</span><span class="sxs-lookup"><span data-stu-id="76759-280">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="76759-281">Kód v předchozích tabulkách se mapuje na `FaultCode` v SOAP 1.1 a `SubCode` (s kódem = odesílatele) v protokolu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="76759-281">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="76759-282">WSDL 1.1 vazby a WS-Policy kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="76759-282">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="76759-283">Označující použití adresování WS</span><span class="sxs-lookup"><span data-stu-id="76759-283">Indicating Use of WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-284">koncový bod podporu pro konkrétní verzi WS-Addressing použije výrazy zásad.</span><span class="sxs-lookup"><span data-stu-id="76759-284">uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="76759-285">Následující výraz zásad má koncový bod zásad subjektu [WS-PA] a znamená, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="76759-285">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="76759-286">Tento výraz zásad argumentech specifikace WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="76759-286">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="76759-287">Následující výraz zásad, že to znamená, že který zprávy odeslat/přijmout musí používat WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="76759-287">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="76759-288">Následující výraz zásad má předmět zásad služby Endpoint [WS-PA] a označuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="76759-288">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="76759-289">`wsaw10:UsingAddressing` Elementu je vždy pouze vypůjčí na [WS-adresování-WSDL] a je použita v kontextu služby WS-Policy v souladu s této specifikaci se v části 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="76759-289">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="76759-290">Použití Addressing nezmění sémantika WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazby.</span><span class="sxs-lookup"><span data-stu-id="76759-290">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="76759-291">Například pokud je odpověď na žádost, kterou posílá koncový bod, který používá Addressing a WSDL SOAP vazby HTTP 1.x očekávána, musí se odpovědi poslat pomocí odpověď HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-291">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="76759-292">Pro odpovědi, odešlou přes odpověď http WS-AM kontrolní výraz je:</span><span class="sxs-lookup"><span data-stu-id="76759-292">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="76759-293">Výraz dokončení zásad může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="76759-293">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="76759-294">Existují však vzory exchange zprávu, využívající má dva nezávislé konverzace HTTP připojení mezi žadatel a respondér, například nevyžádané jednosměrný zprávy odeslané respondér.</span><span class="sxs-lookup"><span data-stu-id="76759-294">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-295">nabízí funkce, pomocí kterého můžete dvě základní přenosové kanály formuláři složené duplexní kanál, kde jeden kanál je používána pro vstupní zprávy a druhý je používána pro zprávy výstup.</span><span class="sxs-lookup"><span data-stu-id="76759-295">offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="76759-296">V případě přenos HTTP poskytuje složené duplexní dvě připojení HTTP konverzace.</span><span class="sxs-lookup"><span data-stu-id="76759-296">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="76759-297">Žadatel používá jedno připojení k odesílání zpráv do odpovídající partner a odpovídající partner dalších odesílání zprávy zpět na žadatel.</span><span class="sxs-lookup"><span data-stu-id="76759-297">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="76759-298">Pro odpovědi, odešlou přes požadavky http samostatné ws-am kontrolní výraz je</span><span class="sxs-lookup"><span data-stu-id="76759-298">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="76759-299">Výraz dokončení zásad může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="76759-299">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="76759-300">Následující kontrolní výraz, který má koncový bod zásad subjektu [WS-PA] na koncové body, které pomocí vazby HTTP 1.x WSDL 1.1 SOAP vyžaduje dva samostatné konverzace připojení protokolu HTTP má být použit pro zpráv předávaných z žadatel respondér a respondér k žadatel, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="76759-300">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="76759-301">Předchozí příkaz vede k následující požadavky `wsa:ReplyTo` hlavičky pro žádosti o zprávy:</span><span class="sxs-lookup"><span data-stu-id="76759-301">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="76759-302">R3514: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost "http://www.w3.org/2005/08/addressing/anonymous" není rovno, pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má alternativní zásady s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` assertion kombinaci s `cdp:CompositeDuplex` připojen.</span><span class="sxs-lookup"><span data-stu-id="76759-302">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="76759-303">R3515: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous", nebo není `ReplyTo` záhlaví na všechny, pokud koncový bod používá WSDL 1.1 SOAP 1.x HTTP vazby a má zásadu alternativní s `wsap10:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` assertion připojen.</span><span class="sxs-lookup"><span data-stu-id="76759-303">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="76759-304">R3516: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má zásadu alternativní s `wsap:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` assertion připojen.</span><span class="sxs-lookup"><span data-stu-id="76759-304">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="76759-305">Specifikace WS-addressing WSDL pokusí popisují podobné vazby protokolu zavedením element `<wsaw:Anonymous/>` s tři textové hodnoty (vyžaduje, volitelné a zakázané) k označení požadavky na `wsa:ReplyTo` hlavičky (část 3.2).</span><span class="sxs-lookup"><span data-stu-id="76759-305">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="76759-306">Bohužel taková definice elementu není zvlášť jako kontrolní výrazy v kontextu služby WS-zásad, protože vyžaduje rozšíření specifické pro doménu, které podporují průnik alternativy pomocí takový prvek jako kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="76759-306">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="76759-307">Taková definice elementu také určuje hodnota `ReplyTo` záhlaví oproti chování koncového bodu v drátové síti, takže je konkrétní přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-307">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="76759-308">Definice akce</span><span class="sxs-lookup"><span data-stu-id="76759-308">Action Definition</span></span>  
 <span data-ttu-id="76759-309">Definuje WS-Addressing 2004/08 `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy.</span><span class="sxs-lookup"><span data-stu-id="76759-309">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="76759-310">Adresování WS 1.0 WSDL vazby (WS-ADDR10-WSDL) definuje atribut podobné `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="76759-310">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="76759-311">Jediným rozdílem mezi těmito dvěma je sémantiky vzor výchozí akce popsané v 3.3.2 WS-ADDR a oddílu bodu 4.4.4 WS-ADDR10-WSDL, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="76759-311">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="76759-312">Je možné logicky tak, aby měl dva koncové body, které sdílejí stejné `portType` (nebo kontrakt, v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologie), ale používání různých verzí WS adres.</span><span class="sxs-lookup"><span data-stu-id="76759-312">It is a reasonable to have two endpoints that share the same `portType` (or contract, in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="76759-313">Ale vzhledem k tomu, že je definována akce `portType` a neměli měnit napříč koncovými body, které implementují `portType`, bude možné podporovat i výchozí akci zpracování.</span><span class="sxs-lookup"><span data-stu-id="76759-313">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="76759-314">Chcete-li vyřešit tento sporům [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje jednu verzi `Action` atribut.</span><span class="sxs-lookup"><span data-stu-id="76759-314">To resolve this controversy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="76759-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá `wsaw10:Action` atributu u `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` dle WS-ADDR10-WSDL k určení `Action` identifikátor URI pro odpovídající zprávy, bez ohledu na verzi WS-Addressing používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="76759-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="76759-316">Použití koncový bod odkaz uvnitř WSDL portu</span><span class="sxs-lookup"><span data-stu-id="76759-316">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="76759-317">WS-ADDR10-WSDL části 4.1 rozšiřuje `wsdl:port` elementu, který chcete zahrnout `<wsa10:EndpointReference…/>` podřízený element k popisu koncový bod v WS-Addressing podmínky.</span><span class="sxs-lookup"><span data-stu-id="76759-317">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="76759-318">rozšíří na adresování WS 2004/08, tento nástroj umožňuje `<wsa:EndpointReference…/>` vypadaly jako podřízeného prvku `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="76759-318"> expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="76759-319">R3531: Pokud koncový bod má alternativu připojené zásady s `<wsaw10:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="76759-319">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="76759-320">R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.</span><span class="sxs-lookup"><span data-stu-id="76759-320">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="76759-321">R3533: Pokud koncový bod má alternativu připojené zásady s `<wsap:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="76759-321">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="76759-322">R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.</span><span class="sxs-lookup"><span data-stu-id="76759-322">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="76759-323">Složení s WS-zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76759-323">Composition with WS-Security</span></span>  
 <span data-ttu-id="76759-324">Podle zabezpečení části aspekt WS-ADDR a WS-ADDR10 se doporučuje všechny adresování hlavičky zpráv být podepsané společně s text zprávy pro vazbu je společně.</span><span class="sxs-lookup"><span data-stu-id="76759-324">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="76759-325">Pokud WS-zabezpečení se používá pro ochranu integrity zprávy, musí být podepsané WS-Addressing zpráva hlavičky, jakož i hlavičky výsledkem parametry odkaz nebo vlastnosti (nebo obě) společně s tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="76759-325">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="76759-326">Příklady</span><span class="sxs-lookup"><span data-stu-id="76759-326">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="76759-327">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-327">One-Way Message</span></span>  
 <span data-ttu-id="76759-328">V tomto scénáři odesílatel odešle zprávu jednosměrný k příjemce.</span><span class="sxs-lookup"><span data-stu-id="76759-328">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="76759-329">SOAP 1.2, HTTP 1.1 a 1.0 W3C WS-Addressing se používají.</span><span class="sxs-lookup"><span data-stu-id="76759-329">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="76759-330">Struktura zprávu požadavku: Záhlaví zprávy zahrnují `wsa10:To` a `wsa10:Action` elementy.</span><span class="sxs-lookup"><span data-stu-id="76759-330">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="76759-331">Tělo zprávy obsahuje konkrétní `<app:Ping>` element z oboru názvů aplikace.</span><span class="sxs-lookup"><span data-stu-id="76759-331">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="76759-332">Hlavičky protokolu HTTP: Cíl v BLOGU odpovídá identifikátoru URI v `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="76759-332">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="76759-333">Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="76759-333">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="76759-334">Parametry `charset` a `action` jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="76759-334">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="76759-335">`action` Hodnota odpovídá parametru hlavičku Content-Type `wsa10:Action` záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="76759-335">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 <span data-ttu-id="76759-336">Příjemce odpoví s prázdnou odpověď HTTP a stav 202.</span><span class="sxs-lookup"><span data-stu-id="76759-336">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="76759-337">Příklad odpověď HTTP:</span><span class="sxs-lookup"><span data-stu-id="76759-337">An example of the HTTP response:</span></span>  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="76759-338">Mechanismus Optimalizace přenosu zpráv protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="76759-338">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="76759-339">Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podrobnosti implementace pro MTOM SOAP protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-339">This section describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="76759-340">Technologie MTOM je protokolu SOAP zprávy kódování mechanismus stejnou třídou jako kódování tradiční text/XML nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binárního kódování.</span><span class="sxs-lookup"><span data-stu-id="76759-340">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary encoding.</span></span> <span data-ttu-id="76759-341">MTOM zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="76759-341">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="76759-342">Kódování XML a mechanismus balení [XOP] popsaného který optimalizuje položky informace XML obsahující binární data s kódováním base64 na samostatné části binární.</span><span class="sxs-lookup"><span data-stu-id="76759-342">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="76759-343">MIME zapouzdření XOP balíčku, který serializuje informační sadu XML a každý binární součást balíčku XOP do samostatné části standardu MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-343">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="76759-344">MIME XOP kódování u SOAP 1.x obálku.</span><span class="sxs-lookup"><span data-stu-id="76759-344">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="76759-345">HTTP přenosu vazby.</span><span class="sxs-lookup"><span data-stu-id="76759-345">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="76759-346">Je možné použít MTOM s jiným protokolem než HTTP přenosy s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76759-346">It is possible to use MTOM with non-HTTP transports with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="76759-347">Ale v tomto tématu se zaměříme na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="76759-347">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="76759-348">Formát MTOM využívá velké sady specifikace, které se týkají MTOM sám sebe, XOP a MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-348">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="76759-349">Modularitu této sady specifikace ztěžuje poněkud rekonstrukci přesných požadavcích na sémantiku formátu a zpracování.</span><span class="sxs-lookup"><span data-stu-id="76759-349">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="76759-350">Tato část popisuje požadavky na zpracování a formát pro vazbu protokolu HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="76759-350">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="76759-351">Kódování MTOM zpráv</span><span class="sxs-lookup"><span data-stu-id="76759-351">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="76759-352">Generování zprávy MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-352">Generating MTOM messages</span></span>  
 <span data-ttu-id="76759-353">[XOP] části 3.1 popisuje proces kódování XML s položkami informace element, které obsahují hodnoty base64 do balíčku abstraktně definované XOP.</span><span class="sxs-lookup"><span data-stu-id="76759-353">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="76759-354">Následující pořadí kroků popisuje proces kódování MTOM konkrétní:</span><span class="sxs-lookup"><span data-stu-id="76759-354">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="76759-355">Zajistěte, aby obsahoval obálku protokolu SOAP kódovaný žádná položka informace o elementu s `[namespace name]` z "http://www.w3.org/2004/08/xop/include" a `[local name]` z `Include`.</span><span class="sxs-lookup"><span data-stu-id="76759-355">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="76759-356">Vytvořte prázdný balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-356">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="76759-357">Identifikujte v původní informační sadu XML položky informace o elementu, které chcete optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="76759-357">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="76759-358">Pro položky, které chcete optimalizovat, znaky, tvoří `[children]` informace o elementu položky musí být v kanonickém tvaru `xs:base64Binary` (viz XSD-2, 3.2.16 pomocí base64Binary) a nesmí obsahovat žádné prázdné znaky před vložením s, nebo Následující obsah neprázdný.</span><span class="sxs-lookup"><span data-stu-id="76759-358">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="76759-359">Vytvoří obálku protokolu SOAP XOP, který je kopií původního obálky protokolu SOAP, ale s podřízenými položkami každý element informací nahrazuje položku identifikovat v předchozím kroku `xop:Include` element informace položka vytvořená následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="76759-359">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="76759-360">Transformace nahrazené znaků do binární data zpracováním je jako data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="76759-360">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="76759-361">Generovat jedinečný hodnota hlavičky Content-ID, který splňuje požadavky R3133 a R3134.</span><span class="sxs-lookup"><span data-stu-id="76759-361">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="76759-362">Vygenerujte hlavička kódování přenosu obsahu MIME s binární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="76759-362">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="76759-363">Pokud se informace o položce element optimalizována ([nadřazený] nově vloženého `xop:Include` element informace položky) má `xmime:contentType` atribut položky informace, vygenerujte hlavičku Content-Type MIME s hodnotou `xmime:contentType` atribut.</span><span class="sxs-lookup"><span data-stu-id="76759-363">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="76759-364">Generovat nové části binární standardu MIME s obsahem tvořená binární data dekódovat z nahrazené znaky zpracovávány jako base64, Hlavička Content-ID ze 4b, Hlavička kódování přenosu obsahu ze 4c, Hlavička Content-Type, pokud vygenerované v kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="76759-364">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="76759-365">Přidat `href` atribut `xop:Include` element s hodnotou cid: identifikátor uri odvozené od hodnota hlavičky Content-ID vygenerované v kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="76759-365">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="76759-366">Odebrat uzavírací "\<" a ">" znaky adresy URL řídicí zbývající řetězec a přidat předponu `cid:`.</span><span class="sxs-lookup"><span data-stu-id="76759-366">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="76759-367">Je potřeba předcházet RFC1738 a RFC2396 následující minimální znakovou sadu.</span><span class="sxs-lookup"><span data-stu-id="76759-367">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="76759-368">Můžete uvozené jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="76759-368">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="76759-369">Vytvořte Kořenová část MIME s XOP obálku protokolu SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="76759-369">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="76759-370">Zápisu hlavičky protokolu HTTP, včetně hlavičku HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="76759-370">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="76759-371">Zápis balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-371">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="76759-372">Zpracování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-372">Processing MTOM messages</span></span>  
 <span data-ttu-id="76759-373">Zpracování MTOM zpráva je přesný zpětného procesu popsané v předchozím "generování MTOM zprávy" části:</span><span class="sxs-lookup"><span data-stu-id="76759-373">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="76759-374">Ujistěte se, má kořenová část MIME Content-Type `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="76759-374">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="76759-375">Vytvořte obálku protokolu SOAP analýzou kořenu MIME součást balíčku jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="76759-375">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="76759-376">Kódování znaků je dáno `charset` parametr Content-Type kořenové části MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-376">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="76759-377">Pro každou položku informace element v sestavené obálku protokolu SOAP, který má, jako jedinou člen jeho [podřízené položky] vlastnosti, `xop:Include` element informace položky:</span><span class="sxs-lookup"><span data-stu-id="76759-377">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="76759-378">Odeberte `cid:` předpony a unescape všechny URI – řídicí sekvence (RFC 2396) v hodnotě `@href` atribut `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="76759-378">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="76759-379">Uzavřete výsledný řetězec v "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="76759-379">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="76759-380">Vyhledejte část MIME s hodnota hlavičky Content-ID, který se shoduje s řetězcem odvozený v krok 3a.</span><span class="sxs-lookup"><span data-stu-id="76759-380">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="76759-381">Nahraďte `xop:Include` položky informace o elementu, který se zobrazí v `children` vlastnost každé položky se položky znak informace, které představují kódování base64 kanonický (viz XSD-2, 3.2.16 pomocí base64Binary) textu entity části standardu MIME v kroku 3b identifikuje (efektivně nahradit `xop:Include` položky informace o elementu s daty znovu vytvořena z součást balíčku).</span><span class="sxs-lookup"><span data-stu-id="76759-381">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="76759-382">Hlavičku HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="76759-382">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="76759-383">Následuje seznam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objasnění, která pro formát hlavičky protokolu HTTP Content-Type kódování MTOM zprávy protokolu SOAP 1.x odvozené od požadavky uvedené v specifikace MTOM sám a jsou odvozené z MTOM a dokumentu RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="76759-383">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="76759-384">R4131: Hlavičku HTTP Content-Type musí mít hodnotu multipart/related (velká a malá písmena) a jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="76759-384">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="76759-385">Názvy parametrů jsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="76759-385">Parameter names are case-insensitive.</span></span> <span data-ttu-id="76759-386">Parametr pořadí není důležité.</span><span class="sxs-lookup"><span data-stu-id="76759-386">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="76759-387">Úplné Backus-Naur formuláře (BNF) hlavičky Content-Type pro zprávy MIME je uvedena v chodu 2045 RFC, část 5.1.</span><span class="sxs-lookup"><span data-stu-id="76759-387">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="76759-388">R4132: Hlavičku HTTP Content-Type musí mít parametr typu s hodnotou `application/xop+xml` uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="76759-388">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="76759-389">Přestože není definován v dokumentu RFC 2387 požadavek na použijte uvozovky, text dodržuje, že všechny typu multipart/related média parametry nejpravděpodobnější obsahovat vyhrazené znaky jako "@" or "/" a je proto třeba dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="76759-389">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="76759-390">R4133: Hlavičku HTTP Content-Type musí mít parametr s hodnotou hlavičku Content-ID části standardu MIME, který obsahuje SOAP 1.x obálky, uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="76759-390">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="76759-391">Pokud je spuštění parametr vynechán, první část MIME musí obsahovat SOAP 1.x obálku.</span><span class="sxs-lookup"><span data-stu-id="76759-391">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="76759-392">R4134: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.1 MTOM kódovaný musí obsahovat úvodní informace parametr s hodnotou typu text/xml, uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="76759-392">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="76759-393">R4135: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.2 MTOM kódováním musí obsahovat úvodní informace parametr s hodnotou `application/soap+xml`, uzavřené v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="76759-393">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="76759-394">R4136: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.x kódování MTOM musí mít parametr hranic s hodnotou (uzavřena v uvozovkách), který odpovídá MIME hranice, na které BNF definované v dokumentu RFC 2046 části 5.1.1</span><span class="sxs-lookup"><span data-stu-id="76759-394">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="76759-395">Příklady:</span><span class="sxs-lookup"><span data-stu-id="76759-395">Examples:</span></span>  
  
     <span data-ttu-id="76759-396">OPRAVTE</span><span class="sxs-lookup"><span data-stu-id="76759-396">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="76759-397">OPRAVTE</span><span class="sxs-lookup"><span data-stu-id="76759-397">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="76759-398">NESPRÁVNÝ</span><span class="sxs-lookup"><span data-stu-id="76759-398">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="76759-399">Část MIME informační sadu</span><span class="sxs-lookup"><span data-stu-id="76759-399">Infoset MIME Part</span></span>  
 <span data-ttu-id="76759-400">SOAP 1.x obálky je zapouzdřený jako část kořenové XOP MIME balíčku a se často říká `infoset` část.</span><span class="sxs-lookup"><span data-stu-id="76759-400">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="76759-401">R4141: SOAP 1.x obálky musí zapouzdřené jako část kořenové XOP MIME balíčku, volá se `infoset` část a odkazované z hlavičku HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="76759-401">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="76759-402">R4142: SOAP `Infoset` část musí zahrnovat následující hlavičky MIME: `Content-ID`, `Content-Transfer-Encoding`, a `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="76759-402">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="76759-403">Formát hlavičky Content-ID je definované chodu 2045 RFC jako</span><span class="sxs-lookup"><span data-stu-id="76759-403">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="76759-404">kde `msg-id` je definován v dokumentu RFC 2822, (který nahrazuje RFC 822, kterou se odkazuje v chodu 2045 RFC) jako:</span><span class="sxs-lookup"><span data-stu-id="76759-404">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="76759-405">a efektivně e-mailovou adresu uzavřena v rámci "\<" a ">".</span><span class="sxs-lookup"><span data-stu-id="76759-405">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="76759-406">`[CFWS]` Předponu a příponu byly přidány RFC 2822 k provedení komentáře a nesmí se použít k zachování interoperability.</span><span class="sxs-lookup"><span data-stu-id="76759-406">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="76759-407">R4143: Musí následovat hodnota hlavičky Content-ID pro část MIME informační sadu `msg-id` produkční z RFC 2822 s `[CFWS]` předponu a příponu částí tento parametr vynechán.</span><span class="sxs-lookup"><span data-stu-id="76759-407">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="76759-408">Počet implementací MIME zmírnit požadavky pro hodnotu v rámci uzavřené "\<" a ">" jako e-mailovou adresu a použít `absoluteURI` v "\<", ">" Kromě e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="76759-408">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="76759-409">Tato verze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá hodnoty hlavičky Content-ID MIME ve tvaru:</span><span class="sxs-lookup"><span data-stu-id="76759-409">This version of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="76759-410">R4144: MTOM procesory musí přijmout záhlaví Content-ID hodnoty, které odpovídají následující zmírnit `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="76759-410">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="76759-411">MIME (RFC chodu 2045) poskytuje hlavičku kódování přenosu obsahu pro komunikaci, kódování obsahu části standardu MIME.</span><span class="sxs-lookup"><span data-stu-id="76759-411">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="76759-412">Výchozí hodnota definovaná pro kódování přenosu obsahu je 7 bitů, což není vhodná pro většinu protokolu SOAP zprávy, aby bylo možné hlavičku Content-Transfer-Encoding větší interoperability:</span><span class="sxs-lookup"><span data-stu-id="76759-412">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="76759-413">R4145: Informační SOAP sadu část musí obsahovat hlavičku kódování přenosu obsahu.</span><span class="sxs-lookup"><span data-stu-id="76759-413">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="76759-414">R4146: Pokud kódování znaků pro obálku protokolu SOAP je UTF-8, musí být hodnota hlavičky Content-Transfer-Encoding 8 bitů.</span><span class="sxs-lookup"><span data-stu-id="76759-414">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="76759-415">R4147: Pokud je znak obálku protokolu SOAP kódování UTF-16, hodnota hlavičky kódování přenosu obsahu musí být binární.</span><span class="sxs-lookup"><span data-stu-id="76759-415">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="76759-416">Závislosti [XOP] část 5,</span><span class="sxs-lookup"><span data-stu-id="76759-416">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="76759-417">R4148: Informační SOAP1.1 sadu část musí obsahovat hlavičku Content-Type s typ média application/xop + xml a parametry type = "text/xml" a znaková sada</span><span class="sxs-lookup"><span data-stu-id="76759-417">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="76759-418">R4149: Část informační SOAP 1.2 sadu musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry type = "`application/soap+xml`" a `charset`.</span><span class="sxs-lookup"><span data-stu-id="76759-418">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="76759-419">Při definuje XOP `charset` parametr pro `application/xop+xml` jako volitelnou, je potřeba pro spolupráci podobná BP 1.1 požadavek na `charset` parametr pro `text/xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="76759-419">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="76759-420">R41410: `type` a `charset` parametry musí být v hlavičce Content-Type části informační sadu 1.x protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="76759-420">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="76759-421">Podpora koncový bod WCF MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-421">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="76759-422">Účelem MTOM je určený ke kódování zprávu protokolu SOAP k optimalizaci data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="76759-422">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="76759-423">Následuje seznam omezení:</span><span class="sxs-lookup"><span data-stu-id="76759-423">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="76759-424">R4151: Může optimalizovat libovolnou položku informace element, který obsahuje data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="76759-424">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="76759-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimalizuje položky element informace, které obsahují data s kódováním base64 a přesáhnout délku 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="76759-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="76759-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod nakonfigurovaný na použití MTOM vždycky odešlou kódování MTOM zprávy.</span><span class="sxs-lookup"><span data-stu-id="76759-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="76759-427">I v případě, že žádné části splňují kritéria požadovaná, zpráva je stále kódování MTOM (serializovat jako balíček MIME s jedné součásti MIME obsahující obálku protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="76759-427">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="76759-428">Výraz WS-zásad pro MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-428">WS-Policy Assertion for MTOM</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <span data-ttu-id="76759-429">Následující výraz zásad se používá k označení MTOM využití pomocí koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="76759-429">uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="76759-430">R4211: Předchozí výraz zásad má subjektu zásad koncového bodu a určuje, že všechny zprávy odesílané do a z koncového bodu musí být optimalizovány s použitím MTOM.</span><span class="sxs-lookup"><span data-stu-id="76759-430">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="76759-431">B4212: Pokud nakonfigurovaná pro použití MTOM optimalizace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod přidá kontrolní výrazy zásad MTOM zásady připojené k odpovídající `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="76759-431">B4212: When configured to use MTOM optimization, an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="76759-432">Složení s WS-zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76759-432">Composition with WS-Security</span></span>  
 <span data-ttu-id="76759-433">MTOM je mechanismus kódování, který je podobný `text/xml` a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binární XML.</span><span class="sxs-lookup"><span data-stu-id="76759-433">MTOM is an encoding mechanism that is similar to `text/xml` and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary XML.</span></span> <span data-ttu-id="76759-434">MTOM nabízí přirozené složení s WS-zabezpečení a jiné WS-\* protokoly: zprávu zabezpečené pomocí protokolu WS-zabezpečení lze optimalizovat pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="76759-434">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="76759-435">Příklady</span><span class="sxs-lookup"><span data-stu-id="76759-435">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="76759-436">WCF SOAP 1.1 zpráva kódované pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-436">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="76759-437">Zabezpečení WCF SOAP 1.2 zpráva kódovaný pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="76759-437">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="76759-438">V tomto příkladu je zpráva kódované pomocí MTOM a SOAP 1.2, který je chráněný pomocí protokolu WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="76759-438">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="76759-439">Binární části identifikovat pro kódování jsou obsah `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpovídající šifrované podpisu a šifrovaný text.</span><span class="sxs-lookup"><span data-stu-id="76759-439">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="76759-440">Všimněte si, že `CipherValue` z `EncryptedKey` nebyla určená pro optimalizaci podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], protože jeho délka je menší pak 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="76759-440">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because its length is less then 1024 bytes.</span></span>  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
