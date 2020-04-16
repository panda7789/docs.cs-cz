---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463835"
---
# <a name="messaging-protocols"></a><span data-ttu-id="79b66-102">Protokoly zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="79b66-102">Messaging Protocols</span></span>

<span data-ttu-id="79b66-103">Zásobník kanálu WCF (Windows Communication Foundation) využívá kódování a přenos kanálů k transformaci reprezentace interní zprávy do svého formátu drátu a odeslat pomocí určitého přenosu.</span><span class="sxs-lookup"><span data-stu-id="79b66-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="79b66-104">Nejběžnější přenos používaný pro interoperabilitu webových služeb je HTTP a nejběžnější kódování používaná webovými službami jsou SOAP 1.1, SOAP 1.2 a Message Transmission Optimization Mechanism (MTOM).</span><span class="sxs-lookup"><span data-stu-id="79b66-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="79b66-105">Toto téma popisuje podrobnosti implementace WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>pro následující protokoly používané .</span><span class="sxs-lookup"><span data-stu-id="79b66-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="79b66-106">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="79b66-106">Specification/document:</span></span>

- [<span data-ttu-id="79b66-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="79b66-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="79b66-108">[SOAP 1.1 VAZBA HTTP](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), oddíl 7</span><span class="sxs-lookup"><span data-stu-id="79b66-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="79b66-109">[SOAP 1.2 HTTP vazba](https://www.w3.org/TR/soap12-part2) Oddíl 7</span><span class="sxs-lookup"><span data-stu-id="79b66-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="79b66-110">Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zaměstnávají.</span><span class="sxs-lookup"><span data-stu-id="79b66-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="79b66-111">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="79b66-111">Specification/Document:</span></span>

- [<span data-ttu-id="79b66-112">Xml</span><span class="sxs-lookup"><span data-stu-id="79b66-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="79b66-113">MÝDLO 1,1</span><span class="sxs-lookup"><span data-stu-id="79b66-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="79b66-114">MÝDLO 1.2 Jádro</span><span class="sxs-lookup"><span data-stu-id="79b66-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="79b66-115">WS-Adresování 2004/08</span><span class="sxs-lookup"><span data-stu-id="79b66-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="79b66-116">W3C Webové služby Adresování 1.0 - Core</span><span class="sxs-lookup"><span data-stu-id="79b66-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="79b66-117">W3C Web Services Addressing 1.0 - SOAP Binding</span><span class="sxs-lookup"><span data-stu-id="79b66-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="79b66-118">W3C Webové služby adresování 1.0 - WSDL vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="79b66-119">W3C Web Services Addressing 1.0 - Metadata</span><span class="sxs-lookup"><span data-stu-id="79b66-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="79b66-120">WSDL SOAP1.1 Vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="79b66-121">WSDL SOAP1.2 Vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="79b66-122">Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zaměstnává.</span><span class="sxs-lookup"><span data-stu-id="79b66-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="79b66-123">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="79b66-123">Specification/document:</span></span>

- [<span data-ttu-id="79b66-124">XOP</span><span class="sxs-lookup"><span data-stu-id="79b66-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="79b66-125">MTOM + SOAP 1.2 Vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="79b66-126">MTOM SOAP 1.1 Vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="79b66-127">Kontrolní výraz zásad služby MTOM WS</span><span class="sxs-lookup"><span data-stu-id="79b66-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="79b66-128">V celém tématu se používají následující obory názvů XML a přidružené předpony:</span><span class="sxs-lookup"><span data-stu-id="79b66-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="79b66-129">Předpona</span><span class="sxs-lookup"><span data-stu-id="79b66-129">Prefix</span></span> | <span data-ttu-id="79b66-130">Identifikátor prostředku oboru názvů (URI)</span><span class="sxs-lookup"><span data-stu-id="79b66-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="79b66-131">S11</span><span class="sxs-lookup"><span data-stu-id="79b66-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="79b66-132">s12</span><span class="sxs-lookup"><span data-stu-id="79b66-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="79b66-133">wsa</span><span class="sxs-lookup"><span data-stu-id="79b66-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="79b66-134">wsam (Wsam)</span><span class="sxs-lookup"><span data-stu-id="79b66-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="79b66-135">wsap</span><span class="sxs-lookup"><span data-stu-id="79b66-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="79b66-136">wsa10 řekl:</span><span class="sxs-lookup"><span data-stu-id="79b66-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="79b66-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="79b66-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="79b66-138">xop</span><span class="sxs-lookup"><span data-stu-id="79b66-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="79b66-139">xmime</span><span class="sxs-lookup"><span data-stu-id="79b66-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="79b66-140">Dp</span><span class="sxs-lookup"><span data-stu-id="79b66-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="79b66-141">MÝDLO 1.1 a SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="79b66-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="79b66-142">Obálka a model zpracování</span><span class="sxs-lookup"><span data-stu-id="79b66-142">Envelope and Processing Model</span></span>
<span data-ttu-id="79b66-143">WCF implementuje soap 1.1 obálky zpracování podle základníprofil 1.1 (BP11) a základní profil 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="79b66-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="79b66-144">SOAP 1.2 Zpracování obálek je implementováno po SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="79b66-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="79b66-145">Tento oddíl vysvětluje některé volby implementace přijaté WCF, pokud jde o BP11 a SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="79b66-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="79b66-146">Povinné zpracování záhlaví</span><span class="sxs-lookup"><span data-stu-id="79b66-146">Mandatory Header Processing</span></span>
<span data-ttu-id="79b66-147">WCF se řídí pravidly `mustUnderstand` pro zpracování hlaviček označených ve specifikacích SOAP 1.1 a SOAP 1.2 s následujícími variantami.</span><span class="sxs-lookup"><span data-stu-id="79b66-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="79b66-148">Zpráva, která vstupuje do zásobníku kanálu WCF, je zpracována jednotlivými kanály nakonfigurovanými přidruženými prvky vazby, například kódováním textových zpráv, zabezpečením, spolehlivým zasíláním zpráv a transakcemi.</span><span class="sxs-lookup"><span data-stu-id="79b66-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="79b66-149">Každý kanál rozpozná záhlaví z přidruženého oboru názvů a označí je jako srozumitelné.</span><span class="sxs-lookup"><span data-stu-id="79b66-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="79b66-150">Jakmile zpráva zadá dispečera, operace formatter čte záhlaví očekávané odpovídající zprávy/operace smlouvy a označí je pochopil.</span><span class="sxs-lookup"><span data-stu-id="79b66-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="79b66-151">Potom dispečer ověří, zda všechny zbývající záhlaví `mustUnderstand` nejsou chápány, ale označeny jako a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="79b66-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="79b66-152">Zprávy, `mustUnderstand` které obsahují záhlaví, které jsou zaměřeny na příjemce nejsou zpracovány kód emitované aplikace příjemce.</span><span class="sxs-lookup"><span data-stu-id="79b66-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="79b66-153">Takové vrstvené zpracování umožňuje oddělení mezi vrstvami infrastruktury a aplikačními vrstvami uzlu SOAP:</span><span class="sxs-lookup"><span data-stu-id="79b66-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="79b66-154">B1111: Záhlaví, které nejsou pochopeny jsou zjištěny po zpracování zprávy zásobníku kanálu infrastruktury WCF, ale před zpracováním aplikací</span><span class="sxs-lookup"><span data-stu-id="79b66-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="79b66-155">Hodnota `mustUnderstand` záhlaví se liší mezi SOAP 1.1 a SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="79b66-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="79b66-156">Základní profil 1.1 `mustUnderstand` vyžaduje, aby hodnota byla 0 nebo 1 pro zprávy SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="79b66-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="79b66-157">SOAP 1.2 umožňuje 0, `false` `true` 1 , a jako hodnoty, ale doporučuje `xs:boolean` vyzařovat`false` `true`kanonické reprezentace hodnot ( , ).</span><span class="sxs-lookup"><span data-stu-id="79b66-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="79b66-158">B1112: WCF `mustUnderstand` vyzařuje hodnoty 0 a 1 pro soap 1.1 a SOAP 1.2 verze obálky SOAP.</span><span class="sxs-lookup"><span data-stu-id="79b66-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="79b66-159">WCF přijímá celý hodnotový `xs:boolean` prostor `mustUnderstand` pro záhlaví (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="79b66-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="79b66-160">CHYBY SOAP</span><span class="sxs-lookup"><span data-stu-id="79b66-160">SOAP Faults</span></span>
<span data-ttu-id="79b66-161">Následuje seznam implementací chyb SOAP specifických pro WCF.</span><span class="sxs-lookup"><span data-stu-id="79b66-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="79b66-162">B2121: WCF vrátí následující kódy chyb `s11:mustUnderstand` `s11:Client`SOAP `s11:Server`1.1: , , a .</span><span class="sxs-lookup"><span data-stu-id="79b66-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="79b66-163">B2122: WCF vrátí následující kódy chyb `s12:MustUnderstand` `s12:Sender`SOAP `s12:Receiver`1.2: , , a .</span><span class="sxs-lookup"><span data-stu-id="79b66-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="79b66-164">Vazba HTTP</span><span class="sxs-lookup"><span data-stu-id="79b66-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="79b66-165">SOAP 1.1 HTTP vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="79b66-166">WCF implementuje VAZBU SOAP1.1 HTTP podle oddílu 3.4 specifikace základního profilu 1.1 s následujícími vyjasněními:</span><span class="sxs-lookup"><span data-stu-id="79b66-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="79b66-167">B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="79b66-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="79b66-168">B2212: Klienti WCF podporují HTTP Cookies v souladu s 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="79b66-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="79b66-169">SOAP 1.2 HTTP vazba</span><span class="sxs-lookup"><span data-stu-id="79b66-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="79b66-170">WCF implementuje SOAP 1.2 HTTP vazbu, jak je popsáno ve specifikaci SOAP 1.2-part 2 (SOAP12Part2) s následujícím vysvětlením.</span><span class="sxs-lookup"><span data-stu-id="79b66-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="79b66-171">SOAP 1.2 zavedl volitelný parametr `application/soap+xml` akce pro typ média.</span><span class="sxs-lookup"><span data-stu-id="79b66-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="79b66-172">Tento parametr je užitečný pro optimalizaci odeslání zprávy bez nutnosti analyzovat text zprávy SOAP při ws adresování není použit.</span><span class="sxs-lookup"><span data-stu-id="79b66-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="79b66-173">R2221: `application/soap+xml` Parametr akce, pokud je k dispozici na požadavku `soapAction` SOAP `wsoap12:operation` 1.2, musí odpovídat atributu na elementu uvnitř odpovídající vazby WSDL.</span><span class="sxs-lookup"><span data-stu-id="79b66-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="79b66-174">R2222: `application/soap+xml` Parametr akce, pokud je k dispozici na `wsa:Action` zprávě SOAP 1.2, musí odpovídat při ws adresování 2004/08 nebo WS adresování 1.0 jsou používány.</span><span class="sxs-lookup"><span data-stu-id="79b66-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="79b66-175">Pokud ws adresování je zakázáno a příchozí požadavek `Action` neobsahuje parametr akce, zpráva se považuje za není zadán.</span><span class="sxs-lookup"><span data-stu-id="79b66-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="79b66-176">WS-adresování</span><span class="sxs-lookup"><span data-stu-id="79b66-176">WS-Addressing</span></span>
<span data-ttu-id="79b66-177">WCF implementuje 3 verze WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="79b66-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="79b66-178">WS-Adresování 2004/08</span><span class="sxs-lookup"><span data-stu-id="79b66-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="79b66-179">W3C Web Services Addressing 1.0 Core (ADDR10-CORE) a SOAP Vazba (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="79b66-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="79b66-180">WS-Adresování 1.0 - Metadata</span><span class="sxs-lookup"><span data-stu-id="79b66-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="79b66-181">Odkazy na koncový bod</span><span class="sxs-lookup"><span data-stu-id="79b66-181">Endpoint References</span></span>
<span data-ttu-id="79b66-182">Všechny verze WS-Addressing, které implementuje WCF použít odkazy na koncový bod k popisu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="79b66-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="79b66-183">Odkazy na koncové ho a ws adresování verze</span><span class="sxs-lookup"><span data-stu-id="79b66-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="79b66-184">WCF implementuje řadu protokolů infrastruktury, které používají WS-Adresování a zejména `EndpointReference` element a `W3C.WsAddressing.EndpointReferenceType` třídy (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="79b66-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="79b66-185">WCF podporuje použití obou verzí WS-Addressing s jinými protokoly infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="79b66-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="79b66-186">Koncové body WCF podporují jednu verzi ws adresování na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79b66-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="79b66-187">Pro R3111 obor názvů `EndpointReference` pro prvek nebo typ používaný ve zprávách vyměňovaných s koncovým bodem WCF musí odpovídat verzi WS adresování implementované tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="79b66-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="79b66-188">Například pokud koncový bod WCF implementuje WS-ReliableMessaging, `AcksTo` záhlaví vrácené takový koncový bod uvnitř `EncodingBinding` `CreateSequenceResponse` používá WS-Addressing verze, která určuje prvek pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79b66-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="79b66-189">Odkazy na koncové ho a metadata</span><span class="sxs-lookup"><span data-stu-id="79b66-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="79b66-190">Řada scénářů vyžaduje komunikaci metadat nebo odkaz na metadata pro daný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79b66-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="79b66-191">B3121: WCF používá mechanismy popsané ve specifikaci WS-MetadataExchange (MEX) Oddíl 6 zahrnout metadata pro odkazy na koncové parametry podle hodnoty nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="79b66-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="79b66-192">Zvažte scénář, kdy služba WCF vyžaduje ověření pomocí tokenu jazyka s výrazy zabezpečení `http://sts.fabrikam123.com`(SAML) vydaného vystavitelem tokenu na adrese .</span><span class="sxs-lookup"><span data-stu-id="79b66-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="79b66-193">Koncový bod WCF popisuje tento požadavek ověřování `sp:IssuedToken` pomocí `sp:Issuer` kontrolního výrazu s vnořeným kontrolním výrazem odkazujícím na vystavittele tokenu.</span><span class="sxs-lookup"><span data-stu-id="79b66-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="79b66-194">Klientské aplikace, `sp:Issuer` které přistupují k kontrolnímu výrazu, potřebují vědět, jak komunikovat s koncovým bodem vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="79b66-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="79b66-195">Klient potřebuje znát metadata o vystaviteli tokenu.</span><span class="sxs-lookup"><span data-stu-id="79b66-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="79b66-196">Pomocí rozšíření metadat odkazu koncového bodu definované v MEX WCF poskytuje odkaz na metadata vystavitela tokenu.</span><span class="sxs-lookup"><span data-stu-id="79b66-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="79b66-197">Záhlaví adresování zpráv</span><span class="sxs-lookup"><span data-stu-id="79b66-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="79b66-198">Záhlaví zpráv</span><span class="sxs-lookup"><span data-stu-id="79b66-198">Message Headers</span></span>
<span data-ttu-id="79b66-199">Pro obě verze WS-Addressing wcf používá následující záhlaví zpráv, jak `wsa:To` `wsa:ReplyTo`je `wsa:Action` `wsa:MessageID`předepsáno `wsa:RelatesTo`specifikace , , , , a .</span><span class="sxs-lookup"><span data-stu-id="79b66-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="79b66-200">B3211: Pro všechny verze WS adresování WCF vyznamenání, ale nevytváří po vybalení, `wsa:FaultTo` `wsa:From`WS adresování záhlaví zpráv a .</span><span class="sxs-lookup"><span data-stu-id="79b66-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="79b66-201">Aplikace, které interagují s aplikacemi WCF můžete přidat tyto hlavičky zpráv a WCF bude zpracovávat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="79b66-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="79b66-202">Referenční parametry a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="79b66-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="79b66-203">WCF implementuje zpracování referenčních parametrů koncového bodu a referenčních vlastností v souladu s příslušnými specifikacemi.</span><span class="sxs-lookup"><span data-stu-id="79b66-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="79b66-204">B3221: Při konfiguraci pro použití WS-Addressing 2004/08 koncové body WCF nerozlišují mezi zpracováním vlastností reference a referenčními parametry.</span><span class="sxs-lookup"><span data-stu-id="79b66-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="79b66-205">Vzory výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="79b66-205">Message Exchange Patterns</span></span>
<span data-ttu-id="79b66-206">Posloupnost zpráv zapojených do vyvolání operace webové služby se označuje jako *vzor výměny zpráv*.</span><span class="sxs-lookup"><span data-stu-id="79b66-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="79b66-207">WCF podporuje jednosměrné, požadavek odpověď a duplexní zprávy exchange vzory.</span><span class="sxs-lookup"><span data-stu-id="79b66-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="79b66-208">Tato část objasňuje ws adresování požadavky na zpracování zpráv v závislosti na vzoru výměny zpráv se používá.</span><span class="sxs-lookup"><span data-stu-id="79b66-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="79b66-209">V této části žadatel odešle první zprávu a respondér obdrží první zprávu.</span><span class="sxs-lookup"><span data-stu-id="79b66-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="79b66-210">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="79b66-210">One-Way Message</span></span>
<span data-ttu-id="79b66-211">Když je koncový bod WCF nakonfigurován `Action` tak, aby podporoval zprávy s daným způsobem, který se řídí jednosměrným vzorem, koncový bod WCF následuje následující chování a požadavky.</span><span class="sxs-lookup"><span data-stu-id="79b66-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="79b66-212">Není-li uvedeno jinak, chování a pravidla platí pro obě verze WS-Adresování podporované v WCF:</span><span class="sxs-lookup"><span data-stu-id="79b66-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="79b66-213">R3311: Žadatel musí `wsa:To`obsahovat , `wsa:Action`a záhlaví pro všechny referenční parametry určené odkazem na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79b66-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="79b66-214">Při ws adresování 2004/08 a [reference vlastnosti] jsou určeny odkaz na koncový bod, odpovídající záhlaví musí být přidány do zprávy příliš.</span><span class="sxs-lookup"><span data-stu-id="79b66-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="79b66-215">B3312: Žadatel může `MessageID`obsahovat `ReplyTo` `FaultTo` , a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="79b66-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="79b66-216">Infrastruktura přijímače je bude ignorovat a budou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="79b66-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="79b66-217">R3313: Pokud je použit protokol HTTP a na straně protokolu HTTP není odesílána žádná zpráva, musí respondér odeslat odpověď HTTP s prázdným tělem a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="79b66-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="79b66-218">Pokud je přenos HTTP používán a smlouva operace deklaruje zprávu jednosměrně, odpověď HTTP lze stále použít pro `SequenceAcknowledgement` odesílání zpráv infrastruktury – například spolehlivé zasílání zpráv může odeslat zprávu na odpověď HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="79b66-219">B3314: WCF respondér neodešle zprávu o chybě v reakci na jednosměrnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="79b66-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="79b66-220">Požadavek a odpověď</span><span class="sxs-lookup"><span data-stu-id="79b66-220">Request-Reply</span></span>
<span data-ttu-id="79b66-221">Pokud je koncový bod WCF nakonfigurován `Action` pro zprávu s danou tak, aby sledovala vzor požadavku a odpovědi, koncový bod WCF následuje následující chování a požadavky.</span><span class="sxs-lookup"><span data-stu-id="79b66-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="79b66-222">Není-li uvedeno jinak, chování a pravidla platí pro obě verze WS-Adresování podporované v WCF:</span><span class="sxs-lookup"><span data-stu-id="79b66-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="79b66-223">R3321: Žadatel musí zahrnout do `wsa:To` `wsa:Action`požadavku `wsa:MessageID`, , a hlavičky pro všechny referenční parametry nebo referenční vlastnosti (nebo obojí) určené odkazem na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="79b66-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="79b66-224">R3322: Při ws `ReplyTo` adresování 2004/08 musí být také zahrnuty v požadavku.</span><span class="sxs-lookup"><span data-stu-id="79b66-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="79b66-225">R3323: Při ws adresování 1.0 a `ReplyTo` není k dispozici v požadavku, výchozí odkaz na `http://www.w3.org/2005/08/addressing/anonymous` koncový bod s [adresa] vlastnost rovná se používá.</span><span class="sxs-lookup"><span data-stu-id="79b66-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="79b66-226">R3324: Žadatel musí `wsa:To`obsahovat `wsa:Action` `wsa:RelatesTo` , a záhlaví ve zprávě odpovědi, jakož i záhlaví pro všechny referenční parametry `ReplyTo` nebo referenční vlastnosti (nebo obojí) určené odkazem na koncový bod v požadavku.</span><span class="sxs-lookup"><span data-stu-id="79b66-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="79b66-227">Chyby adresování webových služeb</span><span class="sxs-lookup"><span data-stu-id="79b66-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="79b66-228">R3411: WCF vytváří následující chyby definované WS adresování 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79b66-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="79b66-229">kód</span><span class="sxs-lookup"><span data-stu-id="79b66-229">Code</span></span> | <span data-ttu-id="79b66-230">Příčina</span><span class="sxs-lookup"><span data-stu-id="79b66-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="79b66-231">Zpráva byla doručena s, `ReplyTo` která se liší od odpovědi adresu stanovenou pro tento kanál; neexistuje žádný koncový bod naslouchání na adresu zadanou v hlavičce Do.</span><span class="sxs-lookup"><span data-stu-id="79b66-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="79b66-232">kanály infrastruktury nebo dispečer přidružený ke koncovému `Action` bodu nerozpoznávají akci zadanou v hlavičce.</span><span class="sxs-lookup"><span data-stu-id="79b66-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="79b66-233">R3412: WCF vytváří následující chyby definované WS adresování 1.0.</span><span class="sxs-lookup"><span data-stu-id="79b66-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="79b66-234">kód</span><span class="sxs-lookup"><span data-stu-id="79b66-234">Code</span></span> | <span data-ttu-id="79b66-235">Příčina</span><span class="sxs-lookup"><span data-stu-id="79b66-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="79b66-236">Duplikát `wsa:To`, `wsa:ReplyTo`nebo `wsa:From` `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="79b66-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="79b66-237">`wsa:RelatesTo` Duplikovat `RelationshipType`se stejným .</span><span class="sxs-lookup"><span data-stu-id="79b66-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="79b66-238">Chybí požadovaná hlavička adresování.</span><span class="sxs-lookup"><span data-stu-id="79b66-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="79b66-239">Zpráva byla doručena `ReplyTo` s, která se liší od odpovědi adresu vytvořenou pro tento kanál.</span><span class="sxs-lookup"><span data-stu-id="79b66-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="79b66-240">Neexistuje žádný koncový bod naslouchání na adresu zadanou v hlavičce Do.</span><span class="sxs-lookup"><span data-stu-id="79b66-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="79b66-241">Akce zadaná `Action` v hlavičce není rozpoznána kanály infrastruktury nebo dispečerem přidruženým ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="79b66-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="79b66-242">Rm kanál odešle tuto chybu zpět, označující koncový bod nebude `CreateSequence` zpracovávat sekvence na základě kontroly adresování záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b66-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="79b66-243">Kód v předchozích tabulkách se mapuje v `FaultCode` SOAP 1.1 a `SubCode` (s Code=Sender) v SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="79b66-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="79b66-244">WSDL 1.1 Tvrzení o vazbě a zásadách WS</span><span class="sxs-lookup"><span data-stu-id="79b66-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="79b66-245">Označující použití ws-adresování</span><span class="sxs-lookup"><span data-stu-id="79b66-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="79b66-246">WCF používá kontrolní výrazy zásad k označení podpory koncového bodu pro konkrétní verzi WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="79b66-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="79b66-247">Následující tvrzení zásad má předmět zásad koncového bodu [WS-PA] a označuje zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79b66-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="79b66-248">Toto tvrzení zásad rozšiřuje ws adresování 2004/08 specifikace.</span><span class="sxs-lookup"><span data-stu-id="79b66-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="79b66-249">Následující tvrzení zásad to znamená, že zprávy odeslané nebo přijaté musí používat WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="79b66-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="79b66-250">Následující tvrzení zásad má předmět zásad koncového bodu [WS-PA] a označuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="79b66-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="79b66-251">Prvek `wsaw10:UsingAddressing` je vypůjčen z [WS-Addressing-WSDL] a používá se v kontextu WS-Policy v souladu s uvedenou specifikací, oddíl 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="79b66-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="79b66-252">Použití adresování nemění sémantiku WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazby.</span><span class="sxs-lookup"><span data-stu-id="79b66-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="79b66-253">Například pokud je očekávána odpověď na požadavek, který je odeslán do koncového bodu, který používá adresování a WSDL SOAP 1.x HTTP vazby, odpověď musí být odeslána pomocí odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="79b66-254">Pro odpovědi odeslané přes odpověď http, WS-AM kontrolní výraz je:</span><span class="sxs-lookup"><span data-stu-id="79b66-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="79b66-255">Úplné tvrzení zásad může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="79b66-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="79b66-256">Existují však vzory výměny zpráv, které těží z toho, že mezi žadatelem a respondérem jsou vytvořena dvě nezávislá konverzní připojení HTTP, například nevyžádané jednosměrné zprávy odeslané respondérem.</span><span class="sxs-lookup"><span data-stu-id="79b66-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="79b66-257">WCF nabízí funkci, kterou dva základní kanály přenosu mohou tvořit složený duplexní kanál, kde jeden kanál se používá pro vstupní zprávy a druhý se používá pro výstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b66-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="79b66-258">V případě přenosu HTTP composite duplex poskytuje dvě připojení http.</span><span class="sxs-lookup"><span data-stu-id="79b66-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="79b66-259">Žadatel používá jedno připojení k odesílání zpráv respondérovi a respondér používá druhé k odesílání zpráv zpět žadateli.</span><span class="sxs-lookup"><span data-stu-id="79b66-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="79b66-260">Pro odpovědi odeslané přes samostatné požadavky http, ws-am tvrzení je</span><span class="sxs-lookup"><span data-stu-id="79b66-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="79b66-261">Úplné tvrzení zásad může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="79b66-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="79b66-262">Použití následující ho výrazu, který má předmět zásad koncového bodu [WS-PA] na koncové body, které používají WSDL 1.1 SOAP 1.x HTTP vazby vyžaduje dvě samostatné konverzní http připojení, které mají být použity pro zprávy přetékající od respondéru k respondéru a respondér na žadateli, resp.</span><span class="sxs-lookup"><span data-stu-id="79b66-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="79b66-263">Předchozí příkaz vede k následujícím `wsa:ReplyTo` požadavkům v záhlaví pro zprávy požadavku:</span><span class="sxs-lookup"><span data-stu-id="79b66-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="79b66-264">R3514: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu musí `http://www.w3.org/2005/08/addressing/anonymous` mít záhlaví s vlastností není rovno, pokud koncový bod používá WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` kontrolní výraz spolu s `cdp:CompositeDuplex` připojeným.</span><span class="sxs-lookup"><span data-stu-id="79b66-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="79b66-265">R3515: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu `http://www.w3.org/2005/08/addressing/anonymous`musí mít záhlaví `ReplyTo` s vlastností rovnou , nebo nemusí mít záhlaví vůbec, pokud koncový bod `wsap10:UsingAddressing` používá WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s kontrolní výraz a žádný `cdp:CompositeDuplex` kontrolní výraz připojen.</span><span class="sxs-lookup"><span data-stu-id="79b66-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="79b66-266">R3516: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu `http://www.w3.org/2005/08/addressing/anonymous` musí mít záhlaví s vlastností, která se rovná, pokud koncový bod `wsap:UsingAddressing` používá `cdp:CompositeDuplex` WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s kontrolní výraz a bez kontrolnívýraz připojen.</span><span class="sxs-lookup"><span data-stu-id="79b66-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="79b66-267">WS adresování WSDL specifikace pokusí popsat podobné vazby `<wsaw:Anonymous/>` protokolu zavedením element se třemi textové hodnoty (povinné, `wsa:ReplyTo` volitelné a zakázané) k označení požadavků na záhlaví (oddíl 3.2).</span><span class="sxs-lookup"><span data-stu-id="79b66-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="79b66-268">Bohužel taková definice prvku není zvláště použitelná jako výraz v kontextu WS-Policy, protože vyžaduje rozšíření specifické pro doménu pro podporu průniku alternativy pomocí takový prvek jako kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="79b66-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="79b66-269">Tato definice prvku také označuje `ReplyTo` hodnotu záhlaví na rozdíl od chování koncového bodu v drátě, což je specifické pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="79b66-270">Definice akce</span><span class="sxs-lookup"><span data-stu-id="79b66-270">Action Definition</span></span>
<span data-ttu-id="79b66-271">WS-Addressing 2004/08 definuje `wsa:Action` atribut `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` pro prvky.</span><span class="sxs-lookup"><span data-stu-id="79b66-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="79b66-272">WS-Addressing 1.0 WSDL vazba (WS-ADDR10-WSDL) `wsaw10:Action`definuje podobný atribut .</span><span class="sxs-lookup"><span data-stu-id="79b66-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="79b66-273">Jediný rozdíl mezi těmito dvěma je výchozí akce vzor sémantiku popsané v části 3.3.2 WS-ADDR a oddíl 4.4.4 WS-ADDR10-WSDL, příslušně.</span><span class="sxs-lookup"><span data-stu-id="79b66-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="79b66-274">Je rozumné mít dva koncové body, `portType` které sdílejí stejné (nebo smlouvy, v terminologii WCF), ale pomocí různých verzí WS adresování.</span><span class="sxs-lookup"><span data-stu-id="79b66-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="79b66-275">Ale vzhledem k tomu, že Action je definován `portType` a `portType`neměla by se měnit mezi koncovými body, které implementují , je nemožné podporovat oba výchozí vzory akcí.</span><span class="sxs-lookup"><span data-stu-id="79b66-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="79b66-276">Chcete-li vyřešit tuto kontroverzi, WCF `Action` podporuje jednu verzi atributu.</span><span class="sxs-lookup"><span data-stu-id="79b66-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="79b66-277">B3521: WCF `wsaw10:Action` používá `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` atribut na prvky definované v WS-ADDR10-WSDL k určení `Action` IDENTIFIKÁTORU URI pro odpovídající zprávy bez ohledu na ws adresování verze používané koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="79b66-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="79b66-278">Použití odkazu koncového bodu uvnitř portu WSDL</span><span class="sxs-lookup"><span data-stu-id="79b66-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="79b66-279">WS-ADDR10-WSDL oddíl 4.1 `wsdl:port` rozšiřuje prvek `<wsa10:EndpointReference…/>` zahrnout podřízený prvek k popisu koncového bodu v WS adresování termíny.</span><span class="sxs-lookup"><span data-stu-id="79b66-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="79b66-280">WCF rozšiřuje tento nástroj na WS-Addressing 2004/08, umožňuje `<wsa:EndpointReference…/>` zobrazit `wsdl:port`jako podřízený prvek .</span><span class="sxs-lookup"><span data-stu-id="79b66-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="79b66-281">R3531: Pokud koncový bod má připojené alternativy zásad s výrazem `<wsaw10:UsingAddressing/>` zásad, odpovídající `wsdl:port` prvek může obsahovat podřízený prvek `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="79b66-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="79b66-282">R3532: Pokud `wsdl:port` a obsahuje `<wsa10:EndpointReference …/>`podřízený prvek , `wsa10:EndpointReference/wsa10:Address` podřízená `@address` hodnota prvku `wsdl:port` / `wsdl:location` musí odpovídat hodnotě atributu prvku na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="79b66-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="79b66-283">R3533: Pokud koncový bod má připojené `<wsap:UsingAddressing/>` alternativy zásad `wsdl:port` s výrazem zásad, odpovídající prvek může obsahovat podřízený prvek `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="79b66-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="79b66-284">R3534: Pokud `wsdl:port` a obsahuje `<wsa:EndpointReference …/>` `wsa:EndpointReference/wsa:Address` podřízený prvek , musí hodnota `@address` podřízeného `wsdl:port` prvku odpovídat hodnotě atributu prvku na stejné úrovni. / `wsdl:location`</span><span class="sxs-lookup"><span data-stu-id="79b66-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="79b66-285">Složení s WS-Security</span><span class="sxs-lookup"><span data-stu-id="79b66-285">Composition with WS-Security</span></span>
<span data-ttu-id="79b66-286">Podle části aspektu zabezpečení v WS-ADDR a WS-ADDR10, všechny adresování záhlaví zpráv se doporučuje podepsat společně s textem zprávy svázat je dohromady.</span><span class="sxs-lookup"><span data-stu-id="79b66-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="79b66-287">Při ws-security se používá pro ochranu integrity zprávy, WS adresování záhlaví zpráv, stejně jako záhlaví vyplývající z referenční parametry nebo vlastnosti (nebo obojí) musí být podepsány společně s textem zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b66-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="79b66-288">Příklady</span><span class="sxs-lookup"><span data-stu-id="79b66-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="79b66-289">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="79b66-289">One-Way Message</span></span>
<span data-ttu-id="79b66-290">V tomto scénáři odesílatel odešle jednosměrnou zprávu příjemci.</span><span class="sxs-lookup"><span data-stu-id="79b66-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="79b66-291">SOAP 1.2, HTTP 1.1 a W3C WS-Addressing 1.0 se používají.</span><span class="sxs-lookup"><span data-stu-id="79b66-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="79b66-292">Struktura požadavku na zprávu: Záhlaví `wsa10:To` `wsa10:Action` zpráv obsahují a prvky.</span><span class="sxs-lookup"><span data-stu-id="79b66-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="79b66-293">Text zprávy obsahuje `<app:Ping>` určitý prvek z oboru názvů aplikace.</span><span class="sxs-lookup"><span data-stu-id="79b66-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="79b66-294">Hlavičky HTTP: Cíl v post odpovídá `wsa10:To` URI v prvku.</span><span class="sxs-lookup"><span data-stu-id="79b66-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="79b66-295">Hlavička typu obsahu má `application/soap+xml` hodnotu požadovanou soap 1.2.</span><span class="sxs-lookup"><span data-stu-id="79b66-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="79b66-296">Parametry `charset` `action` a jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="79b66-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="79b66-297">Parametr `action` hlavičky Typu obsahu odpovídá hodnotě `wsa10:Action` záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="79b66-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

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

<span data-ttu-id="79b66-298">Příjemce odpoví prázdnou odpovědí HTTP a stavem 202.</span><span class="sxs-lookup"><span data-stu-id="79b66-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="79b66-299">Příklad odpovědi HTTP:</span><span class="sxs-lookup"><span data-stu-id="79b66-299">An example of the HTTP response:</span></span>

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

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="79b66-300">Mechanismus optimalizace přenosu zpráv SOAP</span><span class="sxs-lookup"><span data-stu-id="79b66-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="79b66-301">Tato část popisuje podrobnosti implementace WCF pro mtom PROTOKOLU HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="79b66-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="79b66-302">Technologie MTOM je mechanismus kódování zpráv SOAP stejné třídy jako tradiční kódování textu/XML nebo binární kódování WCF.</span><span class="sxs-lookup"><span data-stu-id="79b66-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="79b66-303">MTOM zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="79b66-303">MTOM includes the following:</span></span>

- <span data-ttu-id="79b66-304">Mechanismus kódování a balení XML popsaný [XOP], který optimalizuje informační položky XML obsahující binární data kódovaná základnou 64 do samostatných binárních částí.</span><span class="sxs-lookup"><span data-stu-id="79b66-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="79b66-305">Zapouzdření balíčku XOP MIME, které serializuje XML Infoset a každou binární část balíčku XOP do samostatné části MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="79b66-306">Kódování MIME XOP aplikované na obálku SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="79b66-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="79b66-307">Přenosová vazba HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-307">An HTTP transport binding.</span></span>

<span data-ttu-id="79b66-308">Je možné použít MTOM s non-HTTP přenosy s WCF.</span><span class="sxs-lookup"><span data-stu-id="79b66-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="79b66-309">V tomto tématu se však zaměříme na HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="79b66-310">Formát MTOM využívá velkou sadu specifikací pokrývajících samotné MTOM, XOP a MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="79b66-311">Modularita této sady specifikací ztěžuje rekonstrukci přesných požadavků na formát a sémantiku zpracování.</span><span class="sxs-lookup"><span data-stu-id="79b66-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="79b66-312">Tato část popisuje požadavky na formát a zpracování vazby Protokolu HTTP mtom.</span><span class="sxs-lookup"><span data-stu-id="79b66-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="79b66-313">Kódování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="79b66-314">Generování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-314">Generating MTOM messages</span></span>
<span data-ttu-id="79b66-315">Oddíl [XOP] 3.1 popisuje proces kódování XML s položkami informací o elementech, které obsahují hodnoty base64 do abstraktně definovaného balíčku XOP.</span><span class="sxs-lookup"><span data-stu-id="79b66-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="79b66-316">Následující posloupnost kroků popisuje proces kódování specifické pro MTOM:</span><span class="sxs-lookup"><span data-stu-id="79b66-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="79b66-317">Ujistěte se, že obálka SOAP, která má `[namespace name]` `http://www.w3.org/2004/08/xop/include` být `[local name]` zakódována, neobsahuje žádnou položku informací o prvku s a a a `Include`.</span><span class="sxs-lookup"><span data-stu-id="79b66-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="79b66-318">Vytvořte prázdný balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="79b66-319">Identifikujte v rámci původní informační sady XML položky informací o elementech, které mají být optimalizovány.</span><span class="sxs-lookup"><span data-stu-id="79b66-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="79b66-320">Pro položky, které mají být optimalizovány, musí být znaky, které tvoří `[children]` `xs:base64Binary` položku informací o prvku, v kanonické podobě (viz XSD-2, 3.2.16 base64Binary) a nesmí obsahovat žádné prázdné znaky předcházející, vřádící s obsahem neprázdné mezery nebo za ním.</span><span class="sxs-lookup"><span data-stu-id="79b66-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="79b66-321">Vytvořte obálku XOP SOAP, která je kopií původní obálky SOAP, ale s podřízenými `xop:Include` položkami informací o každém prvku identifikovanými v předchozím kroku nahrazeny položkou informací o prvku, která je vytvořena takto:</span><span class="sxs-lookup"><span data-stu-id="79b66-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="79b66-322">Transformujte nahrazené znaky na binární data jejich zpracováním jako data kódovaná base64.</span><span class="sxs-lookup"><span data-stu-id="79b66-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="79b66-323">Vygenerujte jedinečnou hodnotu záhlaví Content-ID, která splňuje požadavky R3133 a R3134.</span><span class="sxs-lookup"><span data-stu-id="79b66-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="79b66-324">Vygenerujte hlavičku MIME s hodnotou binární.</span><span class="sxs-lookup"><span data-stu-id="79b66-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="79b66-325">Pokud položka informací o prvku, která je optimalizována `xop:Include` ([nadřazená] položky informací o nově vloženém prvku), obsahuje položku informace o atributu, `xmime:contentType` vygenerujte hlavičku MIME typu obsahu s hodnotou atributu. `xmime:contentType`</span><span class="sxs-lookup"><span data-stu-id="79b66-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="79b66-326">Generovat nový binární MIME část s obsahem tvořenbinární data dekódována z nahrazených znaků zpracovaných jako base64, Content-ID záhlaví z 4b, Obsah-Transfer-Kódování záhlaví z 4c, Content-Type záhlaví, pokud jsou generovány v kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="79b66-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="79b66-327">Přidejte `href` atribut `xop:Include` k prvku s hodnotou cid: uri odvozené z hodnoty hlavičky Content-ID generované v kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="79b66-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="79b66-328">Odeberte ohraničující znaky "\<" a ">", uniknete zbývajícímu řetězci adresou URL a přidejte předponu `cid:`.</span><span class="sxs-lookup"><span data-stu-id="79b66-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="79b66-329">Následující minimální znaková sada je nutné uvozena RFC1738 a RFC2396.</span><span class="sxs-lookup"><span data-stu-id="79b66-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="79b66-330">Ostatní znaky mohou být uvozeny.</span><span class="sxs-lookup"><span data-stu-id="79b66-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="79b66-331">Vytvořte kořenový díl MIME s obálkou XOP SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="79b66-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="79b66-332">Napište záhlaví protokolu HTTP, včetně hlavičky typu obsahu HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="79b66-333">Napište balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="79b66-334">Zpracování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-334">Processing MTOM messages</span></span>
<span data-ttu-id="79b66-335">Zpracování zprávy MTOM je přesný opak procesu popsaného v předchozí části Generování zpráv MTOM:</span><span class="sxs-lookup"><span data-stu-id="79b66-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="79b66-336">Ujistěte se, že kořenová `application/xop+xml`část MIME má typ obsahu .</span><span class="sxs-lookup"><span data-stu-id="79b66-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="79b66-337">Vytvořte obálku SOAP analýzou kořenové části MIME balíčku jako dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="79b66-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="79b66-338">Kódování znaků je určeno `charset` parametrem typu Content-Type kořenové části MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="79b66-339">Pro každou položku informací o prvku v konstruované soap envelope, která má `xop:Include` jako jediný člen své vlastnosti [children] položku s informacemi o prvku:</span><span class="sxs-lookup"><span data-stu-id="79b66-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="79b66-340">Odeberte `cid:` předponu a unescape všechny sekvence uri-escape (RFC 2396) v hodnotě `@href` atribut u `xop:Include` prvku.</span><span class="sxs-lookup"><span data-stu-id="79b66-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="79b66-341">Výsledek uzavřete do\<" ", ">".</span><span class="sxs-lookup"><span data-stu-id="79b66-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="79b66-342">Vyhledejte část MIME s hodnotou záhlaví Content-ID, která odpovídá řetězci odvozenému v kroku 3a.</span><span class="sxs-lookup"><span data-stu-id="79b66-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="79b66-343">Nahraďte položku `xop:Include` informací `children` o elementu, která se zobrazí ve vlastnosti každé položky, položkami informací o znaku, které představují kódování canonical base64 (viz XSD-2, `xop:Include` 3.2.16 base64Binary) těla entity části MIME identifikované v kroku 3b (účinně nahradit položku informací o prvku daty rekonstruovanými z dílu balíčku).</span><span class="sxs-lookup"><span data-stu-id="79b66-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="79b66-344">Hlavička typu obsahu HTTP</span><span class="sxs-lookup"><span data-stu-id="79b66-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="79b66-345">Následuje seznam wcf vysvětlení pro formát hlavičky typu obsahu HTTP soap 1.x MTOM kódované zprávy odvozené z požadavků uvedených ve specifikaci MTOM sám a jsou odvozeny z MTOM a RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="79b66-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="79b66-346">R4131: Hlavička typu obsahu HTTP musí mít hodnotu multipart/related (bez rozlišování velkých a malých písmen) a její parametry.</span><span class="sxs-lookup"><span data-stu-id="79b66-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="79b66-347">Názvy parametrů nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="79b66-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="79b66-348">Pořadí parametrů není významné.</span><span class="sxs-lookup"><span data-stu-id="79b66-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="79b66-349">Úplný formulář Backus-Naur (BNF) záhlaví typu obsahu pro zprávy MIME je uveden v oddíle 5.1 rfc 2045.</span><span class="sxs-lookup"><span data-stu-id="79b66-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="79b66-350">R4132: Hlavička typu obsahu HTTP musí mít `application/xop+xml` parametr typu s hodnotou uzavřenou v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="79b66-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="79b66-351">Zatímco požadavek na použití dvojitých uvozovek není v rfc 2387 explicitní, text pozoruje, že všechny\@parametry typu multipart/related média s největší pravděpodobností obsahují vyhrazené znaky jako " " nebo "/", a proto potřebují dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="79b66-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="79b66-352">R4133: Hlavička typu obsahu HTTP by měla mít počáteční parametr s hodnotou hlavičky Content-ID části MIME, která obsahuje obálku SOAP 1.x, uzavřenou v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="79b66-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="79b66-353">Pokud je parametr start vynechán, první část MIME musí obsahovat obálku SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="79b66-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="79b66-354">R4134: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.1 MTOM musí obsahovat parametr start-info s hodnotou text/xml, která je uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="79b66-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="79b66-355">R4135: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.2 MTOM musí `application/soap+xml`obsahovat parametr start-info s hodnotou , uzavřenou v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="79b66-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="79b66-356">R4136: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.x MTOM musí mít parametr hranice s hodnotou (uzavřenou v uvozovkách), která odpovídá hranici MIME BNF definované v RFC 2046, oddíl 5.1.1</span><span class="sxs-lookup"><span data-stu-id="79b66-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="79b66-357">Příklady:</span><span class="sxs-lookup"><span data-stu-id="79b66-357">Examples:</span></span>

     <span data-ttu-id="79b66-358">Správné</span><span class="sxs-lookup"><span data-stu-id="79b66-358">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="79b66-359">Správné</span><span class="sxs-lookup"><span data-stu-id="79b66-359">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="79b66-360">Nesprávné</span><span class="sxs-lookup"><span data-stu-id="79b66-360">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="79b66-361">Infoset MIME část</span><span class="sxs-lookup"><span data-stu-id="79b66-361">Infoset MIME Part</span></span>
<span data-ttu-id="79b66-362">Obálka SOAP 1.x je zapouzdřena jako kořenová část balíčku `infoset` XOP MIME a často se nazývá součást.</span><span class="sxs-lookup"><span data-stu-id="79b66-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="79b66-363">R4141: Obálka SOAP 1.x musí být zapouzdřena jako kořenová `infoset` část balíčku XOP MIME, nazývaná součást a odkazovaná z typu obsahu HTTP.</span><span class="sxs-lookup"><span data-stu-id="79b66-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="79b66-364">R4142: Část `Infoset` SOAP musí obsahovat následující `Content-ID`hlavičky MIME: , `Content-Transfer-Encoding`, a `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="79b66-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="79b66-365">Formát hlavičky Content-ID je definován rfc 2045 jako</span><span class="sxs-lookup"><span data-stu-id="79b66-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="79b66-366">kde `msg-id` je definována v RFC 2822 (která nahrazuje RFC 822, uvedeno v RFC 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="79b66-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="79b66-367">a je fakticky e-mailovou\<adresou uzavřenou v " " a ">".</span><span class="sxs-lookup"><span data-stu-id="79b66-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="79b66-368">Předpona `[CFWS]` a přípona byly přidány v RFC 2822 nést komentáře a by neměly být použity k zachování interoperability.</span><span class="sxs-lookup"><span data-stu-id="79b66-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="79b66-369">R4143: Hodnota hlavičky Content-ID pro část MIME `msg-id` infosady musí následovat výroba z `[CFWS]` RFC 2822 s vynechánou předponou a příponou.</span><span class="sxs-lookup"><span data-stu-id="79b66-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="79b66-370">Řada implementací MIME uvolnila požadavky na hodnotu uzavřenou v "\<" a `absoluteURI` ">"\<jako e-mailovou adresu a použitou v " " , ">" kromě e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="79b66-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="79b66-371">Tato verze WCF používá hodnoty hlavičky MIME content id formuláře:</span><span class="sxs-lookup"><span data-stu-id="79b66-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="79b66-372">R4144: Procesory MTOM by měly přijímat hodnoty záhlaví `msg-id`Content-ID, které odpovídají následujícímu uvolněnému .</span><span class="sxs-lookup"><span data-stu-id="79b66-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="79b66-373">MIME (RFC 2045) poskytuje hlavičku Content-Transfer-Encoding pro komunikaci kódování obsahu části MIME.</span><span class="sxs-lookup"><span data-stu-id="79b66-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="79b66-374">Výchozí definice pro kódování content-transfer-encoding je 7bitová, což není vhodné pro většinu zpráv SOAP, takže hlavička content-transfer-encoding je potřebná pro větší interoperabilitu:</span><span class="sxs-lookup"><span data-stu-id="79b66-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="79b66-375">R4145: Část SOAP Infoset musí obsahovat hlavičku content-transfer-encoding.</span><span class="sxs-lookup"><span data-stu-id="79b66-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="79b66-376">R4146: Pokud je kódování znaku SOAP Envelope UTF-8, hodnota hlavičky Content-Transfer-Encoding musí být 8bitová.</span><span class="sxs-lookup"><span data-stu-id="79b66-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="79b66-377">R4147: Pokud je kódování znaku SOAP Obálka UTF-16, hodnota hlavičky content-transfer-encoding musí být binární.</span><span class="sxs-lookup"><span data-stu-id="79b66-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="79b66-378">Podle [XOP] oddílu 5,</span><span class="sxs-lookup"><span data-stu-id="79b66-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="79b66-379">R4148: Část SOAP1.1 Infoset musí obsahovat hlavičku typu content-type s typem média application/xop+xml a parametry type="text/xml" a znakovou sadou.</span><span class="sxs-lookup"><span data-stu-id="79b66-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="79b66-380">R4149: Část SOAP 1.2 Infoset musí obsahovat hlavičku Typu obsahu s typem `application/xop+xml` média a parametry type="`application/soap+xml`" a `charset`.</span><span class="sxs-lookup"><span data-stu-id="79b66-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="79b66-381">Zatímco XOP definuje `charset` parametr `application/xop+xml` pro volitelné, je potřeba pro interoperabilitu podobnou požadavku BP 1.1 na `charset` parametr pro typ `text/xml` média.</span><span class="sxs-lookup"><span data-stu-id="79b66-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="79b66-382">R41410: `type` Parametry a `charset` musí být k dispozici v záhlaví typu obsahu části SOAP 1.x Infoset.</span><span class="sxs-lookup"><span data-stu-id="79b66-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="79b66-383">Podpora koncového bodu WCF pro MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="79b66-384">Účelem MTOM je zakódovat zprávu SOAP pro optimalizaci dat kódovaných base64.</span><span class="sxs-lookup"><span data-stu-id="79b66-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="79b66-385">Následuje seznam omezení:</span><span class="sxs-lookup"><span data-stu-id="79b66-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="79b66-386">R4151: Všechny položky informací o prvku, který obsahuje data kódovaná base64, mohou být optimalizovány.</span><span class="sxs-lookup"><span data-stu-id="79b66-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="79b66-387">B4152: WCF optimalizuje položky informací o elementech, které obsahují data kódovaná base64 a přesahují délku 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="79b66-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="79b66-388">Koncový bod WCF nakonfigurovaný pro použití mtom bude vždy odesílat zprávy kódované mtom.</span><span class="sxs-lookup"><span data-stu-id="79b66-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="79b66-389">I v případě, že žádné části splňují požadovaná kritéria, zpráva je stále kódována MTOM (serializována jako balíček MIME s jedním dílem MIME obsahujícím obálku SOAP).</span><span class="sxs-lookup"><span data-stu-id="79b66-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="79b66-390">WS-Policy Assertion pro MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="79b66-391">WCF používá následující kontrolní výraz zásad k označení využití mtom podle koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="79b66-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="79b66-392">R4211: Předchozí výraz zásad má předmět zásad koncového bodu a určuje, že všechny zprávy odeslané a přijaté z koncového bodu musí být optimalizovány pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="79b66-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="79b66-393">B4212: Při konfiguraci pro použití optimalizace MTOM přidá koncový bod WCF kontrolní `wsdl:binding`výraz zásad mtom k zásadám připojeným k odpovídající .</span><span class="sxs-lookup"><span data-stu-id="79b66-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="79b66-394">Složení s WS-Security</span><span class="sxs-lookup"><span data-stu-id="79b66-394">Composition with WS-Security</span></span>
<span data-ttu-id="79b66-395">MTOM je mechanismus kódování, `text/xml` který je podobný wcf binární XML.</span><span class="sxs-lookup"><span data-stu-id="79b66-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="79b66-396">MTOM nabízí přirozené složení s WS-Security a dalšíws-\* protokoly: zpráva zabezpečená pomocí WS-Security lze optimalizovat pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="79b66-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="79b66-397">Příklady</span><span class="sxs-lookup"><span data-stu-id="79b66-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="79b66-398">WCF SOAP 1.1 Zpráva kódovaná pomocí mtoma</span><span class="sxs-lookup"><span data-stu-id="79b66-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="79b66-399">WCF Secure SOAP 1.2 Zpráva kódovaná pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="79b66-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="79b66-400">V tomto příkladu je zpráva kódována pomocí mtom a SOAP 1.2, která je chráněna pomocí ws-security.</span><span class="sxs-lookup"><span data-stu-id="79b66-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="79b66-401">Binární části identifikované pro kódování jsou `BinarySecurityToken` `CipherValue` obsah `EncryptedData` , odpovídající šifrovanému podpisu a šifrovanému tělu.</span><span class="sxs-lookup"><span data-stu-id="79b66-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="79b66-402">Všimněte `CipherValue` si, `EncryptedKey` že of nebyl identifikován pro optimalizaci WCF, protože jeho délka je menší než 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="79b66-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

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
