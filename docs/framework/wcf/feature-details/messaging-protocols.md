---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: c900c8fde8b13b4766fb245de2bab46b5601f135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496634"
---
# <a name="messaging-protocols"></a><span data-ttu-id="24d72-102">Protokoly zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-102">Messaging Protocols</span></span>
<span data-ttu-id="24d72-103">Zásobník kanálu Windows Communication Foundation (WCF) aktivuje kódování a přenos kanály transformace reprezentace interní zprávy do jeho přenosový formát a odesílat je pomocí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="24d72-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="24d72-104">Nejběžnější přenos používá funkční spolupráce při webové služby, je HTTP, a nejběžnější kódování používá webové služby jsou na základě XML SOAP 1.1, SOAP 1.2 a zpráva přenosu optimalizace mechanismus (MTOM).</span><span class="sxs-lookup"><span data-stu-id="24d72-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="24d72-105">Toto téma obsahuje podrobnosti o implementaci WCF pro následující protokoly zaměstnaní <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="24d72-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="24d72-106">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="24d72-106">Specification/document</span></span>|<span data-ttu-id="24d72-107">Odkaz</span><span class="sxs-lookup"><span data-stu-id="24d72-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="24d72-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="24d72-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="24d72-109">SOAP 1.1 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="24d72-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="24d72-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Část 7</span><span class="sxs-lookup"><span data-stu-id="24d72-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="24d72-111">SOAP 1.2 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="24d72-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="24d72-112">http://www.w3.org/TR/soap12-part2/, Část 7</span><span class="sxs-lookup"><span data-stu-id="24d72-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="24d72-113">Toto téma obsahuje podrobné informace o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívají.</span><span class="sxs-lookup"><span data-stu-id="24d72-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="24d72-114">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="24d72-114">Specification/Document</span></span>|<span data-ttu-id="24d72-115">Odkaz</span><span class="sxs-lookup"><span data-stu-id="24d72-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="24d72-116">XML</span><span class="sxs-lookup"><span data-stu-id="24d72-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="24d72-117">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="24d72-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="24d72-118">SOAP 1.2 jádra</span><span class="sxs-lookup"><span data-stu-id="24d72-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="24d72-119">Adresování WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="24d72-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="24d72-120">W3C webových služeb adresování 1.0 – základní</span><span class="sxs-lookup"><span data-stu-id="24d72-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="24d72-121">W3C webových služeb adresování 1.0 - vazby protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="24d72-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="24d72-122">W3C webových služeb adresování 1.0 - vazby WSDL</span><span class="sxs-lookup"><span data-stu-id="24d72-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="24d72-123">W3C webových služeb adresování 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="24d72-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="24d72-124">Vazba SOAP1.1 WSDL</span><span class="sxs-lookup"><span data-stu-id="24d72-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="24d72-125">Vazba SOAP1.2 WSDL</span><span class="sxs-lookup"><span data-stu-id="24d72-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="24d72-126">Toto téma obsahuje podrobné informace o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívá.</span><span class="sxs-lookup"><span data-stu-id="24d72-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="24d72-127">Specifikace či dokumentu</span><span class="sxs-lookup"><span data-stu-id="24d72-127">Specification/document</span></span>|<span data-ttu-id="24d72-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="24d72-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="24d72-129">XOP</span><span class="sxs-lookup"><span data-stu-id="24d72-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="24d72-130">MTOM + SOAP 1.2 vazby</span><span class="sxs-lookup"><span data-stu-id="24d72-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="24d72-131">MTOM SOAP 1.1 vazby</span><span class="sxs-lookup"><span data-stu-id="24d72-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="24d72-132">Výraz WS-zásad MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="24d72-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="24d72-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="24d72-134">Následující obory názvů XML a přidružené předpony se používají v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="24d72-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="24d72-135">Předpona</span><span class="sxs-lookup"><span data-stu-id="24d72-135">Prefix</span></span>|<span data-ttu-id="24d72-136">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="24d72-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="24d72-137">s11</span><span class="sxs-lookup"><span data-stu-id="24d72-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="24d72-138">s12</span><span class="sxs-lookup"><span data-stu-id="24d72-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="24d72-139">wsa</span><span class="sxs-lookup"><span data-stu-id="24d72-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="24d72-140">wsam</span><span class="sxs-lookup"><span data-stu-id="24d72-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="24d72-141">wsap</span><span class="sxs-lookup"><span data-stu-id="24d72-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="24d72-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="24d72-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="24d72-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="24d72-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="24d72-144">XOP</span><span class="sxs-lookup"><span data-stu-id="24d72-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="24d72-145">xmime</span><span class="sxs-lookup"><span data-stu-id="24d72-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="24d72-146">distribučního bodu</span><span class="sxs-lookup"><span data-stu-id="24d72-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="24d72-147">SOAP 1.1 a SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="24d72-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="24d72-148">Obálky a zpracování modelu</span><span class="sxs-lookup"><span data-stu-id="24d72-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="24d72-149">WCF implementuje zpracování obálky protokolu SOAP 1.1 Basic Profile 1.1 (základní parametr 11) a základní profil 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="24d72-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="24d72-150">SOAP 1.2 obálky zpracování je implementována následující část SOAP12-1.</span><span class="sxs-lookup"><span data-stu-id="24d72-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="24d72-151">Tato část popisuje některé volby implementace provedenou WCF s ohledem na základní parametr 11 a část SOAP12-1.</span><span class="sxs-lookup"><span data-stu-id="24d72-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="24d72-152">Zpracování povinnou hlavičku</span><span class="sxs-lookup"><span data-stu-id="24d72-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="24d72-153">WCF dodržuje pravidla pro zpracování hlavičky označena `mustUnderstand` popsané v protokolu SOAP 1.1 a SOAP 1.2 specifikace, s následující rozdíly.</span><span class="sxs-lookup"><span data-stu-id="24d72-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="24d72-154">Zpráva, která vstupuje do zásobníku kanálu WCF zpracovává jednotlivé kanály nakonfiguroval prvky přidružené vazeb, například, kódování textu zprávy, zabezpečení, spolehlivé zasílání zpráv a transakce.</span><span class="sxs-lookup"><span data-stu-id="24d72-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="24d72-155">Každý kanál rozpozná hlavičky z přidružených oboru názvů a označí je jako rozumí.</span><span class="sxs-lookup"><span data-stu-id="24d72-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="24d72-156">Jakmile zprávu zadá dispečera, přečte operaci formátování záhlaví očekávanou odpovídající kontrakt zprávy nebo operaci a značky, které jim rozumím jim.</span><span class="sxs-lookup"><span data-stu-id="24d72-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="24d72-157">Pak dispečera ověřuje, zda nejsou žádné zbývající hlavičky rozumí ale označen jako `mustUnderstand` a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="24d72-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="24d72-158">Zprávy, které obsahují `mustUnderstand` hlavičky, které jsou zaměřeny na příjemce nejsou zpracovávány kód příjemce aplikace.</span><span class="sxs-lookup"><span data-stu-id="24d72-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="24d72-159">Například vrstvený zpracování umožňuje oddělení mezi infrastruktury vrstvy a aplikaci vrstvy protokolu SOAP uzlu:</span><span class="sxs-lookup"><span data-stu-id="24d72-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="24d72-160">B1111: Hlavičky, které nejsou rozumí zjištění po zpracování zprávy zásobník infrastruktury kanálu WCF, ale předtím, než je zpracován aplikací</span><span class="sxs-lookup"><span data-stu-id="24d72-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="24d72-161">`mustUnderstand` Hodnota hlavičky se liší mezi SOAP 1.1 a SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="24d72-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="24d72-162">Basic Profile 1.1 vyžaduje, aby `mustUnderstand` hodnota být 0 nebo 1 pro zprávy SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="24d72-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="24d72-163">SOAP 1.2 umožňuje 0, 1, `false`, a `true` hodnoty, ale doporučuje emitování kanonický reprezentace `xs:boolean` hodnoty (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="24d72-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="24d72-164">B1112: Vysílá WCF `mustUnderstand` hodnoty 0 a 1 pro verze protokolu SOAP 1.1 a SOAP 1.2 obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="24d72-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="24d72-165">WCF přijímá prostor celou hodnotu `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="24d72-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="24d72-166">Chyb SOAP</span><span class="sxs-lookup"><span data-stu-id="24d72-166">SOAP Faults</span></span>  
 <span data-ttu-id="24d72-167">Následuje seznam implementace selhání specifické WCF SOAP.</span><span class="sxs-lookup"><span data-stu-id="24d72-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="24d72-168">B2121: WCF vrátí následující kódy chyb protokolu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, a `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="24d72-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="24d72-169">B2122: WCF vrátí následující kódy chyb protokolu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, a `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="24d72-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="24d72-170">Vazba HTTP</span><span class="sxs-lookup"><span data-stu-id="24d72-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="24d72-171">SOAP 1.1 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="24d72-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="24d72-172">WCF implementuje vazby SOAP1.1 HTTP následující specifikace Basic Profile 1.1 oddíl 3.4 objasnění následující:</span><span class="sxs-lookup"><span data-stu-id="24d72-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="24d72-173">B2211: Služby WCF neimplementuje přesměrování požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="24d72-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="24d72-174">B2212: WCF klienti podporují soubory cookie protokolu HTTP v souladu s 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="24d72-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="24d72-175">SOAP 1.2 vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="24d72-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="24d72-176">WCF implementuje vazby SOAP 1.2 HTTP, jak je popsáno v protokolu SOAP 1.2 část 2 (SOAP12Part2) specifikace s následující objasnění.</span><span class="sxs-lookup"><span data-stu-id="24d72-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="24d72-177">Parametr volitelné akce pro zavedená SOAP 1.2 `application/soap+xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="24d72-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="24d72-178">Tento parametr je užitečné k optimalizaci odesílání zpráv bez nutnosti analyzovat do těla protokolu SOAP zprávy při adresování WS nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="24d72-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="24d72-179">R2221: `application/soap+xml` parametr akce, pokud jsou k dispozici na vyžádání SOAP 1.2, musí odpovídat `soapAction` atributu u `wsoap12:operation` prvku v odpovídající vazby WSDL.</span><span class="sxs-lookup"><span data-stu-id="24d72-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="24d72-180">R2222: `application/soap+xml` parametr akce, pokud jsou k dispozici na zprávu protokolu SOAP 1.2 musí odpovídat `wsa:Action` při použití služby WS-Addressing 2004/08 nebo WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="24d72-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="24d72-181">Když WS-Addressing je zakázána a příchozí požadavek neobsahuje parametr akce, zprávy `Action` považuje za není zadaný.</span><span class="sxs-lookup"><span data-stu-id="24d72-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="24d72-182">Adresování WS</span><span class="sxs-lookup"><span data-stu-id="24d72-182">WS-Addressing</span></span>  
 <span data-ttu-id="24d72-183">WCF implementuje 3 verze WS adresování:</span><span class="sxs-lookup"><span data-stu-id="24d72-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="24d72-184">Adresování WS 2004/08</span><span class="sxs-lookup"><span data-stu-id="24d72-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="24d72-185">Adresování 1.0 jádra (ADDR10-jader) a vazbu (ADDR10 protokolu SOAP) SOAP W3C webové služby</span><span class="sxs-lookup"><span data-stu-id="24d72-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="24d72-186">Adresování WS 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="24d72-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="24d72-187">Odkazy na koncový bod</span><span class="sxs-lookup"><span data-stu-id="24d72-187">Endpoint References</span></span>  
 <span data-ttu-id="24d72-188">Všechny verze WS-Addressing implementující WCF pomocí koncového bodu odkazy popisují koncové body.</span><span class="sxs-lookup"><span data-stu-id="24d72-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="24d72-189">Odkazy na koncový bod a adresování WS verze</span><span class="sxs-lookup"><span data-stu-id="24d72-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="24d72-190">WCF implementuje číslo infrastruktury protokolů, které používají služby WS-Addressing, zejména `EndpointReference` elementu a `W3C.WsAddressing.EndpointReferenceType` – třída (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="24d72-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="24d72-191">WCF podporuje jednu z verzí nástroje WS-Addressing s ostatními protokoly infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="24d72-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="24d72-192">Koncových bodů WCF podporovat jednu verzi WS-Addressing na jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="24d72-193">Pro R3111, obor názvů pro `EndpointReference` element nebo typ použitý v zprávy vyměňují s koncovým bodem WCF musí odpovídat verzi WS adresování implementované tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="24d72-194">Pokud koncový bod WCF implementuje WS-ReliableMessaging, například `AcksTo` hlavička bodem uvnitř `CreateSequenceResponse` používá verzi WS-Addressing, `EncodingBinding` element určuje pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="24d72-195">Odkazy na koncový bod a Metadata</span><span class="sxs-lookup"><span data-stu-id="24d72-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="24d72-196">Různé scénáře vyžadují komunikaci metadata nebo odkaz na metadata pro daný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="24d72-197">B3121: WCF aktivuje mechanismy popsána ve specifikaci WS-MetadataExchange (MEX) část 6 Zahrnout metadata pro koncový bod odkazy hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="24d72-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="24d72-198">Vezměte v úvahu scénář, kde služby WCF vyžaduje ověření pomocí tokenu zabezpečení kontrolní výrazy Markup Language (SAML) vydaný vydavatel tokenu v http://sts.fabrikam123.com. Koncový bod WCF popisuje tento požadavek ověřování pomocí `sp:IssuedToken` kontrolní výraz s vnořeným `sp:Issuer` assertion odkazující na vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="24d72-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="24d72-199">Klientských aplikací, které přístup `sp:Issuer` assertion muset vědět, jak ke komunikaci s koncovým bodem tokenu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="24d72-199">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="24d72-200">Klient musí vědět, metadata o vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="24d72-200">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="24d72-201">Pomocí rozšíření koncový bod odkaz metadata definovaná v MEX, WCF obsahuje odkaz na metadata vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="24d72-201">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="24d72-202">Adresování hlavičky zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-202">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="24d72-203">Hlavičky zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-203">Message Headers</span></span>  
 <span data-ttu-id="24d72-204">Pro obě verze WS-Addressing WCF používá následující záhlaví zprávy podle specifikace `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, a `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="24d72-204">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="24d72-205">B3211: Pro všechny verze WS-Addressing WCF ctí, ale nevytváří předinstalované, WS-Addressing hlavičky zpráv `wsa:FaultTo` a `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="24d72-205">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="24d72-206">Aplikace, které spolupracují s aplikací služby WCF můžete přidat, že tyto hlavičky zpráv a WCF se jejich zpracování odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="24d72-206">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="24d72-207">Odkaz na parametry a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="24d72-207">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="24d72-208">WCF implementuje zpracování parametrů odkaz na koncový bod a p – referenční informace</span><span class="sxs-lookup"><span data-stu-id="24d72-208">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="24d72-209">vlastnosti v souladu s příslušnými specifikace.</span><span class="sxs-lookup"><span data-stu-id="24d72-209">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="24d72-210">B3221: Pokud nakonfigurovaná pro použití služby WS-Addressing 2004/08, koncových bodů WCF nerozlišují mezi zpracování vlastnosti odkazu a odkaz na parametry.</span><span class="sxs-lookup"><span data-stu-id="24d72-210">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="24d72-211">Vzory Exchange zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="24d72-212">Pořadí zpráv zahrnutých v operaci volání webové služby se označuje jako *vzorce výměny zpráv*.</span><span class="sxs-lookup"><span data-stu-id="24d72-212">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="24d72-213">WCF podporuje jednosměrné, požadavku a odpovědi a duplexní zprávu výměna vzory.</span><span class="sxs-lookup"><span data-stu-id="24d72-213">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="24d72-214">Tato část vysvětluje, WS-Addressing požadavky na zpracování v závislosti na vzorce výměny zpráv používá zpráv.</span><span class="sxs-lookup"><span data-stu-id="24d72-214">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="24d72-215">V této části žadatel odešle první zprávy a příjemce obdrží první zprávu.</span><span class="sxs-lookup"><span data-stu-id="24d72-215">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="24d72-216">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-216">One-Way Message</span></span>  
 <span data-ttu-id="24d72-217">Když se koncový bod WCF nakonfigurován pro podporu zprávy s danou `Action` sledovat jednosměrného vzor, koncový bod WCF dodržuje následující požadavky a chování.</span><span class="sxs-lookup"><span data-stu-id="24d72-217">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="24d72-218">Pokud není uvedeno jinak, platí pro obě verze WS adresování podporované ve službě WCF chování a pravidla:</span><span class="sxs-lookup"><span data-stu-id="24d72-218">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="24d72-219">R3311: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`a hlavičky pro všechny parametry odkaz určeného odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-219">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="24d72-220">Když se používá WS-Addressing 2004/08 a [Vlastnosti odkazu] jsou určené odkaz na koncový bod odpovídající hlavičky musí být přidaný do zprávy příliš.</span><span class="sxs-lookup"><span data-stu-id="24d72-220">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="24d72-221">B3312: Žadatel může zahrnovat `MessageID`, `ReplyTo`, a `FaultTo` hlavičky.</span><span class="sxs-lookup"><span data-stu-id="24d72-221">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="24d72-222">Příjemce infrastruktury je bude ignorovat a se předají do aplikace.</span><span class="sxs-lookup"><span data-stu-id="24d72-222">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="24d72-223">R3313: Když se používá protokol HTTP a odesílání žádné zprávy na větev odpověď HTTP, musíte odeslat odpovídající počítač s prázdným textem zprávy a HTTP 202 stavový kód HTTP odpovědi.</span><span class="sxs-lookup"><span data-stu-id="24d72-223">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="24d72-224">Pokud přenos HTTP je používán a kontrakt operaci deklaruje zprávu jednosměrné, odpověď HTTP pořád můžou použít pro odesílání zpráv infrastruktury – například může odesílat spolehlivé zasílání zpráv `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="24d72-224">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="24d72-225">B3314: Respondér WCF neodešle zprávu o chybě v odpovědi na zprávu jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="24d72-225">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="24d72-226">Požadavek a odpověď</span><span class="sxs-lookup"><span data-stu-id="24d72-226">Request-Reply</span></span>  
 <span data-ttu-id="24d72-227">Když se koncový bod WCF je nakonfigurován pro zprávu s danou `Action` podle vzoru požadavku a odpovědi, koncový bod WCF řídí chování a požadavky uvedené níže.</span><span class="sxs-lookup"><span data-stu-id="24d72-227">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="24d72-228">Pokud není uvedeno jinak, platí pro obě verze WS adresování podporované ve službě WCF chování a pravidla:</span><span class="sxs-lookup"><span data-stu-id="24d72-228">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="24d72-229">R3321: Žadatel musí zahrnovat v požadavku `wsa:To`, `wsa:Action`, `wsa:MessageID`, tak i hlaviček pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného odkaz na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-229">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="24d72-230">R3322: Pokud je použita WS-Addressing 2004/08, `ReplyTo` musí také obsahovat žádosti.</span><span class="sxs-lookup"><span data-stu-id="24d72-230">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="24d72-231">R3323: Při použití služby WS-Addressing 1.0 a `ReplyTo` se nenachází v žádosti o odkazem na výchozí koncový bod s vlastností [address] rovno "http://www.w3.org/2005/08/addressing/anonymous" se používá.</span><span class="sxs-lookup"><span data-stu-id="24d72-231">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="24d72-232">R3324: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`, a `wsa:RelatesTo` hlavičky v odpovědi, jakož i hlavičky pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného `ReplyTo` odkaz na koncový bod v požadavek.</span><span class="sxs-lookup"><span data-stu-id="24d72-232">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="24d72-233">Webové služby adresování chyb</span><span class="sxs-lookup"><span data-stu-id="24d72-233">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="24d72-234">R3411: WCF vytvoří následující chyb definované WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="24d72-234">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="24d72-235">Kód</span><span class="sxs-lookup"><span data-stu-id="24d72-235">Code</span></span>|<span data-ttu-id="24d72-236">příčina</span><span class="sxs-lookup"><span data-stu-id="24d72-236">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="24d72-237">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="24d72-237">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="24d72-238">Zpráva dorazila po uplynutí `ReplyTo` , se liší od navázána pro tento kanál adresu; neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.</span><span class="sxs-lookup"><span data-stu-id="24d72-238">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="24d72-239">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="24d72-239">wsa:ActionNotSupported</span></span>|<span data-ttu-id="24d72-240">kanály infrastruktury nebo dispečera přiřazené ke koncovému bodu nerozpoznávají zadaná v akci `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="24d72-240">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="24d72-241">R3412: WCF vytvoří následující chyb definované WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="24d72-241">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="24d72-242">Kód</span><span class="sxs-lookup"><span data-stu-id="24d72-242">Code</span></span>|<span data-ttu-id="24d72-243">příčina</span><span class="sxs-lookup"><span data-stu-id="24d72-243">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="24d72-244">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="24d72-244">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="24d72-245">Duplicitní `wsa:To`, `wsa:ReplyTo`, `wsa:From` nebo `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="24d72-245">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="24d72-246">Duplicitní `wsa:RelatesTo` se stejným `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="24d72-246">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="24d72-247">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="24d72-247">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="24d72-248">Požadovaná hlavička Addressing nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="24d72-248">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="24d72-249">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="24d72-249">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="24d72-250">Zpráva dorazila po uplynutí `ReplyTo` která se liší od navázána pro tento kanál adresu.</span><span class="sxs-lookup"><span data-stu-id="24d72-250">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="24d72-251">Neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.</span><span class="sxs-lookup"><span data-stu-id="24d72-251">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="24d72-252">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="24d72-252">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="24d72-253">Zadaná v akci `Action` hlavička nebyla rozpoznána infrastruktury kanály nebo dispečera přiřazené ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="24d72-253">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="24d72-254">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="24d72-254">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="24d72-255">Kanál RM odešle tato porucha zpět, označující koncový bod nezpracuje pořadí na základě zkoumání `CreateSequence` zprávu o adrese hlavičky.</span><span class="sxs-lookup"><span data-stu-id="24d72-255">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="24d72-256">Kód v předchozích tabulkách se mapuje na `FaultCode` v SOAP 1.1 a `SubCode` (s kódem = odesílatele) v protokolu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="24d72-256">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="24d72-257">WSDL 1.1 vazby a WS-Policy kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="24d72-257">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="24d72-258">Označující použití adresování WS</span><span class="sxs-lookup"><span data-stu-id="24d72-258">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="24d72-259">WCF pomocí kontrolních výrazů zásad označuje koncového bodu podporu pro konkrétní verzi WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="24d72-259">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="24d72-260">Následující výraz zásad má koncový bod zásad subjektu [WS-PA] a znamená, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="24d72-260">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="24d72-261">Tento výraz zásad argumentech specifikace WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="24d72-261">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="24d72-262">Následující výraz zásad, že to znamená, že který zprávy odeslat/přijmout musí používat WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="24d72-262">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="24d72-263">Následující výraz zásad má předmět zásad služby Endpoint [WS-PA] a označuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="24d72-263">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="24d72-264">`wsaw10:UsingAddressing` Elementu je vždy pouze vypůjčí na [WS-adresování-WSDL] a je použita v kontextu služby WS-Policy v souladu s této specifikaci se v části 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="24d72-264">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="24d72-265">Použití Addressing nezmění sémantika WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazby.</span><span class="sxs-lookup"><span data-stu-id="24d72-265">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="24d72-266">Například pokud je odpověď na žádost, kterou posílá koncový bod, který používá Addressing a WSDL SOAP vazby HTTP 1.x očekávána, musí se odpovědi poslat pomocí odpověď HTTP.</span><span class="sxs-lookup"><span data-stu-id="24d72-266">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="24d72-267">Pro odpovědi, odešlou přes odpověď http WS-AM kontrolní výraz je:</span><span class="sxs-lookup"><span data-stu-id="24d72-267">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="24d72-268">Výraz dokončení zásad může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="24d72-268">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="24d72-269">Existují však vzory exchange zprávu, využívající má dva nezávislé konverzace HTTP připojení mezi žadatel a respondér, například nevyžádané jednosměrný zprávy odeslané respondér.</span><span class="sxs-lookup"><span data-stu-id="24d72-269">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="24d72-270">WCF nabízí funkce, pomocí kterého můžete dvě základní přenosové kanály formuláři složené duplexní kanál, kde jeden kanál je používána pro vstupní zprávy a druhý je používána pro zprávy výstup.</span><span class="sxs-lookup"><span data-stu-id="24d72-270">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="24d72-271">V případě přenos HTTP poskytuje složené duplexní dvě připojení HTTP konverzace.</span><span class="sxs-lookup"><span data-stu-id="24d72-271">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="24d72-272">Žadatel používá jedno připojení k odesílání zpráv do odpovídající partner a odpovídající partner dalších odesílání zprávy zpět na žadatel.</span><span class="sxs-lookup"><span data-stu-id="24d72-272">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="24d72-273">Pro odpovědi, odešlou přes požadavky http samostatné ws-am kontrolní výraz je</span><span class="sxs-lookup"><span data-stu-id="24d72-273">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="24d72-274">Výraz dokončení zásad může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="24d72-274">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="24d72-275">Následující kontrolní výraz, který má koncový bod zásad subjektu [WS-PA] na koncové body, které pomocí vazby HTTP 1.x WSDL 1.1 SOAP vyžaduje dva samostatné konverzace připojení protokolu HTTP má být použit pro zpráv předávaných z žadatel respondér a respondér k žadatel, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="24d72-275">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="24d72-276">Předchozí příkaz vede k následující požadavky `wsa:ReplyTo` hlavičky pro žádosti o zprávy:</span><span class="sxs-lookup"><span data-stu-id="24d72-276">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="24d72-277">R3514: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost není rovno "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má alternativní zásady s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` kontrolní výraz kombinaci s `cdp:CompositeDuplex` připojen.</span><span class="sxs-lookup"><span data-stu-id="24d72-277">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="24d72-278">R3515: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous", nebo není `ReplyTo` záhlaví na všechny, pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má alternativní zásad s `wsap10:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` assertion připojen.</span><span class="sxs-lookup"><span data-stu-id="24d72-278">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="24d72-279">R3516: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má alternativní zásady s `wsap:UsingAddressing` kontrolní výraz a žádné `cdp:CompositeDuplex`assertion připojen.</span><span class="sxs-lookup"><span data-stu-id="24d72-279">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="24d72-280">Specifikace WS-addressing WSDL pokusí popisují podobné vazby protokolu zavedením element `<wsaw:Anonymous/>` s tři textové hodnoty (vyžaduje, volitelné a zakázané) k označení požadavky na `wsa:ReplyTo` hlavičky (část 3.2).</span><span class="sxs-lookup"><span data-stu-id="24d72-280">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="24d72-281">Bohužel taková definice elementu není zvlášť jako kontrolní výrazy v kontextu služby WS-zásad, protože vyžaduje rozšíření specifické pro doménu, které podporují průnik alternativy pomocí takový prvek jako kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="24d72-281">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="24d72-282">Taková definice elementu také určuje hodnota `ReplyTo` záhlaví oproti chování koncového bodu v drátové síti, takže je konkrétní přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="24d72-282">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="24d72-283">Definice akce</span><span class="sxs-lookup"><span data-stu-id="24d72-283">Action Definition</span></span>  
 <span data-ttu-id="24d72-284">Definuje WS-Addressing 2004/08 `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy.</span><span class="sxs-lookup"><span data-stu-id="24d72-284">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="24d72-285">Adresování WS 1.0 WSDL vazby (WS-ADDR10-WSDL) definuje atribut podobné `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="24d72-285">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="24d72-286">Jediným rozdílem mezi těmito dvěma je sémantiky vzor výchozí akce popsané v 3.3.2 WS-ADDR a oddílu bodu 4.4.4 WS-ADDR10-WSDL, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="24d72-286">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="24d72-287">Je možné logicky tak, aby měl dva koncové body, které sdílejí stejné `portType` (nebo kontrakt, v terminologii WCF), ale používání různých verzí WS adres.</span><span class="sxs-lookup"><span data-stu-id="24d72-287">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="24d72-288">Ale vzhledem k tomu, že je definována akce `portType` a neměli měnit napříč koncovými body, které implementují `portType`, bude možné podporovat i výchozí akci zpracování.</span><span class="sxs-lookup"><span data-stu-id="24d72-288">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="24d72-289">Chcete-li vyřešit tento sporům, WCF podporuje jednu verzi `Action` atribut.</span><span class="sxs-lookup"><span data-stu-id="24d72-289">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="24d72-290">B3521: Používá WCF `wsaw10:Action` atributu u `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` dle WS-ADDR10-WSDL k určení `Action` identifikátor URI pro odpovídající zprávy, bez ohledu na verzi WS-Addressing používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="24d72-290">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="24d72-291">Použití koncový bod odkaz uvnitř WSDL portu</span><span class="sxs-lookup"><span data-stu-id="24d72-291">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="24d72-292">WS-ADDR10-WSDL části 4.1 rozšiřuje `wsdl:port` elementu, který chcete zahrnout `<wsa10:EndpointReference…/>` podřízený element k popisu koncový bod v WS-Addressing podmínky.</span><span class="sxs-lookup"><span data-stu-id="24d72-292">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="24d72-293">WCF rozšíří na adresování WS 2004/08, tento nástroj umožňuje `<wsa:EndpointReference…/>` vypadaly jako podřízeného prvku `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="24d72-293">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="24d72-294">R3531: Pokud koncový bod má alternativu připojené zásady s `<wsaw10:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="24d72-294">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="24d72-295">R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.</span><span class="sxs-lookup"><span data-stu-id="24d72-295">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="24d72-296">R3533: Pokud koncový bod má alternativu připojené zásady s `<wsap:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="24d72-296">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="24d72-297">R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.</span><span class="sxs-lookup"><span data-stu-id="24d72-297">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="24d72-298">Složení s WS-zabezpečení</span><span class="sxs-lookup"><span data-stu-id="24d72-298">Composition with WS-Security</span></span>  
 <span data-ttu-id="24d72-299">Podle zabezpečení části aspekt WS-ADDR a WS-ADDR10 se doporučuje všechny adresování hlavičky zpráv být podepsané společně s text zprávy pro vazbu je společně.</span><span class="sxs-lookup"><span data-stu-id="24d72-299">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="24d72-300">Pokud WS-zabezpečení se používá pro ochranu integrity zprávy, musí být podepsané WS-Addressing zpráva hlavičky, jakož i hlavičky výsledkem parametry odkaz nebo vlastnosti (nebo obě) společně s tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="24d72-300">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="24d72-301">Příklady</span><span class="sxs-lookup"><span data-stu-id="24d72-301">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="24d72-302">Jednosměrné zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-302">One-Way Message</span></span>  
 <span data-ttu-id="24d72-303">V tomto scénáři odesílatel odešle zprávu jednosměrný k příjemce.</span><span class="sxs-lookup"><span data-stu-id="24d72-303">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="24d72-304">SOAP 1.2, HTTP 1.1 a 1.0 W3C WS-Addressing se používají.</span><span class="sxs-lookup"><span data-stu-id="24d72-304">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="24d72-305">Struktura zprávu požadavku: Záhlaví zprávy zahrnují `wsa10:To` a `wsa10:Action` elementy.</span><span class="sxs-lookup"><span data-stu-id="24d72-305">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="24d72-306">Tělo zprávy obsahuje konkrétní `<app:Ping>` element z oboru názvů aplikace.</span><span class="sxs-lookup"><span data-stu-id="24d72-306">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="24d72-307">Hlavičky protokolu HTTP: Cíl v BLOGU odpovídá identifikátoru URI v `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="24d72-307">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="24d72-308">Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="24d72-308">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="24d72-309">Parametry `charset` a `action` jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="24d72-309">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="24d72-310">`action` Hodnota odpovídá parametru hlavičku Content-Type `wsa10:Action` záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="24d72-310">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="24d72-311">Příjemce odpoví s prázdnou odpověď HTTP a stav 202.</span><span class="sxs-lookup"><span data-stu-id="24d72-311">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="24d72-312">Příklad odpověď HTTP:</span><span class="sxs-lookup"><span data-stu-id="24d72-312">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="24d72-313">Mechanismus Optimalizace přenosu zpráv protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="24d72-313">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="24d72-314">Tato část popisuje podrobnosti implementace WCF pro MTOM SOAP protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="24d72-314">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="24d72-315">Technologie MTOM je protokolu SOAP zprávy kódování mechanismus stejnou třídou jako kódování tradiční text/XML nebo WCF binárního kódování.</span><span class="sxs-lookup"><span data-stu-id="24d72-315">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="24d72-316">MTOM zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="24d72-316">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="24d72-317">Kódování XML a mechanismus balení [XOP] popsaného který optimalizuje položky informace XML obsahující binární data s kódováním base64 na samostatné části binární.</span><span class="sxs-lookup"><span data-stu-id="24d72-317">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="24d72-318">MIME zapouzdření XOP balíčku, který serializuje informační sadu XML a každý binární součást balíčku XOP do samostatné části standardu MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-318">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="24d72-319">MIME XOP kódování u SOAP 1.x obálku.</span><span class="sxs-lookup"><span data-stu-id="24d72-319">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="24d72-320">HTTP přenosu vazby.</span><span class="sxs-lookup"><span data-stu-id="24d72-320">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="24d72-321">Je možné použít MTOM s jiným protokolem než HTTP přenosy s použitím technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="24d72-321">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="24d72-322">Ale v tomto tématu se zaměříme na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="24d72-322">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="24d72-323">Formát MTOM využívá velké sady specifikace, které se týkají MTOM sám sebe, XOP a MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-323">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="24d72-324">Modularitu této sady specifikace ztěžuje poněkud rekonstrukci přesných požadavcích na sémantiku formátu a zpracování.</span><span class="sxs-lookup"><span data-stu-id="24d72-324">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="24d72-325">Tato část popisuje požadavky na zpracování a formát pro vazbu protokolu HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="24d72-325">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="24d72-326">Kódování MTOM zpráv</span><span class="sxs-lookup"><span data-stu-id="24d72-326">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="24d72-327">Generování zprávy MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-327">Generating MTOM messages</span></span>  
 <span data-ttu-id="24d72-328">[XOP] části 3.1 popisuje proces kódování XML s položkami informace element, které obsahují hodnoty base64 do balíčku abstraktně definované XOP.</span><span class="sxs-lookup"><span data-stu-id="24d72-328">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="24d72-329">Následující pořadí kroků popisuje proces kódování MTOM konkrétní:</span><span class="sxs-lookup"><span data-stu-id="24d72-329">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="24d72-330">Zajistěte, aby obsahoval obálku protokolu SOAP kódovaný žádná položka informace o elementu s `[namespace name]` z "http://www.w3.org/2004/08/xop/include" a `[local name]` z `Include`.</span><span class="sxs-lookup"><span data-stu-id="24d72-330">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="24d72-331">Vytvořte prázdný balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-331">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="24d72-332">Identifikujte v původní informační sadu XML položky informace o elementu, které chcete optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="24d72-332">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="24d72-333">Pro položky, které chcete optimalizovat, znaky, tvoří `[children]` informace o elementu položky musí být v kanonickém tvaru `xs:base64Binary` (viz XSD-2, 3.2.16 pomocí base64Binary) a nesmí obsahovat žádné prázdné znaky před vložením s, nebo Následující obsah neprázdný.</span><span class="sxs-lookup"><span data-stu-id="24d72-333">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="24d72-334">Vytvoří obálku protokolu SOAP XOP, který je kopií původního obálky protokolu SOAP, ale s podřízenými položkami každý element informací nahrazuje položku identifikovat v předchozím kroku `xop:Include` element informace položka vytvořená následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="24d72-334">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="24d72-335">Transformace nahrazené znaků do binární data zpracováním je jako data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="24d72-335">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="24d72-336">Generovat jedinečný hodnota hlavičky Content-ID, který splňuje požadavky R3133 a R3134.</span><span class="sxs-lookup"><span data-stu-id="24d72-336">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="24d72-337">Vygenerujte hlavička kódování přenosu obsahu MIME s binární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="24d72-337">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="24d72-338">Pokud se informace o položce element optimalizována ([nadřazený] nově vloženého `xop:Include` element informace položky) má `xmime:contentType` atribut položky informace, vygenerujte hlavičku Content-Type MIME s hodnotou `xmime:contentType` atribut.</span><span class="sxs-lookup"><span data-stu-id="24d72-338">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="24d72-339">Generovat nové části binární standardu MIME s obsahem tvořená binární data dekódovat z nahrazené znaky zpracovávány jako base64, Hlavička Content-ID ze 4b, Hlavička kódování přenosu obsahu ze 4c, Hlavička Content-Type, pokud vygenerované v kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="24d72-339">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="24d72-340">Přidat `href` atribut `xop:Include` element s hodnotou cid: identifikátor uri odvozené od hodnota hlavičky Content-ID vygenerované v kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="24d72-340">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="24d72-341">Odebrat uzavírací "\<" a ">" znaky adresy URL řídicí zbývající řetězec a přidat předponu `cid:`.</span><span class="sxs-lookup"><span data-stu-id="24d72-341">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="24d72-342">Je potřeba předcházet RFC1738 a RFC2396 následující minimální znakovou sadu.</span><span class="sxs-lookup"><span data-stu-id="24d72-342">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="24d72-343">Můžete uvozené jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="24d72-343">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="24d72-344">Vytvořte Kořenová část MIME s XOP obálku protokolu SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="24d72-344">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="24d72-345">Zápisu hlavičky protokolu HTTP, včetně hlavičku HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="24d72-345">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="24d72-346">Zápis balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-346">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="24d72-347">Zpracování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-347">Processing MTOM messages</span></span>  
 <span data-ttu-id="24d72-348">Zpracování MTOM zpráva je přesný zpětného procesu popsané v předchozím "generování MTOM zprávy" části:</span><span class="sxs-lookup"><span data-stu-id="24d72-348">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="24d72-349">Ujistěte se, má kořenová část MIME Content-Type `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="24d72-349">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="24d72-350">Vytvořte obálku protokolu SOAP analýzou kořenu MIME součást balíčku jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="24d72-350">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="24d72-351">Kódování znaků je dáno `charset` parametr Content-Type kořenové části MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-351">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="24d72-352">Pro každou položku informace element v sestavené obálku protokolu SOAP, který má, jako jedinou člen jeho [podřízené položky] vlastnosti, `xop:Include` element informace položky:</span><span class="sxs-lookup"><span data-stu-id="24d72-352">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="24d72-353">Odeberte `cid:` předpony a unescape všechny URI – řídicí sekvence (RFC 2396) v hodnotě `@href` atribut `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="24d72-353">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="24d72-354">Uzavřete výsledný řetězec v "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="24d72-354">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="24d72-355">Vyhledejte část MIME s hodnota hlavičky Content-ID, který se shoduje s řetězcem odvozený v krok 3a.</span><span class="sxs-lookup"><span data-stu-id="24d72-355">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="24d72-356">Nahraďte `xop:Include` položky informace o elementu, který se zobrazí v `children` vlastnost každé položky se položky znak informace, které představují kódování base64 kanonický (viz XSD-2, 3.2.16 pomocí base64Binary) textu entity části standardu MIME v kroku 3b identifikuje (efektivně nahradit `xop:Include` položky informace o elementu s daty znovu vytvořena z součást balíčku).</span><span class="sxs-lookup"><span data-stu-id="24d72-356">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="24d72-357">Hlavičku HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="24d72-357">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="24d72-358">Toto je seznam WCF objasnění, která pro formát hlavičky protokolu HTTP Content-Type SOAP 1.x kódování MTOM zprávy odvozené od požadavky uvedené v specifikace MTOM sám a jsou odvozené z MTOM a dokumentu RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="24d72-358">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="24d72-359">R4131: Hlavičku HTTP Content-Type musí mít hodnotu multipart/related (velká a malá písmena) a jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="24d72-359">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="24d72-360">Názvy parametrů jsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="24d72-360">Parameter names are case-insensitive.</span></span> <span data-ttu-id="24d72-361">Parametr pořadí není důležité.</span><span class="sxs-lookup"><span data-stu-id="24d72-361">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="24d72-362">Úplné Backus-Naur formuláře (BNF) hlavičky Content-Type pro zprávy MIME je uvedena v chodu 2045 RFC, část 5.1.</span><span class="sxs-lookup"><span data-stu-id="24d72-362">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="24d72-363">R4132: Hlavičku HTTP Content-Type musí mít parametr typu s hodnotou `application/xop+xml` uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="24d72-363">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="24d72-364">Přestože není definován v dokumentu RFC 2387 požadavek na použijte uvozovky, text dodržuje, že všechny typu multipart/related média parametry nejpravděpodobnější obsahovat vyhrazené znaky jako "@" or "/" a je proto třeba dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="24d72-364">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="24d72-365">R4133: Hlavičku HTTP Content-Type musí mít parametr s hodnotou hlavičku Content-ID části standardu MIME, který obsahuje SOAP 1.x obálky, uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="24d72-365">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="24d72-366">Pokud je spuštění parametr vynechán, první část MIME musí obsahovat SOAP 1.x obálku.</span><span class="sxs-lookup"><span data-stu-id="24d72-366">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="24d72-367">R4134: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.1 MTOM kódovaný musí obsahovat úvodní informace parametr s hodnotou typu text/xml, uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="24d72-367">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="24d72-368">R4135: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.2 MTOM kódováním musí obsahovat úvodní informace parametr s hodnotou `application/soap+xml`, uzavřené v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="24d72-368">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="24d72-369">R4136: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.x kódování MTOM musí mít parametr hranic s hodnotou (uzavřena v uvozovkách), který odpovídá MIME hranice, na které BNF definované v dokumentu RFC 2046 části 5.1.1</span><span class="sxs-lookup"><span data-stu-id="24d72-369">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="24d72-370">Příklady:</span><span class="sxs-lookup"><span data-stu-id="24d72-370">Examples:</span></span>  
  
     <span data-ttu-id="24d72-371">OPRAVTE</span><span class="sxs-lookup"><span data-stu-id="24d72-371">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="24d72-372">OPRAVTE</span><span class="sxs-lookup"><span data-stu-id="24d72-372">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="24d72-373">NESPRÁVNÝ</span><span class="sxs-lookup"><span data-stu-id="24d72-373">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="24d72-374">Část MIME informační sadu</span><span class="sxs-lookup"><span data-stu-id="24d72-374">Infoset MIME Part</span></span>  
 <span data-ttu-id="24d72-375">SOAP 1.x obálky je zapouzdřený jako část kořenové XOP MIME balíčku a se často říká `infoset` část.</span><span class="sxs-lookup"><span data-stu-id="24d72-375">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="24d72-376">R4141: SOAP 1.x obálky musí zapouzdřené jako část kořenové XOP MIME balíčku, volá se `infoset` část a odkazované z hlavičku HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="24d72-376">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="24d72-377">R4142: SOAP `Infoset` část musí zahrnovat následující hlavičky MIME: `Content-ID`, `Content-Transfer-Encoding`, a `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="24d72-377">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="24d72-378">Formát hlavičky Content-ID je definované chodu 2045 RFC jako</span><span class="sxs-lookup"><span data-stu-id="24d72-378">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="24d72-379">kde `msg-id` je definován v dokumentu RFC 2822, (který nahrazuje RFC 822, kterou se odkazuje v chodu 2045 RFC) jako:</span><span class="sxs-lookup"><span data-stu-id="24d72-379">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="24d72-380">a efektivně e-mailovou adresu uzavřena v rámci "\<" a ">".</span><span class="sxs-lookup"><span data-stu-id="24d72-380">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="24d72-381">`[CFWS]` Předponu a příponu byly přidány RFC 2822 k provedení komentáře a nesmí se použít k zachování interoperability.</span><span class="sxs-lookup"><span data-stu-id="24d72-381">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="24d72-382">R4143: Musí následovat hodnota hlavičky Content-ID pro část MIME informační sadu `msg-id` produkční z RFC 2822 s `[CFWS]` předponu a příponu částí tento parametr vynechán.</span><span class="sxs-lookup"><span data-stu-id="24d72-382">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="24d72-383">Počet implementací MIME zmírnit požadavky pro hodnotu v rámci uzavřené "\<" a ">" jako e-mailovou adresu a použít `absoluteURI` v "\<", ">" Kromě e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="24d72-383">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="24d72-384">Tato verze služby WCF používá hodnoty hlavičky Content-ID MIME ve tvaru:</span><span class="sxs-lookup"><span data-stu-id="24d72-384">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="24d72-385">R4144: MTOM procesory musí přijmout záhlaví Content-ID hodnoty, které odpovídají následující zmírnit `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="24d72-385">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="24d72-386">MIME (RFC chodu 2045) poskytuje hlavičku kódování přenosu obsahu pro komunikaci, kódování obsahu části standardu MIME.</span><span class="sxs-lookup"><span data-stu-id="24d72-386">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="24d72-387">Výchozí hodnota definovaná pro kódování přenosu obsahu je 7 bitů, což není vhodná pro většinu protokolu SOAP zprávy, aby bylo možné hlavičku Content-Transfer-Encoding větší interoperability:</span><span class="sxs-lookup"><span data-stu-id="24d72-387">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="24d72-388">R4145: Informační SOAP sadu část musí obsahovat hlavičku kódování přenosu obsahu.</span><span class="sxs-lookup"><span data-stu-id="24d72-388">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="24d72-389">R4146: Pokud kódování znaků pro obálku protokolu SOAP je UTF-8, musí být hodnota hlavičky Content-Transfer-Encoding 8 bitů.</span><span class="sxs-lookup"><span data-stu-id="24d72-389">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="24d72-390">R4147: Pokud je znak obálku protokolu SOAP kódování UTF-16, hodnota hlavičky kódování přenosu obsahu musí být binární.</span><span class="sxs-lookup"><span data-stu-id="24d72-390">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="24d72-391">Závislosti [XOP] část 5,</span><span class="sxs-lookup"><span data-stu-id="24d72-391">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="24d72-392">R4148: Informační SOAP1.1 sadu část musí obsahovat hlavičku Content-Type s typ média application/xop + xml a parametry type = "text/xml" a znaková sada</span><span class="sxs-lookup"><span data-stu-id="24d72-392">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="24d72-393">R4149: Část informační SOAP 1.2 sadu musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry type = "`application/soap+xml`" a `charset`.</span><span class="sxs-lookup"><span data-stu-id="24d72-393">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="24d72-394">Při definuje XOP `charset` parametr pro `application/xop+xml` jako volitelnou, je potřeba pro spolupráci podobná BP 1.1 požadavek na `charset` parametr pro `text/xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="24d72-394">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="24d72-395">R41410: `type` a `charset` parametry musí být v hlavičce Content-Type části informační sadu 1.x protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="24d72-395">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="24d72-396">Podpora koncový bod WCF MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-396">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="24d72-397">Účelem MTOM je určený ke kódování zprávu protokolu SOAP k optimalizaci data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="24d72-397">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="24d72-398">Následuje seznam omezení:</span><span class="sxs-lookup"><span data-stu-id="24d72-398">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="24d72-399">R4151: Může optimalizovat libovolnou položku informace element, který obsahuje data s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="24d72-399">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="24d72-400">B4152: WCF optimalizuje položky element informace, které obsahují data s kódováním base64 a přesáhnout délku 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="24d72-400">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="24d72-401">Koncový bod WCF, který je nakonfigurovaný na použití MTOM vždycky odešlou kódování MTOM zprávy.</span><span class="sxs-lookup"><span data-stu-id="24d72-401">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="24d72-402">I v případě, že žádné části splňují kritéria požadovaná, zpráva je stále kódování MTOM (serializovat jako balíček MIME s jedné součásti MIME obsahující obálku protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="24d72-402">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="24d72-403">Výraz WS-zásad pro MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-403">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="24d72-404">WCF používá následující výraz zásad indikující bodem MTOM využití:</span><span class="sxs-lookup"><span data-stu-id="24d72-404">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="24d72-405">R4211: Předchozí výraz zásad má subjektu zásad koncového bodu a určuje, že všechny zprávy odesílané do a z koncového bodu musí být optimalizovány s použitím MTOM.</span><span class="sxs-lookup"><span data-stu-id="24d72-405">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="24d72-406">B4212: Pokud nakonfigurovaný na použití MTOM optimalizace, koncový bod WCF přidá kontrolní výrazy zásad MTOM do zásady připojené k odpovídající `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="24d72-406">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="24d72-407">Složení s WS-zabezpečení</span><span class="sxs-lookup"><span data-stu-id="24d72-407">Composition with WS-Security</span></span>  
 <span data-ttu-id="24d72-408">MTOM je mechanismus kódování, který je podobný `text/xml` a WCF binární XML.</span><span class="sxs-lookup"><span data-stu-id="24d72-408">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="24d72-409">MTOM nabízí přirozené složení s WS-zabezpečení a jiné WS-\* protokoly: zprávu zabezpečené pomocí protokolu WS-zabezpečení lze optimalizovat pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="24d72-409">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="24d72-410">Příklady</span><span class="sxs-lookup"><span data-stu-id="24d72-410">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="24d72-411">WCF SOAP 1.1 zpráva kódované pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-411">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="24d72-412">Zabezpečení WCF SOAP 1.2 zpráva kódovaný pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="24d72-412">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="24d72-413">V tomto příkladu je zpráva kódované pomocí MTOM a SOAP 1.2, který je chráněný pomocí protokolu WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="24d72-413">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="24d72-414">Binární části identifikovat pro kódování jsou obsah `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpovídající šifrované podpisu a šifrovaný text.</span><span class="sxs-lookup"><span data-stu-id="24d72-414">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="24d72-415">Všimněte si, že `CipherValue` z `EncryptedKey` nebyla určená pro optimalizaci technologie WCF, protože jeho délka je menší pak 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="24d72-415">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
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
