---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 3e56636e8364eec333f9585a0f62f6510561d1cc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253062"
---
# <a name="messaging-protocols"></a><span data-ttu-id="16955-102">Protokoly zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="16955-102">Messaging Protocols</span></span>
<span data-ttu-id="16955-103">Zásobník kanál Windows Communication Foundation (WCF) používá kódování a přenos kanály pro transformaci zprávě interní reprezentace do jeho přenosový formát a jejich odesílání pomocí konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="16955-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="16955-104">Je nejběžnější přenos používá pro interoperabilitu webových služeb HTTP a nejběžnější kódování používá webové služby jsou zpráv přenosu optimalizace mechanismus (MTOM), založený na formátu XML SOAP 1.1 a SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="16955-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="16955-105">Toto téma obsahuje podrobnosti o těchto protokolů náhradník implementaci WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="16955-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="16955-106">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="16955-106">Specification/document</span></span>|<span data-ttu-id="16955-107">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16955-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="16955-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="16955-108">HTTP 1.1</span></span>|http://www.ietf.org/rfc/rfc2616.txt|  
|<span data-ttu-id="16955-109">Ze SOAP 1.1 vazbu protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="16955-109">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="16955-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Část 7</span><span class="sxs-lookup"><span data-stu-id="16955-110">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="16955-111">Ze SOAP 1.2 vazbu protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="16955-111">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="16955-112">http://www.w3.org/TR/soap12-part2/, Část 7</span><span class="sxs-lookup"><span data-stu-id="16955-112">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="16955-113">Toto téma obsahuje podrobnosti o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívat.</span><span class="sxs-lookup"><span data-stu-id="16955-113">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="16955-114">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="16955-114">Specification/Document</span></span>|<span data-ttu-id="16955-115">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16955-115">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="16955-116">XML</span><span class="sxs-lookup"><span data-stu-id="16955-116">XML</span></span>|http://www.w3.org/TR/REC-xml|  
|<span data-ttu-id="16955-117">PROTOKOL SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="16955-117">SOAP 1.1</span></span>|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|<span data-ttu-id="16955-118">Ze SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="16955-118">SOAP 1.2 Core</span></span>|http://www.w3.org/TR/soap12-part1/|  
|<span data-ttu-id="16955-119">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="16955-119">WS-Addressing 2004/08</span></span>|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|<span data-ttu-id="16955-120">W3C webových služeb adresování Core 1.0-</span><span class="sxs-lookup"><span data-stu-id="16955-120">W3C Web Services Addressing 1.0 - Core</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|<span data-ttu-id="16955-121">W3C webových služeb adresování 1.0 - vazba SOAP</span><span class="sxs-lookup"><span data-stu-id="16955-121">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|<span data-ttu-id="16955-122">W3C webových služeb adresování 1.0 - Vazba WSDL</span><span class="sxs-lookup"><span data-stu-id="16955-122">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
<span data-ttu-id="16955-123">W3C webových služeb adresování 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="16955-123">W3C Web Services Addressing 1.0 - Metadata</span></span>|http://www.w3.org/TR/ws-addr-metadata/|  
|<span data-ttu-id="16955-124">Vazba WSDL SOAP1.1</span><span class="sxs-lookup"><span data-stu-id="16955-124">WSDL SOAP1.1 Binding</span></span>|http://www.w3.org/TR/wsdl/|  
|<span data-ttu-id="16955-125">Vazba WSDL SOAP1.2</span><span class="sxs-lookup"><span data-stu-id="16955-125">WSDL SOAP1.2 Binding</span></span>|http://www.w3.org/Submission/wsdl11soap12/|  
  
 <span data-ttu-id="16955-126">Toto téma obsahuje podrobnosti o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívá.</span><span class="sxs-lookup"><span data-stu-id="16955-126">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="16955-127">Specifikace/dokumentu</span><span class="sxs-lookup"><span data-stu-id="16955-127">Specification/document</span></span>|<span data-ttu-id="16955-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16955-128">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="16955-129">XOP</span><span class="sxs-lookup"><span data-stu-id="16955-129">XOP</span></span>|http://www.w3.org/TR/xop10/|  
|<span data-ttu-id="16955-130">MTOM + SOAP 1.2 vazby</span><span class="sxs-lookup"><span data-stu-id="16955-130">MTOM + SOAP 1.2 Binding</span></span>|http://www.w3.org/TR/soap12-mtom/|  
|<span data-ttu-id="16955-131">MTOM SOAP 1.1 vazbu</span><span class="sxs-lookup"><span data-stu-id="16955-131">MTOM SOAP 1.1 Binding</span></span>|http://www.w3.org/Submission/soap11mtom10/|  
|<span data-ttu-id="16955-132">Kontrolní výraz MTOM WS-Policy</span><span class="sxs-lookup"><span data-stu-id="16955-132">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="16955-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="16955-133">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="16955-134">Následující obory názvů XML a přidružené předpony se používají v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="16955-134">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="16955-135">Předpona</span><span class="sxs-lookup"><span data-stu-id="16955-135">Prefix</span></span>|<span data-ttu-id="16955-136">Namespace Uniform Resource Identifier (URI)</span><span class="sxs-lookup"><span data-stu-id="16955-136">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="16955-137">s11</span><span class="sxs-lookup"><span data-stu-id="16955-137">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="16955-138">s12</span><span class="sxs-lookup"><span data-stu-id="16955-138">s12</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="16955-139">wsa</span><span class="sxs-lookup"><span data-stu-id="16955-139">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="16955-140">wsam</span><span class="sxs-lookup"><span data-stu-id="16955-140">wsam</span></span>|http://www.w3.org/2007/05/addressing/metadata|  
|<span data-ttu-id="16955-141">wsap</span><span class="sxs-lookup"><span data-stu-id="16955-141">wsap</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|<span data-ttu-id="16955-142">wsa10</span><span class="sxs-lookup"><span data-stu-id="16955-142">wsa10</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="16955-143">wsaw10</span><span class="sxs-lookup"><span data-stu-id="16955-143">wsaw10</span></span>|http://www.w3.org/2006/05/addressing/wsdl|  
|<span data-ttu-id="16955-144">XOP</span><span class="sxs-lookup"><span data-stu-id="16955-144">xop</span></span>|http://www.w3.org/2004/08/xop/include|  
|<span data-ttu-id="16955-145">xmime</span><span class="sxs-lookup"><span data-stu-id="16955-145">xmime</span></span>|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
<span data-ttu-id="16955-146">distribučního bodu</span><span class="sxs-lookup"><span data-stu-id="16955-146">dp</span></span>|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="16955-147">Protokol SOAP 1.1 a SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="16955-147">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="16955-148">Obálka a zpracování modelu</span><span class="sxs-lookup"><span data-stu-id="16955-148">Envelope and Processing Model</span></span>  
 <span data-ttu-id="16955-149">WCF implementuje zpracování obálky protokolu SOAP 1.1 Basic Profile 1.1 (základní parametr 11) a základní profil 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="16955-149">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="16955-150">Ze SOAP 1.2 obálky zpracování se implementují podle SOAP12 – část 1.</span><span class="sxs-lookup"><span data-stu-id="16955-150">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="16955-151">Tato část popisuje některé volby implementace provedenou WCF s ohledem na základní parametr 11 a SOAP12 – část 1.</span><span class="sxs-lookup"><span data-stu-id="16955-151">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="16955-152">Zpracování povinnou hlavičku</span><span class="sxs-lookup"><span data-stu-id="16955-152">Mandatory Header Processing</span></span>  
 <span data-ttu-id="16955-153">WCF dodržuje pravidla pro zpracování záhlaví označená `mustUnderstand` podle specifikace SOAP 1.1 a SOAP 1.2 s následujícím změnám.</span><span class="sxs-lookup"><span data-stu-id="16955-153">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="16955-154">Zpráva, která vstupuje do zásobníku kanál WCF zpracovává jednotlivé kanály nakonfiguroval prvky přidružené vazeb, například kódování textu zprávy, zabezpečení, spolehlivé zasílání zpráv a transakce.</span><span class="sxs-lookup"><span data-stu-id="16955-154">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="16955-155">Každý kanál rozpozná hlavičky z oboru přidružených a označí je jako srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="16955-155">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="16955-156">Jakmile zprávu zadá dispečer, načte formátovací modul operace záhlaví očekává odpovídající zpráva nebo operace kontraktu a značky, které je srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="16955-156">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="16955-157">Dispečer se ověří, zda nejsou žádné zbývající záhlaví porozuměl jsem jim ale označené jako `mustUnderstand` a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="16955-157">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="16955-158">Zprávy, které obsahují `mustUnderstand` hlavičky, které jsou cíleny na straně příjemce nezpracovávají kódem přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="16955-158">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="16955-159">Tyto vrstvy zpracování umožňuje oddělení mezi vrstev infrastruktury a aplikací vrstvy uzlu SOAP:</span><span class="sxs-lookup"><span data-stu-id="16955-159">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="16955-160">B1111: Hlavičky, které nejsou rozpoznána se zjistí po zpracování zprávy zásobník infrastruktury kanálu WCF, ale předtím, než je zpracován programovacím modelem aplikace</span><span class="sxs-lookup"><span data-stu-id="16955-160">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="16955-161">`mustUnderstand` Hodnota hlavičky se liší mezi SOAP 1.1 a SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="16955-161">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="16955-162">Basic Profile 1.1 vyžaduje, aby `mustUnderstand` hodnota být 0 nebo 1 pro zprávy SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="16955-162">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="16955-163">Protokol SOAP 1.2 umožňuje 0, 1, `false`, a `true` hodnoty, ale doporučuje generování canonical reprezentace `xs:boolean` hodnoty (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="16955-163">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="16955-164">B1112: Vysílá WCF `mustUnderstand` hodnoty 0 a 1 pro verze protokolu SOAP 1.1 a SOAP 1.2 obálku protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="16955-164">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="16955-165">WCF přijímá celou hodnotu prostor `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="16955-165">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="16955-166">Chyby protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="16955-166">SOAP Faults</span></span>  
 <span data-ttu-id="16955-167">Následuje seznam implementace proti konkrétní WCF SOAP.</span><span class="sxs-lookup"><span data-stu-id="16955-167">The following is a list of WCF-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="16955-168">B2121: WCF vrátí následující kódy chyb protokolu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, a `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="16955-168">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="16955-169">B2122: WCF vrátí následující kódy chyb protokolu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, a `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="16955-169">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="16955-170">Vazbu protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="16955-170">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="16955-171">Ze SOAP 1.1 vazbu protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="16955-171">SOAP 1.1 HTTP Binding</span></span>  
 <span data-ttu-id="16955-172">WCF implementuje vazby SOAP1.1 HTTP podle specifikace Basic Profile 1.1 s následující vyjasnění části 3.4:</span><span class="sxs-lookup"><span data-stu-id="16955-172">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="16955-173">B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="16955-173">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="16955-174">B2212: WCF klienti podporují soubory cookie protokolu HTTP v souladu s 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="16955-174">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="16955-175">Ze SOAP 1.2 vazbu protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="16955-175">SOAP 1.2 HTTP Binding</span></span>  
 <span data-ttu-id="16955-176">WCF implementuje vazba SOAP 1.2 HTTP, jak je popsáno ve specifikaci protokolu SOAP 1.2 – část 2 (SOAP12Part2) s následující vyjasnění.</span><span class="sxs-lookup"><span data-stu-id="16955-176">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="16955-177">Parametr volitelný akce pro zavedené SOAP 1.2 `application/soap+xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="16955-177">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="16955-178">Tento parametr je užitečný pro optimalizaci odeslání zprávy bez nutnosti analyzovat text zprávy protokolu SOAP při adresování WS-Addressing není použit.</span><span class="sxs-lookup"><span data-stu-id="16955-178">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="16955-179">R2221: `application/soap+xml` parametr akce, pokud je k dispozici na vyžádání SOAP 1.2, musí odpovídat `soapAction` atribut na `wsoap12:operation` element v rámci odpovídající Vazba WSDL.</span><span class="sxs-lookup"><span data-stu-id="16955-179">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="16955-180">R2222: `application/soap+xml` musí odpovídat parametru akce, pokud je k dispozici na zprávu protokolu SOAP 1.2 `wsa:Action` při použití WS-Addressing 2004/08 nebo WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="16955-180">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="16955-181">Když příchozí požadavek neobsahuje parametr akce WS-Addressing je zakázaná, zpráva `Action` je považováno za nevyhovující zadané.</span><span class="sxs-lookup"><span data-stu-id="16955-181">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="16955-182">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="16955-182">WS-Addressing</span></span>  
 <span data-ttu-id="16955-183">WCF implementuje 3 verze WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="16955-183">WCF implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="16955-184">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="16955-184">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="16955-185">Webové služby W3C adresování Core 1.0 (ADDR10 než CORE) a SOAP vazby (ADDR10 protokolu SOAP)</span><span class="sxs-lookup"><span data-stu-id="16955-185">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="16955-186">WS-Addressing 1.0 - metadat</span><span class="sxs-lookup"><span data-stu-id="16955-186">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="16955-187">Reference koncového bodu</span><span class="sxs-lookup"><span data-stu-id="16955-187">Endpoint References</span></span>  
 <span data-ttu-id="16955-188">Všechny verze WS-Addressing, který implementuje WCF pomocí odkazů na koncový bod k popisu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="16955-188">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="16955-189">Reference koncového bodu a WS-Addressing verze</span><span class="sxs-lookup"><span data-stu-id="16955-189">Endpoint References and WS-Addressing Versions</span></span>  
 <span data-ttu-id="16955-190">WCF implementuje číslo z protokolů infrastruktury, které používají WS-Addressing, zejména `EndpointReference` elementu a `W3C.WsAddressing.EndpointReferenceType` tříd (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="16955-190">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="16955-191">WCF podporuje používání jedné verze elementu WS-Addressing s dalšími protokoly infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="16955-191">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="16955-192">Koncových bodů WCF podporovat jednu verzi elementu WS-Addressing jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="16955-192">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="16955-193">Pro R3111, obor názvů pro `EndpointReference` element nebo typ použitý v zpráv pomocí koncových bodů WCF, které si vyměňují musí odpovídat verzi elementu WS-Addressing implementovaná tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="16955-193">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="16955-194">Například, pokud koncový bod WCF implementuje WS-ReliableMessaging `AcksTo` vrácený takové koncový bod v záhlaví `CreateSequenceResponse` používá verzi elementu WS-Addressing, který `EncodingBinding` prvek určuje pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="16955-194">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="16955-195">Reference koncového bodu a metadat</span><span class="sxs-lookup"><span data-stu-id="16955-195">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="16955-196">Různé scénáře vyžadují komunikaci metadata nebo odkaz na metadata pro daný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="16955-196">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="16955-197">B3121: WCF využívá mechanismy, které je popsáno ve specifikaci WS-MetadataExchange (MEX) části 6 obsahovat metadata ohledně Reference koncového bodu podle hodnoty nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="16955-197">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="16955-198">Představte si třeba situaci, kde služba WCF vyžaduje ověřování pomocí tokenu zabezpečení kontrolní výrazy SAML (Markup Language) vydaného službou vydavatel tokenu v http://sts.fabrikam123.com.</span><span class="sxs-lookup"><span data-stu-id="16955-198">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com.</span></span> <span data-ttu-id="16955-199">Koncový bod WCF popisuje tento požadavek ověřování s použitím `sp:IssuedToken` kontrolní výraz s vnořeným `sp:Issuer` kontrolní výraz odkazuje na vydavatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="16955-199">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="16955-200">Klientské aplikace, které přistupují k `sp:Issuer` kontrolní výraz potřebovat vědět, jak ke komunikaci s koncovým bodem vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="16955-200">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="16955-201">Klient musí vědět, metadata o vydavatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="16955-201">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="16955-202">Pomocí rozšíření metadat odkaz na koncový bod definovaný v MEX, WCF poskytuje odkaz na metadata vydavatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="16955-202">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>  
  
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
  
### <a name="message-addressing-headers"></a><span data-ttu-id="16955-203">Záhlaví adresování zpráv</span><span class="sxs-lookup"><span data-stu-id="16955-203">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="16955-204">Záhlaví zpráv</span><span class="sxs-lookup"><span data-stu-id="16955-204">Message Headers</span></span>  
 <span data-ttu-id="16955-205">Pro obě verze WS-Addressing WCF používá následující záhlaví zpráv podle specifikace `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, a `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="16955-205">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="16955-206">B3211: Pro všechny verze WS-Addressing, WCF respektuje, ale nevytvoří hned po spuštění záhlaví zpráv WS-Addressing `wsa:FaultTo` a `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="16955-206">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="16955-207">Aplikace, které pracují s aplikací služby WCF můžete přidat že tyto hlavičky zpráv a WCF se jejich zpracování odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="16955-207">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="16955-208">Odkaz na parametry a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="16955-208">Reference Parameters and Properties</span></span>  
 <span data-ttu-id="16955-209">Implementuje zpracování parametrů odkaz na koncový bod a odkaz p WCF</span><span class="sxs-lookup"><span data-stu-id="16955-209">WCF implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="16955-210">vlastnosti v souladu s odpovídající specifikací.</span><span class="sxs-lookup"><span data-stu-id="16955-210">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="16955-211">B3221: Když konfigurován pro použití WS-Addressing 2004/08, koncových bodů WCF nerozlišují mezi zpracování vlastnosti odkazu a parametry odkazů.</span><span class="sxs-lookup"><span data-stu-id="16955-211">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="16955-212">Vzorky serveru Exchange zprávu</span><span class="sxs-lookup"><span data-stu-id="16955-212">Message Exchange Patterns</span></span>  
 <span data-ttu-id="16955-213">Pořadí zpráv při volání operace webové služby, které se označuje jako *vzoru výměny zpráv*.</span><span class="sxs-lookup"><span data-stu-id="16955-213">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="16955-214">Podporuje WCF jednosměrné, požadavek odpověď a duplexní zprávy vyměňují vzory.</span><span class="sxs-lookup"><span data-stu-id="16955-214">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="16955-215">Tato část vysvětluje WS-Addressing požadavky na zpracování v závislosti na vzorce výměny zpráv používá zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-215">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="16955-216">V celé této části se pošle žadateli první zprávu a příjemce dostane první zprávu.</span><span class="sxs-lookup"><span data-stu-id="16955-216">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="16955-217">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="16955-217">One-Way Message</span></span>  
 <span data-ttu-id="16955-218">Když koncového bodu WCF je nakonfigurována pro podporu zprávy s daný `Action` dodržovat jednosměrné vzor koncového bodu WCF následuje následující chování a požadavky.</span><span class="sxs-lookup"><span data-stu-id="16955-218">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="16955-219">Pokud není uvedeno jinak, platí pro obě verze WS-Addressing podporované ve službě WCF chování a pravidla:</span><span class="sxs-lookup"><span data-stu-id="16955-219">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="16955-220">R3311: Žadatel musí obsahovat `wsa:To`, `wsa:Action`, tak i hlaviček parametrů odkaz na určeném reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="16955-220">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="16955-221">Když se používá WS-Addressing 2004/08 a [referenční vlastnosti] jsou určena podle reference koncového bodu odpovídající záhlaví musí být přidané do zprávy příliš.</span><span class="sxs-lookup"><span data-stu-id="16955-221">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="16955-222">B3312: Žadatel mohou zahrnovat `MessageID`, `ReplyTo`, a `FaultTo` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="16955-222">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="16955-223">Příjemce infrastruktury je bude ignorovat a bude předávat do aplikace.</span><span class="sxs-lookup"><span data-stu-id="16955-223">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="16955-224">R3313: Když se používá protokol HTTP a žádná zpráva se odesílá na větev odpovědi protokolu HTTP, musíte odeslat straně odpovídajícího odpověď HTTP s prázdným textem zprávy a stavový kód HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="16955-224">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="16955-225">Když kontrakt deklaruje zprávu jednosměrný přenos pomocí protokolu HTTP se používá, odpověď HTTP je stále možné pro odesílání zpráv infrastruktury – například můžete odesílat spolehlivé zasílání zpráv `SequenceAcknowledgement` zprávu na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-225">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="16955-226">B3314: WCF respondér neodesílá jednosměrné zprávy pro zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="16955-226">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="16955-227">Požadavek a odpověď</span><span class="sxs-lookup"><span data-stu-id="16955-227">Request-Reply</span></span>  
 <span data-ttu-id="16955-228">Když koncového bodu WCF je nakonfigurován pro zprávu s danou `Action` Pokud chcete postupovat podle vzoru požadavek odpověď, koncového bodu WCF řídí chování a požadavcích na.</span><span class="sxs-lookup"><span data-stu-id="16955-228">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="16955-229">Pokud není uvedeno jinak, platí pro obě verze WS-Addressing podporované ve službě WCF chování a pravidla:</span><span class="sxs-lookup"><span data-stu-id="16955-229">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>  
  
-   <span data-ttu-id="16955-230">R3321: V požadavku musí obsahovat žadateli `wsa:To`, `wsa:Action`, `wsa:MessageID`, tak i hlaviček pro všechny parametry odkazu nebo referenční vlastnosti (nebo obojí) určené reference koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="16955-230">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="16955-231">R3322: Při použití WS-Addressing 2004/08 `ReplyTo` musí také obsahovat žádosti.</span><span class="sxs-lookup"><span data-stu-id="16955-231">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="16955-232">R3323: Při použití WS-Addressing 1.0 a `ReplyTo` není k dispozici v požadavku, výchozí koncový bod odkaz s vlastností [address] rovno "http://www.w3.org/2005/08/addressing/anonymous" se používá.</span><span class="sxs-lookup"><span data-stu-id="16955-232">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="16955-233">R3324: Žadatel musí obsahovat `wsa:To`, `wsa:Action`, a `wsa:RelatesTo` záhlaví ve zprávě odpovědi a také hlavičky pro všechny parametry odkazu nebo referenční vlastnosti (nebo obojí) určené `ReplyTo` reference koncového bodu v požadavek.</span><span class="sxs-lookup"><span data-stu-id="16955-233">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="16955-234">Na vyřešení chyby webové služby</span><span class="sxs-lookup"><span data-stu-id="16955-234">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="16955-235">R3411: WCF vytvoří následující chyby definované WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="16955-235">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="16955-236">Kód</span><span class="sxs-lookup"><span data-stu-id="16955-236">Code</span></span>|<span data-ttu-id="16955-237">příčina</span><span class="sxs-lookup"><span data-stu-id="16955-237">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="16955-238">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="16955-238">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="16955-239">Zpráva dorazila s `ReplyTo` , která se liší od adresa pro odpovědi pro tento kanál, neexistuje žádný koncový bod na adrese určené v záhlaví Komu.</span><span class="sxs-lookup"><span data-stu-id="16955-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="16955-240">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="16955-240">wsa:ActionNotSupported</span></span>|<span data-ttu-id="16955-241">kanály infrastruktury nebo dispečer spojená s koncovým bodem nebyl rozpoznán akce určená ve `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="16955-241">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="16955-242">R3412: WCF vytvoří následující chyby definované WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="16955-242">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="16955-243">Kód</span><span class="sxs-lookup"><span data-stu-id="16955-243">Code</span></span>|<span data-ttu-id="16955-244">příčina</span><span class="sxs-lookup"><span data-stu-id="16955-244">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="16955-245">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="16955-245">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="16955-246">Duplicitní `wsa:To`, `wsa:ReplyTo`, `wsa:From` nebo `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="16955-246">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="16955-247">Duplicitní `wsa:RelatesTo` se stejným `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="16955-247">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="16955-248">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="16955-248">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="16955-249">Chybí požadované záhlaví adresování.</span><span class="sxs-lookup"><span data-stu-id="16955-249">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="16955-250">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="16955-250">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="16955-251">Zpráva dorazila s `ReplyTo` , která se liší od adresa pro odpovědi pro tento kanál.</span><span class="sxs-lookup"><span data-stu-id="16955-251">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="16955-252">Neexistuje žádný koncový bod na adrese určené v záhlaví Komu.</span><span class="sxs-lookup"><span data-stu-id="16955-252">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="16955-253">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="16955-253">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="16955-254">Zadaná v akci `Action` hlavička nebyla rozpoznána infrastruktury kanály nebo dispečer spojená s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="16955-254">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="16955-255">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="16955-255">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="16955-256">Kanál RM odešle tato porucha zpět, která koncový bod nezpracuje pořadí na základě posouzení `CreateSequence` adrese záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-256">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="16955-257">Do mapy kódu v předchozích tabulkách `FaultCode` v protokolu SOAP 1.1 a `SubCode` (kód = odesílatele) v protokolu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="16955-257">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="16955-258">WSDL 1.1 vazbu a kontrolní výrazy WS-Policy</span><span class="sxs-lookup"><span data-stu-id="16955-258">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="16955-259">Použití elementu WS-Addressing označující</span><span class="sxs-lookup"><span data-stu-id="16955-259">Indicating Use of WS-Addressing</span></span>  
 <span data-ttu-id="16955-260">WCF používá k označení podporu koncového bodu pro konkrétní verzi elementu WS-Addressing kontrolní výrazy zásad.</span><span class="sxs-lookup"><span data-stu-id="16955-260">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="16955-261">Následující kontrolní výraz zásad má koncový bod zásad předmět [WS-PA] a indikuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="16955-261">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="16955-262">Tento kontrolní výraz zásad argumentech specifikaci WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="16955-262">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="16955-263">Následující výraz zásad, že to znamená, že zprávy odeslat/přijmout musí používat WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="16955-263">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="16955-264">Následující kontrolní výraz zásad má předmět zásad koncový bod [WS-PA] a označuje, že musíte používat zprávy odeslané a přijaté z koncového bodu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="16955-264">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="16955-265">`wsaw10:UsingAddressing` Element si z [WS-Addressing-WSDL] a používá se v kontextu v souladu s specifikaci WS-Policy, části 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="16955-265">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="16955-266">Použijte adresování nezmění sémantiku WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazeb.</span><span class="sxs-lookup"><span data-stu-id="16955-266">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="16955-267">Například pokud odpověď na žádost o odeslání do koncového bodu, který používá vazbu protokolu HTTP 1.x adresování a WSDL SOAP, musí poslat odpověď pomocí odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-267">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="16955-268">O reakcích zaslaného prostřednictvím protokolu http odpovědi je WS-AM kontrolního výrazu:</span><span class="sxs-lookup"><span data-stu-id="16955-268">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="16955-269">Kontrolní výraz zásad dokončení může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="16955-269">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="16955-270">Existují však zpráv exchange vzory, kterým přináší výhody máte dvě nezávislé konverzace HTTP připojení mezi žadatelem a respondér, například nevyžádané jednosměrné zprávy odesílané straně odpovídajícího.</span><span class="sxs-lookup"><span data-stu-id="16955-270">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 <span data-ttu-id="16955-271">WCF nabízí funkce, pomocí kterého můžete tvoří dvě základní přenosové kanály kompozitní duplexní kanál, ve kterém jeden kanál se používá pro zprávy o zadávání a druhý se používá pro výstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-271">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="16955-272">V případě přenos pomocí protokolu HTTP kompozitní duplexní poskytuje dvě připojení HTTP konverzace.</span><span class="sxs-lookup"><span data-stu-id="16955-272">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="16955-273">Žadatel používá jedno připojení pro odesílání zpráv na straně odpovídajícího a druhé straně odpovídajícího používá k odesílání zpráv zpět žadateli.</span><span class="sxs-lookup"><span data-stu-id="16955-273">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="16955-274">O reakcích zaslaného prostřednictvím požadavků http samostatné je kontrolní výraz ws-am</span><span class="sxs-lookup"><span data-stu-id="16955-274">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="16955-275">Kontrolní výraz zásad dokončení může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="16955-275">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="16955-276">Použijte následující kontrolní výraz, který má koncový bod zásad subjektu [WS-PA] na koncové body, které používají vazby WSDL 1.1 SOAP 1.x HTTP vyžaduje dva samostatné konverzace připojení protokolu HTTP má být použit pro zpráv odesílaných ze žadatel respondér a respondér žadatel, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="16955-276">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="16955-277">Předchozí příkaz vede k následující požadavky `wsa:ReplyTo` záhlaví zpráv požadavku:</span><span class="sxs-lookup"><span data-stu-id="16955-277">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="16955-278">R3514: Žádost o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastnost nerovná se "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásady s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` s velkou provázaností kontrolní výraz `cdp:CompositeDuplex` připojen.</span><span class="sxs-lookup"><span data-stu-id="16955-278">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="16955-279">R3515: Žádost o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností "http://www.w3.org/2005/08/addressing/anonymous", nebo není `ReplyTo` záhlaví na všechny, pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásad s `wsap10:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` kontrolní výraz připojen.</span><span class="sxs-lookup"><span data-stu-id="16955-279">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="16955-280">R3516: Žádost o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásady s `wsap:UsingAddressing` kontrolní výraz a žádné `cdp:CompositeDuplex`kontrolní výraz připojen.</span><span class="sxs-lookup"><span data-stu-id="16955-280">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="16955-281">Specifikace WS-addressing WSDL pokusí popisují podobnými vazbami protokol zavedením element `<wsaw:Anonymous/>` tři textové hodnoty (povinné, volitelné a zakázané) k označení požadavky na `wsa:ReplyTo` hlavičky (část 3.2).</span><span class="sxs-lookup"><span data-stu-id="16955-281">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="16955-282">Bohužel tyto definice prvku není jako kontrolní výraz v kontextu aplikace WS-Policy, zejména použitelné, protože vyžaduje specifického pro doménu rozšíření pro podporu je určena průsečíkem alternativy pomocí takový prvek jako kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="16955-282">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="16955-283">Tato definice prvku také určuje hodnotu `ReplyTo` záhlaví na rozdíl od chování koncového bodu na lince, což usnadňuje konkrétní přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-283">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="16955-284">Definice akce</span><span class="sxs-lookup"><span data-stu-id="16955-284">Action Definition</span></span>  
 <span data-ttu-id="16955-285">Definuje WS-Addressing 2004/08 `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy.</span><span class="sxs-lookup"><span data-stu-id="16955-285">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="16955-286">WS-Addressing 1.0 WSDL vazby (WS-ADDR10 WSDL) definuje podobně jako atribut `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="16955-286">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="16955-287">Jediným rozdílem mezi těmito dvěma je výchozí akce vzor sémantiku podle 3.3.2 WS-ADDR a části bodu 4.4.4 WS-ADDR10-WSDL.</span><span class="sxs-lookup"><span data-stu-id="16955-287">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="16955-288">Je možné logicky mít dva koncové body, které sdílejí stejný `portType` (nebo smlouvy, v, řečeno terminologií WCF), ale používáte různé verze WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="16955-288">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="16955-289">Ale vzhledem k tomu, že je definována akce `portType` a by neměly měnit napříč koncovými body, které implementují `portType`, bude možné podporovat obě výchozí akci zpracování.</span><span class="sxs-lookup"><span data-stu-id="16955-289">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="16955-290">Chcete-li vyřešit tento spor, WCF podporuje jednu verzi `Action` atribut.</span><span class="sxs-lookup"><span data-stu-id="16955-290">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="16955-291">B3521: Používá WCF `wsaw10:Action` atribut na `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy definované v WS-ADDR10-WSDL k určení `Action` identifikátor URI pro odpovídající zprávy bez ohledu na verzi elementu WS-Addressing používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="16955-291">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="16955-292">Použití koncového bodu odkaz na vnitřní WSDL portu</span><span class="sxs-lookup"><span data-stu-id="16955-292">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="16955-293">WS WSDL ADDR10 oddíle 4.1 rozšiřuje `wsdl:port` prvek, který chcete zahrnout `<wsa10:EndpointReference…/>` podřízený prvek k podrobnému popisu, koncový bod WS-Addressing podmínky.</span><span class="sxs-lookup"><span data-stu-id="16955-293">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="16955-294">Tento nástroj na WS-Addressing 2004/08 rozbalí WCF umožňuje `<wsa:EndpointReference…/>` jako podřízený prvek `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="16955-294">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="16955-295">R3531: Pokud má koncový bod alternativu připojené zásady s `<wsaw10:UsingAddressing/>` kontrolního výrazu zásad odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="16955-295">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="16955-296">R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` hodnota podřízeného elementu musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="16955-296">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="16955-297">R3533: Pokud má koncový bod alternativu připojené zásady s `<wsap:UsingAddressing/>` kontrolního výrazu zásad odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="16955-297">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="16955-298">R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` hodnota podřízeného elementu musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` elementu.</span><span class="sxs-lookup"><span data-stu-id="16955-298">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="16955-299">Kompozice s WS-Security</span><span class="sxs-lookup"><span data-stu-id="16955-299">Composition with WS-Security</span></span>  
 <span data-ttu-id="16955-300">Podle části posouzení zabezpečení v WS-ADDR a WS-ADDR10 všechny adresování zpráv hlavičky doporučují podepsat spolu s text zprávy je svázat dohromady.</span><span class="sxs-lookup"><span data-stu-id="16955-300">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="16955-301">Pokud WS-Security slouží pro ochranu integrity zprávy, musí být podepsané zprávy WS-Addressing, záhlaví, jakož i hlavičky je výsledkem odkaz parametry vlastnosti (nebo obojí) společně s tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-301">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="16955-302">Příklady</span><span class="sxs-lookup"><span data-stu-id="16955-302">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="16955-303">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="16955-303">One-Way Message</span></span>  
 <span data-ttu-id="16955-304">V tomto scénáři odesílatel odešle zprávu jednosměrné příjemci.</span><span class="sxs-lookup"><span data-stu-id="16955-304">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="16955-305">SOAP 1.2, protokol HTTP 1.1 a 1.0 W3C WS-Addressing se používají.</span><span class="sxs-lookup"><span data-stu-id="16955-305">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="16955-306">Struktura zprávy požadavku: Hlavičky zprávy zahrnují `wsa10:To` a `wsa10:Action` elementy.</span><span class="sxs-lookup"><span data-stu-id="16955-306">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="16955-307">Tělo zprávy obsahuje konkrétní `<app:Ping>` element z oboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="16955-307">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="16955-308">Hlavičky protokolu HTTP: Cíl v příspěvku odpovídá identifikátoru URI v `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="16955-308">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="16955-309">Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="16955-309">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="16955-310">Parametry `charset` a `action` jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="16955-310">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="16955-311">`action` Odpovídá hodnotě parametru hlavičku Content-Type `wsa10:Action` záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-311">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
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
  
 <span data-ttu-id="16955-312">Příjemce odpoví prázdnou odpověď HTTP a stav 202.</span><span class="sxs-lookup"><span data-stu-id="16955-312">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="16955-313">Příklad odpovědi protokolu HTTP:</span><span class="sxs-lookup"><span data-stu-id="16955-313">An example of the HTTP response:</span></span>  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="16955-314">Mechanismus optimalizaci přenosu zprávy protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="16955-314">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="16955-315">Tato část popisuje podrobnosti implementace WCF MTOM SOAP protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-315">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="16955-316">Technologie MTOM je mechanismus kódování SOAP zprávy stejné třídy jako kódování tradiční text/XML nebo WCF binární kódování.</span><span class="sxs-lookup"><span data-stu-id="16955-316">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="16955-317">MTOM zahrnuje následující položky:</span><span class="sxs-lookup"><span data-stu-id="16955-317">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="16955-318">Kódování XML a balení mechanismus popsal [XOP], který optimalizuje XML informačních položek do samostatných částí binární obsahující binární data zakódovaná ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="16955-318">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="16955-319">Zapouzdření MIME XOP balíčku, který serializuje informační sadu XML a každá část binární balíčku XOP do samostatné části MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-319">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="16955-320">MIME XOP kódování u protokolu SOAP 1.x obálky.</span><span class="sxs-lookup"><span data-stu-id="16955-320">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="16955-321">HTTP přenosu vazby.</span><span class="sxs-lookup"><span data-stu-id="16955-321">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="16955-322">Je možné použít MTOM s jiným protokolem než HTTP přenosy s použitím technologie WCF.</span><span class="sxs-lookup"><span data-stu-id="16955-322">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="16955-323">Ale v tomto tématu se zaměříme na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-323">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="16955-324">Formát MTOM využívá velké sady specifikace pokrývající MTOM samotné XOP a MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-324">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="16955-325">Modularitu této specifikace sady je poněkud obtížné rekonstrukci přesných požadavcích na sémantiku formátu a zpracování.</span><span class="sxs-lookup"><span data-stu-id="16955-325">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="16955-326">Tato část popisuje požadavky na zpracování a formát vazby MTOM HTTP.</span><span class="sxs-lookup"><span data-stu-id="16955-326">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="16955-327">Kódování MTOM zpráv</span><span class="sxs-lookup"><span data-stu-id="16955-327">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="16955-328">Generování zprávy MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-328">Generating MTOM messages</span></span>  
 <span data-ttu-id="16955-329">[XOP] části 3.1 popisuje postup kódování XML pomocí elementu informačních položek, které obsahují hodnoty ve formátu base64 do abstraktně definovaná balíčku XOP.</span><span class="sxs-lookup"><span data-stu-id="16955-329">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="16955-330">Následující sled kroků popisuje proces kódování MTOM konkrétní:</span><span class="sxs-lookup"><span data-stu-id="16955-330">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="16955-331">Zajistěte, aby obsahoval obálku protokolu SOAP být zakódovaný, aby se žádná položka informace o elementu s `[namespace name]` z "http://www.w3.org/2004/08/xop/include" a `[local name]` z `Include`.</span><span class="sxs-lookup"><span data-stu-id="16955-331">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="16955-332">Vytvořte prázdný balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-332">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="16955-333">Identifikujte v rámci původní XML informační sadu položek informací elementu optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="16955-333">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="16955-334">Pro položky, které chcete optimalizovat, znaky, které tvoří `[children]` informace prvku položky musí být v kanonickém tvaru z `xs:base64Binary` (viz XSD-2, 3.2.16 base64Binary) a nesmí obsahovat žádné prázdné znaky před vložené, nebo Následující obsah prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="16955-334">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>  
  
4.  <span data-ttu-id="16955-335">Vytvoří obálku protokolu SOAP XOP, který je kopií původního obálku protokolu SOAP, ale s podřízenými informace každého prvku bod identifikován v předchozím kroku nahrazuje `xop:Include` položka informací o elementu vypočte takto:</span><span class="sxs-lookup"><span data-stu-id="16955-335">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="16955-336">Transformujte nahrazené znaků na binární data zpracováním jako data zakódovaná ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="16955-336">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="16955-337">Generovat jedinečný hodnota hlavičky Content-ID, která splňuje požadavky R3133 a R3134.</span><span class="sxs-lookup"><span data-stu-id="16955-337">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="16955-338">Vygenerujte hlavička MIME Content-Transfer-Encoding s binární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="16955-338">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="16955-339">Pokud element položka informací o optimalizaci ([nadřazený] nově vloženou `xop:Include` položek informací elementu) má `xmime:contentType` atribut položky informace, generování záhlaví Content-Type MIME s hodnotou `xmime:contentType` atribut.</span><span class="sxs-lookup"><span data-stu-id="16955-339">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="16955-340">Generovat nové binární část MIME s obsahem tvořen binární data dekódovaná z nahrazené znaky zpracovány jako base64, Hlavička Content-ID z 4b, Hlavička Content-Transfer-Encoding ze 4 jádra, Hlavička Content-Type, pokud je vygenerovaný v kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="16955-340">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="16955-341">Přidat `href` atribut `xop:Include` element s hodnotou cid: identifikátor uri odvozený od hodnota hlavičky Content-ID vygenerované v kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="16955-341">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="16955-342">Odebrat nadřazený "\<" a ">" znaky adresy URL řídicí zbývající řetězec a přidejte tuto předponu `cid:`.</span><span class="sxs-lookup"><span data-stu-id="16955-342">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="16955-343">Následující minimální znaková sada je povinná-li být uvozena RFC1738 a RFC2396.</span><span class="sxs-lookup"><span data-stu-id="16955-343">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="16955-344">Může být uvozena jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="16955-344">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="16955-345">Vytvoření kořenové části MIME se XOP obálku protokolu SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="16955-345">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="16955-346">Zápis hlavičky protokolu HTTP, včetně hlavičku HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="16955-346">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="16955-347">Zapsat balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-347">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="16955-348">Zpracování zprávy MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-348">Processing MTOM messages</span></span>  
 <span data-ttu-id="16955-349">Zpracování MTOM zpráva je přesně naopak procesu popsaného v předchozím "generování MTOM zprávy" části:</span><span class="sxs-lookup"><span data-stu-id="16955-349">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="16955-350">Ujistěte se, má kořenová část MIME Content-Type `application/xop+xml`.</span><span class="sxs-lookup"><span data-stu-id="16955-350">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="16955-351">Sestavení obálky protokolu SOAP analýzou kořenovou část MIME balíčku jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="16955-351">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="16955-352">Kódování znaků závisí `charset` parametru Content-Type kořenovou část MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-352">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="16955-353">Pro každou položku element informace konstruovaný obálku protokolu SOAP, která má, jako jedinými členy vlastností [podřízené] `xop:Include` položek informací elementu:</span><span class="sxs-lookup"><span data-stu-id="16955-353">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="16955-354">Odeberte `cid:` Předpona a unescape – identifikátor URI – řídicí sekvence všechny (RFC 2396) v hodnotě `@href` atribut `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="16955-354">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="16955-355">Uzavřete výsledný řetězec v "\<", ">".</span><span class="sxs-lookup"><span data-stu-id="16955-355">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="16955-356">Vyhledejte část MIME s hodnota hlavičky Content-ID, který se shoduje s řetězcem odvozené v kroku 3a.</span><span class="sxs-lookup"><span data-stu-id="16955-356">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="16955-357">Nahradit `xop:Include` položka informací o elementu, který se zobrazí `children` vlastnosti každé položky s položkami znak informace, které představují kódování canonical base64 (viz XSD-2, 3.2.16 base64Binary) z obsahu entity část MIME identifikovali v kroku 3b (efektivně nahradit `xop:Include` položka informací o elementu s daty, které jsou znovu vytvořena z část balíček).</span><span class="sxs-lookup"><span data-stu-id="16955-357">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="16955-358">Hlavičku HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="16955-358">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="16955-359">Následující seznam obsahuje WCF objasnit, kontaktujte pro formát hlavičky protokolu HTTP Content-Type 1.x kódování MTOM zprávy SOAP odvozený od požadavky uvedené v samotnou specifikaci MTOM a jsou odvozeny z MTOM a dokumentu RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="16955-359">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="16955-360">R4131: Hlavičku HTTP Content-Type musí mít hodnotu multipart/related (velká a malá písmena) a jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="16955-360">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="16955-361">Názvy parametrů rozlišují velikost písmen.</span><span class="sxs-lookup"><span data-stu-id="16955-361">Parameter names are case-insensitive.</span></span> <span data-ttu-id="16955-362">Parametr pořadí není důležité.</span><span class="sxs-lookup"><span data-stu-id="16955-362">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="16955-363">Úplné Backus-Naur formuláře (BNF) hlavičky Content-Type pro zprávy MIME je uvedena v RFC 2045, část 5.1.</span><span class="sxs-lookup"><span data-stu-id="16955-363">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="16955-364">R4132: Hlavičku HTTP Content-Type musí mít parametr typu s hodnotou `application/xop+xml` uzavřený do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="16955-364">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="16955-365">Požadavek na použití dvojitých uvozovek není definován v dokumentu RFC 2387, text dodržuje všechny parametry typu multipart/related média pravděpodobně obsahovat vyhrazené znaky, jako je "\@" nebo "/" a je proto nutné dvojité uvozovky značky.</span><span class="sxs-lookup"><span data-stu-id="16955-365">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="16955-366">R4133: Hlavičku HTTP Content-Type musí mít parametr počáteční hodnotu hlavičky Content-ID z část MIME obsahující SOAP 1.x obálky, uzavřen do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="16955-366">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="16955-367">Pokud tento parametr spuštění se vynechá, první část MIME musí obsahovat SOAP 1.x obálky.</span><span class="sxs-lookup"><span data-stu-id="16955-367">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="16955-368">R4134: Hlavičku HTTP Content-Type pro zprávu MTOM SOAP 1.1 kódovaný musí obsahovat úvodní informace o parametr s hodnotou typu text/xml, uzavřen do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="16955-368">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="16955-369">R4135: Hlavičku HTTP Content-Type pro zprávu SOAP 1.2 MTOM kódovaný musí obsahovat úvodní informace o parametr s hodnotou `application/soap+xml`, uzavřené v dvojitých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="16955-369">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="16955-370">R4136: Hlavičku HTTP Content-Type pro zprávu MTOM kódováním SOAP 1.x musí mít parametr hranic s hodnotou (uzavřený v dvojitých uvozovkách), který odpovídá ohraničení MIME BNF definovaný v dokumentu RFC 2046 části 5.1.1</span><span class="sxs-lookup"><span data-stu-id="16955-370">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="16955-371">Příklady:</span><span class="sxs-lookup"><span data-stu-id="16955-371">Examples:</span></span>  
  
     <span data-ttu-id="16955-372">OPRAVIT</span><span class="sxs-lookup"><span data-stu-id="16955-372">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="16955-373">OPRAVIT</span><span class="sxs-lookup"><span data-stu-id="16955-373">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="16955-374">NESPRÁVNÝ</span><span class="sxs-lookup"><span data-stu-id="16955-374">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="16955-375">Část MIME informační sadu</span><span class="sxs-lookup"><span data-stu-id="16955-375">Infoset MIME Part</span></span>  
 <span data-ttu-id="16955-376">SOAP 1.x obálky je zapouzdřen v rámci kořenového balíček XOP MIME a se často nazývá `infoset` část.</span><span class="sxs-lookup"><span data-stu-id="16955-376">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="16955-377">R4141: SOAP 1.x obálky musí být zapouzdřen v rámci kořenového balíček XOP MIME, volá se, `infoset` část a odkazované z HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="16955-377">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="16955-378">R4142: SOAP `Infoset` část musí obsahovat následující hlavičky MIME: `Content-ID`, `Content-Transfer-Encoding`, a `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="16955-378">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="16955-379">Formát hlavičky Content-ID je definován specifikací 2045 RFC jako</span><span class="sxs-lookup"><span data-stu-id="16955-379">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="16955-380">kde `msg-id` je definován v dokumentu RFC 2822, (, který nahrazuje RFC 822 odkazovat v dokumentu RFC 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="16955-380">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="16955-381">a je efektivně e-mailovou adresu uzavřený do složených závorek "\<" a ">".</span><span class="sxs-lookup"><span data-stu-id="16955-381">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="16955-382">`[CFWS]` Předpon a přípon byly přidány v dokumentu RFC 2822 provádět komentáře a neměl by se zachovat vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="16955-382">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="16955-383">R4143: Hodnotu hlavičky Content-ID pro část MIME informační sadu musí následovat `msg-id` produkčním prostředí z 2822 RFC s `[CFWS]` předpon a přípon částí vynechán.</span><span class="sxs-lookup"><span data-stu-id="16955-383">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="16955-384">Počet implementací MIME mírnější požadavky pro hodnotu uzavřený do složených závorek "\<" a ">" bude e-mailovou adresu a použít `absoluteURI` uzavřeny v "\<", ">" Kromě e-mailovou adresu.</span><span class="sxs-lookup"><span data-stu-id="16955-384">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="16955-385">Tato verze služby WCF používá hodnoty hlavičky MIME Content-ID ve formátu:</span><span class="sxs-lookup"><span data-stu-id="16955-385">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="16955-386">R4144: MTOM procesory by měla přijímat hlavička Content-ID hodnoty, které odpovídají následující mírnější `msg-id`.</span><span class="sxs-lookup"><span data-stu-id="16955-386">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="16955-387">MIME (RFC 2045) obsahuje hlavičku Content-Transfer-Encoding komunikovat kódování obsahu části MIME.</span><span class="sxs-lookup"><span data-stu-id="16955-387">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="16955-388">Definované pro Content-Transfer-Encoding výchozí hodnota je 7 bitů, což není vhodný pro většinu zprávy protokolu SOAP, takže hlavičku Content-Transfer-Encoding je potřeba větší interoperability:</span><span class="sxs-lookup"><span data-stu-id="16955-388">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="16955-389">R4145: Informační sadu SOAP část musí obsahovat hlavičku Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="16955-389">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="16955-390">R4146: Pokud kódování znaků pro obálku protokolu SOAP je UTF-8, musí být hodnota hlavičky Content-Transfer-Encoding 8 bitů.</span><span class="sxs-lookup"><span data-stu-id="16955-390">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="16955-391">R4147: Pokud kódování znaků pro obálku protokolu SOAP je UTF-16, hodnota hlavičky Content-Transfer-Encoding musí být binární.</span><span class="sxs-lookup"><span data-stu-id="16955-391">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="16955-392">Závislosti [XOP] části 5</span><span class="sxs-lookup"><span data-stu-id="16955-392">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="16955-393">R4148: Informační sadu SOAP1.1 část musí obsahovat hlavičku Content-Type s typ média application/xop + xml a parametry type = "text/xml" a znaková sada</span><span class="sxs-lookup"><span data-stu-id="16955-393">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="16955-394">R4149: Informační sadu SOAP 1.2 část musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry type = "`application/soap+xml`" a `charset`.</span><span class="sxs-lookup"><span data-stu-id="16955-394">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="16955-395">Zatímco XOP definuje `charset` parametr pro `application/xop+xml` být volitelné, je potřeba podobný BP 1.1 požadavek na funkční spolupráce `charset` parametr pro `text/xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="16955-395">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="16955-396">R41410: `type` a `charset` parametry musí být k dispozici v hlavičce Content-Type části SOAP 1.x informační sadu.</span><span class="sxs-lookup"><span data-stu-id="16955-396">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="16955-397">Podpora koncových bodů WCF MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-397">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="16955-398">Účelem MTOM je určený ke kódování zprávy protokolu SOAP pro optimalizaci dat s kódováním base64.</span><span class="sxs-lookup"><span data-stu-id="16955-398">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="16955-399">Následuje seznam omezení:</span><span class="sxs-lookup"><span data-stu-id="16955-399">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="16955-400">R4151: Může být optimalizován libovolné položky informace o elementu, který obsahuje data zakódovaná ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="16955-400">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="16955-401">B4152: WCF optimalizuje element informačních položek, které obsahují data zakódovaná ve formátu base64 a přesáhnout délku 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="16955-401">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="16955-402">Koncový bod WCF, který je nakonfigurován pro použití MTOM vždycky odešlou MTOM kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="16955-402">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="16955-403">I v případě, že žádné části splňovat požadovaná kritéria, zprávy se stále kódování MTOM (serializovat jako balíček MIME s jednou částí MIME obsahující obálku protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="16955-403">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="16955-404">Kontrolní výraz WS-Policy pro MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-404">WS-Policy Assertion for MTOM</span></span>  
 <span data-ttu-id="16955-405">WCF používá k označení MTOM využití koncovým bodem následující kontrolní výraz zásad:</span><span class="sxs-lookup"><span data-stu-id="16955-405">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="16955-406">R4211: Předchozí kontrolního výrazu zásad má předmětu zásad koncového bodu a určuje, že všechny zprávy odesílané do a z koncového bodu musí být optimalizovalo pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="16955-406">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="16955-407">B4212: Když konfigurován pro použití MTOM optimalizace, koncový bod WCF přidá kontrolní výraz zásad MTOM zásady připojené k odpovídající `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="16955-407">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="16955-408">Kompozice s WS-Security</span><span class="sxs-lookup"><span data-stu-id="16955-408">Composition with WS-Security</span></span>  
 <span data-ttu-id="16955-409">MTOM je mechanismus, který je podobný `text/xml` a WCF binární formát XML.</span><span class="sxs-lookup"><span data-stu-id="16955-409">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="16955-410">MTOM nabízí přirozené složení s WS-Security a dalších WS-\* protokoly: zpráva zabezpečena WS-Security, lze optimalizovat pomocí funkce MTOM.</span><span class="sxs-lookup"><span data-stu-id="16955-410">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="16955-411">Příklady</span><span class="sxs-lookup"><span data-stu-id="16955-411">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="16955-412">WCF SOAP 1.1 zpráva kódovaný pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-412">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
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
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="16955-413">Zabezpečení WCF SOAP 1.2 zpráva kódovaný pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="16955-413">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="16955-414">V tomto příkladu je zpráva kódovaný pomocí MTOM a SOAP 1.2, který je chráněný pomocí WS-Security.</span><span class="sxs-lookup"><span data-stu-id="16955-414">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="16955-415">Binární částí pro kódování se obsah `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpovídající šifrované podpis a šifrovaného textu.</span><span class="sxs-lookup"><span data-stu-id="16955-415">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="16955-416">Všimněte si, že `CipherValue` z `EncryptedKey` nebyla identifikována pro optimalizaci službou WCF, protože její délka je menší pak 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="16955-416">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>  
  
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
