---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812052"
---
# <a name="messaging-protocols"></a><span data-ttu-id="dec93-102">Protokoly zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="dec93-102">Messaging Protocols</span></span>

<span data-ttu-id="dec93-103">Zásobník kanálů Windows Communication Foundation (WCF) využívá kódování a přenosové kanály k transformaci interní reprezentace zpráv do jejího formátu a jejich odeslání pomocí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="dec93-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="dec93-104">Nejběžnější přenos používaný pro interoperabilitu webových služeb je HTTP a nejběžnější kódování používané webovými službami jsou založené na jazyce XML SOAP 1,1, SOAP 1,2 a mechanizmus pro optimalizaci přenosu zpráv (MTOM).</span><span class="sxs-lookup"><span data-stu-id="dec93-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="dec93-105">Toto téma popisuje podrobnosti implementace WCF pro následující protokoly zaměstnané nástrojem <xref:System.ServiceModel.Channels.HttpTransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="dec93-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="dec93-106">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="dec93-106">Specification/document:</span></span>

- [<span data-ttu-id="dec93-107">HTTP 1,1</span><span class="sxs-lookup"><span data-stu-id="dec93-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="dec93-108">[Vazba SOAP 1,1 http](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), část 7</span><span class="sxs-lookup"><span data-stu-id="dec93-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="dec93-109">[Vazba SOAP 1,2 http](https://www.w3.org/TR/soap12-part2) Oddíl 7</span><span class="sxs-lookup"><span data-stu-id="dec93-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="dec93-110">Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívají.</span><span class="sxs-lookup"><span data-stu-id="dec93-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="dec93-111">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="dec93-111">Specification/Document:</span></span>

- [<span data-ttu-id="dec93-112">XML</span><span class="sxs-lookup"><span data-stu-id="dec93-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="dec93-113">PROTOKOL SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="dec93-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="dec93-114">Jádro protokolu SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="dec93-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="dec93-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="dec93-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="dec93-116">Webové služby W3C Addressing 1,0 – jádro</span><span class="sxs-lookup"><span data-stu-id="dec93-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="dec93-117">Webové služby W3C Addressing 1,0 – vazba SOAP</span><span class="sxs-lookup"><span data-stu-id="dec93-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="dec93-118">Webové služby W3C Addressing 1,0 – Vazba WSDL</span><span class="sxs-lookup"><span data-stu-id="dec93-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="dec93-119">Webové služby W3C Addressing 1,0 – metadata</span><span class="sxs-lookup"><span data-stu-id="dec93-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="dec93-120">Vazba WSDL SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="dec93-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="dec93-121">Vazba WSDL SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="dec93-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="dec93-122">Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které se <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> používají.</span><span class="sxs-lookup"><span data-stu-id="dec93-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="dec93-123">Specifikace/dokument:</span><span class="sxs-lookup"><span data-stu-id="dec93-123">Specification/document:</span></span>

- [<span data-ttu-id="dec93-124">XOP</span><span class="sxs-lookup"><span data-stu-id="dec93-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="dec93-125">Vazba MTOM + SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="dec93-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="dec93-126">Vazba MTOM SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="dec93-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="dec93-127">MTOM WS-Policy – kontrolní výraz</span><span class="sxs-lookup"><span data-stu-id="dec93-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="dec93-128">V rámci tohoto tématu se používají následující obory názvů XML a přidružené předpony:</span><span class="sxs-lookup"><span data-stu-id="dec93-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="dec93-129">Předpona</span><span class="sxs-lookup"><span data-stu-id="dec93-129">Prefix</span></span> | <span data-ttu-id="dec93-130">Obor názvů identifikátoru URI (Uniform Resource Identifier)</span><span class="sxs-lookup"><span data-stu-id="dec93-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="dec93-131">s11</span><span class="sxs-lookup"><span data-stu-id="dec93-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="dec93-132">S12</span><span class="sxs-lookup"><span data-stu-id="dec93-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="dec93-133">WSA</span><span class="sxs-lookup"><span data-stu-id="dec93-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="dec93-134">wsam</span><span class="sxs-lookup"><span data-stu-id="dec93-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="dec93-135">wsap</span><span class="sxs-lookup"><span data-stu-id="dec93-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="dec93-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="dec93-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="dec93-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="dec93-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="dec93-138">XOP</span><span class="sxs-lookup"><span data-stu-id="dec93-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="dec93-139">xmime</span><span class="sxs-lookup"><span data-stu-id="dec93-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="dec93-140">DP</span><span class="sxs-lookup"><span data-stu-id="dec93-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="dec93-141">SOAP 1,1 a SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="dec93-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="dec93-142">Model obálky a zpracování</span><span class="sxs-lookup"><span data-stu-id="dec93-142">Envelope and Processing Model</span></span>
<span data-ttu-id="dec93-143">WCF implementuje zpracování obálek SOAP 1,1 následující po základním profilu 1,1 (BP11) a Basic Profile 1,0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="dec93-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="dec93-144">Zpracování obálek SOAP 1,2 se implementuje po SOAP12-part1.</span><span class="sxs-lookup"><span data-stu-id="dec93-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="dec93-145">V této části jsou vysvětleny určité možnosti implementace, které služba WCF provedla v souvislosti s BP11 a SOAP12-part1.</span><span class="sxs-lookup"><span data-stu-id="dec93-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="dec93-146">Povinné zpracování hlaviček</span><span class="sxs-lookup"><span data-stu-id="dec93-146">Mandatory Header Processing</span></span>
<span data-ttu-id="dec93-147">WCF sleduje pravidla pro zpracování hlaviček označená `mustUnderstand` ve specifikacích protokolu soap 1,1 a soap 1,2 s následujícími variantami.</span><span class="sxs-lookup"><span data-stu-id="dec93-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="dec93-148">Zpráva, která vstupuje do zásobníku kanálu WCF, je zpracována jednotlivými kanály nakonfigurovanými pomocí přidružených prvků vazby, například kódování textových zpráv, zabezpečení, spolehlivého zasílání zpráv a transakcí.</span><span class="sxs-lookup"><span data-stu-id="dec93-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="dec93-149">Každý kanál rozpoznává záhlaví z přidruženého oboru názvů a označí je jako srozumitelnější.</span><span class="sxs-lookup"><span data-stu-id="dec93-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="dec93-150">Jakmile zpráva vstoupí do dispečera, formátovací modul operace čte hlavičky očekávané odpovídající kontraktem zprávy/operace a označuje jejich pochopení.</span><span class="sxs-lookup"><span data-stu-id="dec93-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="dec93-151">Potom dispečer ověří, zda nejsou žádné zbývající hlavičky srozumitelné, ale označeny jako `mustUnderstand` a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="dec93-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="dec93-152">Zprávy, které obsahují `mustUnderstand` hlavičky cílené na příjemce, nejsou zpracovávány kódem aplikace příjemce.</span><span class="sxs-lookup"><span data-stu-id="dec93-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="dec93-153">Takové vrstvené zpracování umožňuje oddělení vrstev infrastruktury a aplikačních vrstev uzlu SOAP:</span><span class="sxs-lookup"><span data-stu-id="dec93-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="dec93-154">B1111: po zpracování zprávy zásobníkem kanálu infrastruktury WCF jsou zjištěny nesrozumitelné hlavičky, ale ještě před tím, než je zpracuje aplikace</span><span class="sxs-lookup"><span data-stu-id="dec93-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="dec93-155">`mustUnderstand`Hodnota hlavičky se liší mezi SOAP 1,1 a soap 1,2.</span><span class="sxs-lookup"><span data-stu-id="dec93-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="dec93-156">Základní profil 1,1 vyžaduje, aby byla `mustUnderstand` hodnota 0 nebo 1 pro zprávy SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="dec93-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="dec93-157">Protokol SOAP 1,2 povoluje hodnoty 0, 1, `false` a `true` jako hodnoty, ale doporučuje vysílat kanonické vyjádření `xs:boolean` hodnot ( `false` , `true` ).</span><span class="sxs-lookup"><span data-stu-id="dec93-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="dec93-158">B1112: WCF generuje `mustUnderstand` hodnoty 0 a 1 pro verze soap 1,1 a soap 1,2 obálky protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="dec93-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="dec93-159">WCF akceptuje celý prostor hodnoty `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false` , `true` ).</span><span class="sxs-lookup"><span data-stu-id="dec93-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="dec93-160">Chyby protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="dec93-160">SOAP Faults</span></span>
<span data-ttu-id="dec93-161">Následuje seznam implementací selhání protokolu SOAP specifických pro WCF.</span><span class="sxs-lookup"><span data-stu-id="dec93-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="dec93-162">B2121: WCF vrátí následující kódy chyb SOAP 1,1: `s11:mustUnderstand` , `s11:Client` a `s11:Server` .</span><span class="sxs-lookup"><span data-stu-id="dec93-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="dec93-163">B2122: WCF vrátí následující kódy chyb SOAP 1,2: `s12:MustUnderstand` , `s12:Sender` a `s12:Receiver` .</span><span class="sxs-lookup"><span data-stu-id="dec93-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="dec93-164">Vazba HTTP</span><span class="sxs-lookup"><span data-stu-id="dec93-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="dec93-165">Vazba SOAP 1,1 HTTP</span><span class="sxs-lookup"><span data-stu-id="dec93-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="dec93-166">WCF implementuje vazbu protokolu HTTP protokolu SOAP 1.1 podle specifikace Basic Profile 1,1, část 3,4 s následujícími objasněmi:</span><span class="sxs-lookup"><span data-stu-id="dec93-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="dec93-167">B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="dec93-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="dec93-168">B2212: Klienti WCF podporují soubory cookie HTTP v souladu s 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="dec93-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="dec93-169">Vazba SOAP 1,2 HTTP</span><span class="sxs-lookup"><span data-stu-id="dec93-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="dec93-170">WCF implementuje vazbu HTTP protokolu SOAP 1,2, jak je popsáno ve specifikaci SOAP 1,2-Part 2 (SOAP12Part2), s následujícími objasněmi.</span><span class="sxs-lookup"><span data-stu-id="dec93-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="dec93-171">Protokol SOAP 1,2 představil pro typ média volitelný parametr Action `application/soap+xml` .</span><span class="sxs-lookup"><span data-stu-id="dec93-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="dec93-172">Tento parametr je vhodný k optimalizaci odesílání zpráv, aniž by bylo nutné, aby tělo zprávy SOAP bylo analyzováno, pokud není použito WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dec93-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="dec93-173">R2221: `application/soap+xml` parametr Action, pokud je přítomen v žádosti SOAP 1,2, musí odpovídat `soapAction` atributu v `wsoap12:operation` elementu uvnitř odpovídající vazby WSDL.</span><span class="sxs-lookup"><span data-stu-id="dec93-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="dec93-174">R2222: `application/soap+xml` parametr Action, pokud je přítomen ve zprávě SOAP 1,2, se musí shodovat, `wsa:Action` když se používají WS-addressing 2004/08 nebo WS-addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="dec93-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="dec93-175">Pokud je protokol WS-Addressing zakázán a příchozí požadavek neobsahuje parametr Action, zpráva `Action` se považuje za nespecifikovanou.</span><span class="sxs-lookup"><span data-stu-id="dec93-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="dec93-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="dec93-176">WS-Addressing</span></span>
<span data-ttu-id="dec93-177">WCF implementuje 3 verze elementu WS-Addressing:</span><span class="sxs-lookup"><span data-stu-id="dec93-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="dec93-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="dec93-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="dec93-179">Webové služby W3C Addressing 1,0 Core (ADDR10-CORE) a SOAP Binding (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="dec93-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="dec93-180">WS-Addressing 1,0 – metadata</span><span class="sxs-lookup"><span data-stu-id="dec93-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="dec93-181">Odkazy na koncový bod</span><span class="sxs-lookup"><span data-stu-id="dec93-181">Endpoint References</span></span>
<span data-ttu-id="dec93-182">Všechny verze elementu WS-Addressing, které služba WCF implementuje k popisu koncových bodů pomocí odkazů na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="dec93-183">Odkazy na koncové body a verze WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="dec93-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="dec93-184">Služba WCF implementuje řadu protokolů infrastruktury, které používají WS-Addressing, a zejména `EndpointReference` element a `W3C.WsAddressing.EndpointReferenceType` třídu (například WS-RELIABLEMESSAGING, WS-SECURECONVERSATION a WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="dec93-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="dec93-185">Služba WCF podporuje použití libovolné verze elementu WS-Addressing s dalšími protokoly infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="dec93-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="dec93-186">Koncové body WCF podporují jednu verzi elementu WS-Addressing na jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="dec93-187">V případě R3111 musí obor názvů pro `EndpointReference` element nebo typ použitý ve zprávách vyměňovaných s koncovým bodem WCF odpovídat verzi elementu WS-Addressing implementovaného tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="dec93-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="dec93-188">Například pokud koncový bod WCF implementuje WS-ReliableMessaging, `AcksTo` Hlavička vrácená tímto koncovým bodem v rámci `CreateSequenceResponse` používá verzi WS-Addressing, kterou `EncodingBinding` prvek určuje pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="dec93-189">Odkazy a metadata koncového bodu</span><span class="sxs-lookup"><span data-stu-id="dec93-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="dec93-190">Řada scénářů vyžaduje komunikaci metadat nebo odkaz na metadata pro daný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="dec93-191">B3121: WCF využívá mechanismy popsané v části specifikace WS-MetadataExchange (MEX) 6, aby zahrnovaly metadata odkazů na koncový bod podle hodnoty nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="dec93-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="dec93-192">Vezměte v úvahu scénář, ve kterém služba WCF vyžaduje ověření pomocí tokenu SAML (Security Assert Markup Language) vydaného vystavitelem tokenu na adrese `http://sts.fabrikam123.com` .</span><span class="sxs-lookup"><span data-stu-id="dec93-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="dec93-193">Koncový bod WCF popisuje tento požadavek na ověření pomocí `sp:IssuedToken` kontrolního výrazu s vnořeným `sp:Issuer` kontrolním výrazem ukazujícím na vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="dec93-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="dec93-194">Klientské aplikace, které přistupují k `sp:Issuer` kontrolnímu výrazu, musí znát, jak komunikovat s koncovým bodem vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="dec93-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="dec93-195">Klient potřebuje znát metadata vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="dec93-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="dec93-196">Pomocí rozšíření metadat odkazů na koncový bod definovaný v MEX poskytuje WCF odkaz na metadata vystavitele tokenu.</span><span class="sxs-lookup"><span data-stu-id="dec93-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

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

### <a name="message-addressing-headers"></a><span data-ttu-id="dec93-197">Hlavičky adresování zpráv</span><span class="sxs-lookup"><span data-stu-id="dec93-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="dec93-198">Záhlaví zpráv</span><span class="sxs-lookup"><span data-stu-id="dec93-198">Message Headers</span></span>
<span data-ttu-id="dec93-199">Pro verze WS-Addressing používá WCF následující záhlaví zpráv, jak jsou předepsány specifikacemi `wsa:To` , `wsa:ReplyTo` , `wsa:Action` , `wsa:MessageID` a `wsa:RelatesTo` .</span><span class="sxs-lookup"><span data-stu-id="dec93-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="dec93-200">B3211: pro všechny verze WS-Addressing se služba WCF dodrží, ale neposkytuje žádné z polí, záhlaví zpráv WS-Addressing `wsa:FaultTo` a `wsa:From` .</span><span class="sxs-lookup"><span data-stu-id="dec93-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="dec93-201">Aplikace, které komunikují s aplikacemi WCF, můžou přidat tato záhlaví zpráv a WCF je zpracovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="dec93-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="dec93-202">Referenční parametry a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dec93-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="dec93-203">WCF implementuje zpracování parametrů odkazu na koncový bod a referenční vlastnosti v souladu s příslušnými specifikacemi.</span><span class="sxs-lookup"><span data-stu-id="dec93-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="dec93-204">B3221: Pokud je nakonfigurovaná pro použití WS-Addressing 2004/08, koncové body WCF nerozlišují mezi vlastnostmi odkazu na zpracování a referenčními parametry.</span><span class="sxs-lookup"><span data-stu-id="dec93-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="dec93-205">Vzorce výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="dec93-205">Message Exchange Patterns</span></span>
<span data-ttu-id="dec93-206">Posloupnost zpráv zapojených do vyvolání operace webové služby se nazývá *vzor výměny zpráv*.</span><span class="sxs-lookup"><span data-stu-id="dec93-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="dec93-207">WCF podporuje jednosměrné, požadavek-odpověď a duplexní vzory výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="dec93-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="dec93-208">Tato část vysvětluje požadavky WS-Addressing při zpracování zpráv v závislosti na použitém vzoru výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="dec93-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="dec93-209">V celé této části žadatel pošle první zprávu a příjemce obdrží první zprávu.</span><span class="sxs-lookup"><span data-stu-id="dec93-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="dec93-210">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="dec93-210">One-Way Message</span></span>
<span data-ttu-id="dec93-211">Když je koncový bod WCF nakonfigurovaný tak, aby podporoval zprávy s daným předaným `Action` způsobem, koncový bod WCF sleduje následující chování a požadavky.</span><span class="sxs-lookup"><span data-stu-id="dec93-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="dec93-212">Pokud není uvedeno jinak, chování a pravidla se vztahují na obě verze elementu WS-Addressing podporovaných ve službě WCF:</span><span class="sxs-lookup"><span data-stu-id="dec93-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="dec93-213">R3311: Žadatel musí zahrnout `wsa:To` `wsa:Action` hlavičky, a pro všechny referenční parametry určené odkazem na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="dec93-214">Při použití specifikace WS-Addressing 2004/08 a [Reference Properties] jsou určeny odkazem koncového bodu, musí být také do zprávy přidány odpovídající hlavičky.</span><span class="sxs-lookup"><span data-stu-id="dec93-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="dec93-215">B3312: Žadatel může zahrnovat `MessageID` `ReplyTo` hlavičky, a `FaultTo` .</span><span class="sxs-lookup"><span data-stu-id="dec93-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="dec93-216">Infrastruktura přijímače je ignoruje a předává se do aplikace.</span><span class="sxs-lookup"><span data-stu-id="dec93-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="dec93-217">R3313: Pokud je použit protokol HTTP a v nožkě odpovědi HTTP není odeslána žádná zpráva, musí respondér odeslat odpověď HTTP s prázdným textem a stavovým kódem HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dec93-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="dec93-218">Je-li použit přenos HTTP a kontrakt operace deklaruje zprávu jednosměrná, může být odpověď HTTP stále používána k posílání zpráv infrastruktury, například spolehlivé zasílání zpráv může odesílat `SequenceAcknowledgement` zprávy na odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="dec93-219">B3314: respondér WCF neodesílá zprávu o chybě jako odpověď na jednosměrnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="dec93-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="dec93-220">Požadavek a odpověď</span><span class="sxs-lookup"><span data-stu-id="dec93-220">Request-Reply</span></span>
<span data-ttu-id="dec93-221">Pokud je pro zprávu s daným koncovým bodem WCF nakonfigurované pravidlo `Action` , které se řídí vzorem požadavek-odpověď, pak koncový bod WCF sleduje chování a požadavky níže.</span><span class="sxs-lookup"><span data-stu-id="dec93-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="dec93-222">Pokud není uvedeno jinak, chování a pravidla se vztahují na obě verze elementu WS-Addressing podporovaných ve službě WCF:</span><span class="sxs-lookup"><span data-stu-id="dec93-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="dec93-223">R3321: Žadatel musí zahrnout do hlaviček Request,, `wsa:To` `wsa:Action` `wsa:MessageID` a pro všechny referenční parametry nebo vlastnosti odkazu (nebo obojí) určené odkazem na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="dec93-224">R3322: při použití elementu WS-Addressing 2004/08 `ReplyTo` musí být do žádosti zahrnut i.</span><span class="sxs-lookup"><span data-stu-id="dec93-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="dec93-225">R3323: Pokud se používá specifikace WS-Addressing 1,0 a `ReplyTo` v žádosti chybí, použije se výchozí odkaz na koncový bod s vlastností [address], která se rovná `http://www.w3.org/2005/08/addressing/anonymous` .</span><span class="sxs-lookup"><span data-stu-id="dec93-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="dec93-226">R3324: Žadatel musí ve `wsa:To` `wsa:Action` `wsa:RelatesTo` zprávě odpovědi zahrnovat hlavičky, a i hlavičky všech referenčních parametrů nebo referenčních vlastností (nebo obou) určených `ReplyTo` odkazem koncového bodu v žádosti.</span><span class="sxs-lookup"><span data-stu-id="dec93-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="dec93-227">Chyby adresování webových služeb</span><span class="sxs-lookup"><span data-stu-id="dec93-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="dec93-228">R3411: WCF generuje následující chyby definované pomocí elementu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="dec93-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="dec93-229">Kód</span><span class="sxs-lookup"><span data-stu-id="dec93-229">Code</span></span> | <span data-ttu-id="dec93-230">Příčina</span><span class="sxs-lookup"><span data-stu-id="dec93-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="dec93-231">Zpráva dorazila se systémem `ReplyTo` , který se liší od adresy pro odpověď vytvořené pro tento kanál. na adrese zadané v hlavičce komu není žádný koncový bod naslouchá.</span><span class="sxs-lookup"><span data-stu-id="dec93-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="dec93-232">kanály infrastruktury nebo dispečera přidružené ke koncovému bodu nerozpoznají akci určenou v `Action` hlavičce.</span><span class="sxs-lookup"><span data-stu-id="dec93-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="dec93-233">R3412: WCF generuje následující chyby definované pomocí elementu WS-Addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="dec93-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="dec93-234">Kód</span><span class="sxs-lookup"><span data-stu-id="dec93-234">Code</span></span> | <span data-ttu-id="dec93-235">Příčina</span><span class="sxs-lookup"><span data-stu-id="dec93-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="dec93-236">Duplicitní `wsa:To` , `wsa:ReplyTo` , `wsa:From` nebo `wsa:MessageID` .</span><span class="sxs-lookup"><span data-stu-id="dec93-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="dec93-237">Duplikovat `wsa:RelatesTo` se stejným `RelationshipType` .</span><span class="sxs-lookup"><span data-stu-id="dec93-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="dec93-238">Chybí požadované záhlaví adresování.</span><span class="sxs-lookup"><span data-stu-id="dec93-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="dec93-239">Zpráva dorazila se systémem `ReplyTo` , který se liší od adresy pro odpověď vytvořené pro tento kanál.</span><span class="sxs-lookup"><span data-stu-id="dec93-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="dec93-240">Na adrese určené v hlavičce to nenaslouchá žádný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="dec93-241">Akce zadaná v hlavičce není `Action` rozpoznaná pro kanály infrastruktury ani dispečera přidružené ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="dec93-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="dec93-242">Kanál RM pošle tuto chybu zpátky, což znamená, že koncový bod nezpracuje sekvenci na základě zkoumání `CreateSequence` hlaviček adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="dec93-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="dec93-243">Kód v předchozích tabulkách je mapován na `FaultCode` v protokolu soap 1,1 a `SubCode` (s kódem = odesilatele) v protokolu SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="dec93-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="dec93-244">Vazba WSDL 1,1 a kontrolní výrazy WS-Policy</span><span class="sxs-lookup"><span data-stu-id="dec93-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="dec93-245">Označení použití elementu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="dec93-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="dec93-246">WCF používá kontrolní výrazy zásad k označení podpory koncového bodu pro konkrétní verzi WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dec93-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="dec93-247">Následující kontrolní výraz zásad má předmět zásad koncového bodu [WS-PA] a indikuje, že zprávy odeslané a přijímané z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="dec93-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="dec93-248">Tento kontrolní výraz zásady rozšiřuje specifikaci WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="dec93-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="dec93-249">Následující kontrolní výraz zásad znamená, že zprávy odeslané/přijaté musí používat WS-Addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="dec93-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="dec93-250">Následující kontrolní výraz zásad má předmět zásad koncového bodu [WS-PA] a označuje, že zprávy odesílané a přijímané z koncového bodu musí používat WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="dec93-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="dec93-251">`wsaw10:UsingAddressing`Element je vypůjčený z [WS-Addressing-WSDL] a používá se v kontextu WS-Policy, která je v souladu s touto specifikací, část 3.1.2.</span><span class="sxs-lookup"><span data-stu-id="dec93-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="dec93-252">Použití adresování nemění sémantiku vazeb protokolu HTTP v rámci WSDL 1,1, SOAP 1,1 a SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="dec93-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="dec93-253">Pokud se například očekává odpověď na požadavek, který je odeslán do koncového bodu, který používá adresování a vazby HTTP SOAP 1. x, je nutné odpověď odeslat pomocí odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="dec93-254">Pro odpovědi odeslané přes odpověď protokolu HTTP je kontrolní výraz WS-AM:</span><span class="sxs-lookup"><span data-stu-id="dec93-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="dec93-255">Výraz úplných zásad by mohl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dec93-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="dec93-256">Existují však vzory výměny zpráv, které mají výhodu ze dvou nezávislých připojení k odeslání HTTP mezi žadatelem a respondérem, například nevyžádanými jednosměrné zprávy odesílané respondérem.</span><span class="sxs-lookup"><span data-stu-id="dec93-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="dec93-257">Služba WCF nabízí funkci, kterou dva podkladové transportní kanály můžou tvořit složený duplexní kanál, ve kterém se pro vstupní zprávy používá jeden kanál a druhý se používá pro výstupní zprávy.</span><span class="sxs-lookup"><span data-stu-id="dec93-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="dec93-258">V případě přenosu protokolu HTTP poskytuje složené duplexní spojení dvě konverzace HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="dec93-259">Žadatel používá jedno připojení k posílání zpráv na respondér a partner používá druhý k posílání zpráv zpět žadateli.</span><span class="sxs-lookup"><span data-stu-id="dec93-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="dec93-260">Pro odpovědi odeslané přes samostatné požadavky HTTP je kontrolní výraz WS-am</span><span class="sxs-lookup"><span data-stu-id="dec93-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="dec93-261">Výraz úplných zásad by mohl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dec93-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="dec93-262">Použijte následující kontrolní výraz, který má předmět zásad koncového bodu [WS-PA] u koncových bodů používajících vazby WSDL 1,1 protokolu SOAP 1. x vyžaduje, aby se pro zprávy, které jsou v žadateli a respondérem na žadatele, použila dvě samostatná připojení HTTP, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dec93-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="dec93-263">Předchozí příkaz vede na následující požadavky v `wsa:ReplyTo` hlavičce pro zprávy s požadavky:</span><span class="sxs-lookup"><span data-stu-id="dec93-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="dec93-264">R3514: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností, které se nerovná, `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu k zásadě `wsap10:UsingAddressing` s `wsap:UsingAddressing` kontrolním výrazem nebo `cdp:CompositeDuplex` připojeným k němu.</span><span class="sxs-lookup"><span data-stu-id="dec93-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="dec93-265">R3515: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností Equal `http://www.w3.org/2005/08/addressing/anonymous` nebo nesmí mít vůbec `ReplyTo` hlavičku, pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu zásady s `wsap10:UsingAddressing` kontrolním výrazem a není `cdp:CompositeDuplex` připojen žádný kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="dec93-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="dec93-266">R3516: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` hlavičku s `[address]` vlastností rovnou, `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu k zásadě s `wsap:UsingAddressing` kontrolním výrazem a není `cdp:CompositeDuplex` připojen žádný kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="dec93-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="dec93-267">Specifikace WSDL WS-Addressing se pokusí popsat podobné vazby protokolu tím, že zavádí element `<wsaw:Anonymous/>` se třemi textovými hodnotami (povinné, volitelné a zakázané), které označují požadavky v `wsa:ReplyTo` hlavičce (oddíl 3,2).</span><span class="sxs-lookup"><span data-stu-id="dec93-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="dec93-268">Tato definice elementu bohužel není zvlášť použitelná jako kontrolní výraz v kontextu specifikace WS-Policy, protože vyžaduje rozšíření specifická pro doménu pro podporu průniku alternativ pomocí takového prvku jako kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="dec93-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="dec93-269">Tato definice elementu také označuje hodnotu `ReplyTo` záhlaví na rozdíl od chování koncového bodu na lince, což umožňuje přenos přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="dec93-270">Definice akce</span><span class="sxs-lookup"><span data-stu-id="dec93-270">Action Definition</span></span>
<span data-ttu-id="dec93-271">WS-Addressing 2004/08 definuje `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` prvky.</span><span class="sxs-lookup"><span data-stu-id="dec93-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="dec93-272">WS-Addressing 1,0 WSDL Binding (WS-ADDR10-WSDL) definuje podobný atribut `wsaw10:Action` .</span><span class="sxs-lookup"><span data-stu-id="dec93-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="dec93-273">Jediným rozdílem mezi těmito dvěma hodnotami je výchozí sémantika vzorců popsaná v části 3.3.2 specifikace WS-ADDR a sekce 4.4.4 elementu WS-ADDR10-WSDL, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dec93-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="dec93-274">Je vhodné mít dva koncové body, které sdílejí stejný `portType` (nebo kontrakt v terminologii WCF), ale používají různé verze elementu WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dec93-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="dec93-275">Ale vzhledem k tomu, že tato akce je definována a nesmí se `portType` měnit mezi koncovými body, které implementují `portType` , není možné podporovat jak výchozí vzor akce.</span><span class="sxs-lookup"><span data-stu-id="dec93-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="dec93-276">Pro vyřešení tohoto Controversy podporuje WCF jedinou verzi `Action` atributu.</span><span class="sxs-lookup"><span data-stu-id="dec93-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="dec93-277">B3521: WCF používá `wsaw10:Action` atribut u `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementů definovaných v WS-ADDR10-WSDL k určení `Action` identifikátoru URI pro odpovídající zprávy bez ohledu na verzi WS-Addressing, kterou používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec93-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="dec93-278">Použít odkaz na koncový bod uvnitř portu WSDL</span><span class="sxs-lookup"><span data-stu-id="dec93-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="dec93-279">WS-ADDR10-WSDL oddíl 4,1 rozšiřuje `wsdl:port` element tak, aby zahrnoval `<wsa10:EndpointReference…/>` podřízený element k popisu koncového bodu v rámci podmínek WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dec93-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="dec93-280">WCF rozšiřuje tento nástroj na WS-Addressing 2004/08, což umožňuje `<wsa:EndpointReference…/>` zobrazení jako podřízený element `wsdl:port` .</span><span class="sxs-lookup"><span data-stu-id="dec93-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="dec93-281">R3531: Pokud má koncový bod připojenou alternativu zásady s `<wsaw10:UsingAddressing/>` kontrolním výrazem zásady, odpovídající `wsdl:port` prvek může obsahovat podřízený element `<wsa10:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="dec93-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="dec93-282">R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>` , `wsa10:EndpointReference/wsa10:Address` hodnota podřízeného elementu se musí shodovat s hodnotou `@address` atributu elementu na stejné úrovni `wsdl:port` / `wsdl:location` .</span><span class="sxs-lookup"><span data-stu-id="dec93-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="dec93-283">R3533: Pokud má koncový bod připojenou alternativu zásad s `<wsap:UsingAddressing/>` kontrolním výrazem zásad, odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>` .</span><span class="sxs-lookup"><span data-stu-id="dec93-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="dec93-284">R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>` , `wsa:EndpointReference/wsa:Address` hodnota podřízeného elementu se musí shodovat s hodnotou `@address` atributu elementu na stejné úrovni `wsdl:port` / `wsdl:location` .</span><span class="sxs-lookup"><span data-stu-id="dec93-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="dec93-285">Složení pomocí WS-Security</span><span class="sxs-lookup"><span data-stu-id="dec93-285">Composition with WS-Security</span></span>
<span data-ttu-id="dec93-286">V souladu s aspekty zabezpečení v oddílech WS-ADDR a WS-ADDR10 se doporučuje podepisovat všechna záhlaví zpráv adres, aby je bylo možné propojit společně s textem zprávy.</span><span class="sxs-lookup"><span data-stu-id="dec93-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="dec93-287">Pokud se pro ochranu integrity zpráv používá protokol WS-Security, záhlaví zpráv WS-Addressing a záhlaví, které jsou výsledkem z referenčních parametrů nebo vlastností (nebo obojí), musí být podepsané spolu s textem zprávy.</span><span class="sxs-lookup"><span data-stu-id="dec93-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="dec93-288">Příklady</span><span class="sxs-lookup"><span data-stu-id="dec93-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="dec93-289">Jednosměrná zpráva</span><span class="sxs-lookup"><span data-stu-id="dec93-289">One-Way Message</span></span>
<span data-ttu-id="dec93-290">V tomto scénáři odesílatel pošle jednosměrnou zprávu příjemci.</span><span class="sxs-lookup"><span data-stu-id="dec93-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="dec93-291">Používají se protokoly SOAP 1,2, HTTP 1,1 a W3C WS-Addressing 1,0.</span><span class="sxs-lookup"><span data-stu-id="dec93-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="dec93-292">Struktura zprávy požadavku: záhlaví zpráv obsahují `wsa10:To` `wsa10:Action` prvky a.</span><span class="sxs-lookup"><span data-stu-id="dec93-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="dec93-293">Tělo zprávy obsahuje konkrétní `<app:Ping>` prvek z oboru názvů aplikace.</span><span class="sxs-lookup"><span data-stu-id="dec93-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="dec93-294">Hlavičky HTTP: cíl v příspěvku odpovídá identifikátoru URI v `wsa10:To` elementu.</span><span class="sxs-lookup"><span data-stu-id="dec93-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="dec93-295">Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1,2.</span><span class="sxs-lookup"><span data-stu-id="dec93-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="dec93-296">Parametry `charset` a `action` jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="dec93-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="dec93-297">`action`Parametr záhlaví Content-Type se shoduje s hodnotou v `wsa10:Action` záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="dec93-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```http
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

<span data-ttu-id="dec93-298">Příjemce odpoví prázdnou odpovědí HTTP a stav 202.</span><span class="sxs-lookup"><span data-stu-id="dec93-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="dec93-299">Příklad odpovědi HTTP:</span><span class="sxs-lookup"><span data-stu-id="dec93-299">An example of the HTTP response:</span></span>

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="dec93-300">Mechanismus optimalizace přenosu zpráv SOAP</span><span class="sxs-lookup"><span data-stu-id="dec93-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="dec93-301">Tato část popisuje podrobnosti implementace WCF pro HTTP SOAP pro MTOM.</span><span class="sxs-lookup"><span data-stu-id="dec93-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="dec93-302">Technologie MTOM je mechanismus kódování zpráv SOAP stejné třídy jako tradiční kódování text/XML nebo binární kódování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="dec93-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="dec93-303">MTOM zahrnuje tyto:</span><span class="sxs-lookup"><span data-stu-id="dec93-303">MTOM includes the following:</span></span>

- <span data-ttu-id="dec93-304">Mechanismus kódování a balení XML popsaný [XOP], který optimalizuje položky XML s informacemi, které obsahují binární data kódovaná pomocí Base64, do samostatných binárních částí.</span><span class="sxs-lookup"><span data-stu-id="dec93-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="dec93-305">Zapouzdření MIME balíčku XOP, který zabalí XML sadu a každou binární část balíčku XOP do samostatné části MIME</span><span class="sxs-lookup"><span data-stu-id="dec93-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="dec93-306">Kódování MIME XOP použité pro obálku SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="dec93-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="dec93-307">Vazba přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-307">An HTTP transport binding.</span></span>

<span data-ttu-id="dec93-308">U služby WCF je možné použít MTOM s přenosem jiným než HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="dec93-309">V tomto tématu se ale zaměříme na HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="dec93-310">Formát MTOM využívá velkou sadu specifikací, které se týkají samotného MTOM, XOP a MIME.</span><span class="sxs-lookup"><span data-stu-id="dec93-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="dec93-311">Modularita této sady upřesnění je trochu obtížné rekonstruovat přesné požadavky na sémantiku formátu a zpracování.</span><span class="sxs-lookup"><span data-stu-id="dec93-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="dec93-312">Tato část popisuje požadavky na formát a zpracování pro vazbu na MTOM protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="dec93-313">Kódování zprávy MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="dec93-314">Generování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-314">Generating MTOM messages</span></span>
<span data-ttu-id="dec93-315">Oddíl [XOP] 3,1 popisuje proces kódování XML s položkami informací o prvcích, které obsahují hodnoty Base64, do abstraktního definovaného balíčku XOP.</span><span class="sxs-lookup"><span data-stu-id="dec93-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="dec93-316">Následující posloupnost kroků popisuje proces kódování specifický pro MTOM:</span><span class="sxs-lookup"><span data-stu-id="dec93-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="dec93-317">Ujistěte se, že obálka protokolu SOAP, která má být zakódována, neobsahuje žádné položky informací o elementu s `[namespace name]` `http://www.w3.org/2004/08/xop/include` a `[local name]` `Include` .</span><span class="sxs-lookup"><span data-stu-id="dec93-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="dec93-318">Vytvořte prázdný balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="dec93-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="dec93-319">Identifikujte se v rámci originální sady XML – informační položky prvku, které se mají optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="dec93-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="dec93-320">Pro položky, které mají být optimalizovány, musí být znaky, které tvoří `[children]` položku informací o prvku, v kanonické formě `xs:base64Binary` (viz XSD-2, 3.2.16 kódovaná base64Binary) a nesmí obsahovat žádné prázdné znaky před, vloženou s nebo za neprázdným obsahem.</span><span class="sxs-lookup"><span data-stu-id="dec93-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="dec93-321">Vytvořte obálku XOP SOAP, která je kopií původní obálky protokolu SOAP, ale s podřízenými položkami každé položky informací o elementu identifikované v předchozím kroku nahradila `xop:Include` položka informací o elementu vytvořenou takto:</span><span class="sxs-lookup"><span data-stu-id="dec93-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="dec93-322">Převeďte nahrazené znaky na binární data jejich zpracováním jako data zakódovaná ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="dec93-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="dec93-323">Vygenerujte jedinečnou hodnotu hlavičky Content-ID, která bude vyhovovat požadavkům R3133 a R3134.</span><span class="sxs-lookup"><span data-stu-id="dec93-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="dec93-324">Vygenerujte hlavičku MIME Content-Transfer-Encoding s hodnotou Binary.</span><span class="sxs-lookup"><span data-stu-id="dec93-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="dec93-325">Pokud je položka informací o prvku optimalizovaná ([Parent] nově vložené `xop:Include` informace o elementu) `xmime:contentType` , vygeneruje hlavičku MIME Content-Type s hodnotou `xmime:contentType` atributu.</span><span class="sxs-lookup"><span data-stu-id="dec93-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="dec93-326">Vygeneruje novou binární část MIME s obsahem vytvořeným binárními daty, která byla dekódována z nahrazených znaků zpracovaných jako base64, hlavička Content-ID z 4. hlavičky Content-Transfer-Encoding z 4C, hlavička Content-Type, pokud je vygenerována v kroku 4d.</span><span class="sxs-lookup"><span data-stu-id="dec93-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="dec93-327">Přidejte `href` atribut k `xop:Include` elementu s hodnotou CID: identifikátor URI odvozený z hodnoty hlavičky Content-ID vygenerované v kroku 4b.</span><span class="sxs-lookup"><span data-stu-id="dec93-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="dec93-328">Odstraňte ohraničující " \<" and "> " znaky, adresu URL – řídicí znak zbývajícího řetězce a přidejte předponu `cid:` .</span><span class="sxs-lookup"><span data-stu-id="dec93-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="dec93-329">Následující minimální znaková sada musí být uvozena řídicími znaky RFC1738 a RFC2396.</span><span class="sxs-lookup"><span data-stu-id="dec93-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="dec93-330">Jiné znaky mohou být uvozeny řídicími znaky.</span><span class="sxs-lookup"><span data-stu-id="dec93-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="dec93-331">Vytvořte kořenovou část MIME s obálkou XOP SOAP z kroku 4.</span><span class="sxs-lookup"><span data-stu-id="dec93-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="dec93-332">Zápis hlaviček protokolu HTTP včetně záhlaví Content-Type protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="dec93-333">Zapište balíček MIME.</span><span class="sxs-lookup"><span data-stu-id="dec93-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="dec93-334">Zpracování zpráv MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-334">Processing MTOM messages</span></span>
<span data-ttu-id="dec93-335">Zpracování zprávy MTOM je přesné vrácení procesu popsaného v předchozí části "generování zpráv MTOM":</span><span class="sxs-lookup"><span data-stu-id="dec93-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="dec93-336">Ujistěte se, že kořenová část MIME má typ Content-Type `application/xop+xml` .</span><span class="sxs-lookup"><span data-stu-id="dec93-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="dec93-337">Vytvořte obálku protokolu SOAP tím, že proanalyzujete kořenovou část MIME balíčku jako dokument XML.</span><span class="sxs-lookup"><span data-stu-id="dec93-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="dec93-338">Kódování znaků je určeno `charset` parametrem Content-Type kořenové části MIME.</span><span class="sxs-lookup"><span data-stu-id="dec93-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="dec93-339">Pro každou položku informací o elementu v konstruované obálce SOAP, která má jako jediný člen své vlastnosti [children], `xop:Include` položku informací o elementu:</span><span class="sxs-lookup"><span data-stu-id="dec93-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="dec93-340">Odeberte `cid:` předponu a zrušte řídicí sekvence všech identifikátorů Escape URI (RFC 2396) v hodnotě `@href` atributu `xop:Include` elementu.</span><span class="sxs-lookup"><span data-stu-id="dec93-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="dec93-341">Vložte výsledný řetězec do řetězce " \<", "> ".</span><span class="sxs-lookup"><span data-stu-id="dec93-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="dec93-342">Vyhledejte část MIME s hodnotou hlavičky Content-ID, která odpovídá řetězci odvozenému v kroku 3a.</span><span class="sxs-lookup"><span data-stu-id="dec93-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="dec93-343">Nahraďte `xop:Include` položku informací o elementu, která se zobrazí ve `children` Vlastnosti každé položky, pomocí položek informací o znacích, které reprezentují kanonické kódování Base64 (viz XSD-2, 3.2.16 kódovaná base64Binary) těla entity části MIME identifikované v kroku 3B (efektivně nahraďte `xop:Include` položku informací o elementu daty znovu vytvořenými z části balíčku).</span><span class="sxs-lookup"><span data-stu-id="dec93-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="dec93-344">Hlavička Content-Type protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="dec93-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="dec93-345">Následuje seznam vyčiření WCF pro formát obsahu HTTP Content-Type zprávy protokolu SOAP 1. x, která je odvozena z požadavků uvedených ve specifikaci MTOM a jsou odvozena z MTOM a RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="dec93-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="dec93-346">R4131: Hlavička Content-Type protokolu HTTP musí mít hodnotu multipart/s (bez rozlišení velkých a malých písmen) a její parametry.</span><span class="sxs-lookup"><span data-stu-id="dec93-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="dec93-347">V názvech parametrů se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="dec93-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="dec93-348">Pořadí parametrů není důležité.</span><span class="sxs-lookup"><span data-stu-id="dec93-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="dec93-349">Úplný formulář Backus-Naur (BNF) záhlaví Content-Type pro zprávy MIME je uveden v dokumentu RFC 2045, Section 5,1.</span><span class="sxs-lookup"><span data-stu-id="dec93-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="dec93-350">R4132: Hlavička Content-Type protokolu HTTP musí mít parametr typu s hodnotou `application/xop+xml` uzavřenou v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="dec93-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="dec93-351">I když požadavek na použití dvojitých uvozovek není v RFC 2387 explicitní, text se bude řídit tím, že všechny parametry typu média s více částmi nebo s nimi budou pravděpodobně obsahovat rezervované znaky, jako například " \@ " nebo "/", a proto musí být dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="dec93-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="dec93-352">R4133: Hlavička Content-Type protokolu HTTP by měla mít parametr Start s hodnotou hlavičky Content-ID části MIME, která obsahuje obálku SOAP 1. x uzavřenou do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="dec93-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="dec93-353">Pokud je parametr Start vynechán, první část MIME musí obsahovat obálku SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="dec93-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="dec93-354">R4134: Hlavička Content-Type protokolu HTTP pro zprávu kódovaná v protokolu SOAP 1,1 musí zahrnovat parametr start-info s hodnotou text/XML uzavřenou do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="dec93-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="dec93-355">R4135: Hlavička Content-Type protokolu HTTP pro zprávu kódovaná pomocí protokolu SOAP 1,2 musí zahrnovat parametr start-info s hodnotou `application/soap+xml` uzavřenou do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="dec93-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="dec93-356">R4136: Hlavička Content-Type protokolu HTTP pro zprávu s protokolem SOAP 1. x MTOM musí mít parametr hranice s hodnotou (uzavřenou do dvojitých uvozovek), která odpovídá BNF hranice MIME definované v dokumentu RFC 2046, oddíl 5.1.1.</span><span class="sxs-lookup"><span data-stu-id="dec93-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="dec93-357">Příklady:</span><span class="sxs-lookup"><span data-stu-id="dec93-357">Examples:</span></span>

     <span data-ttu-id="dec93-358">ODSTRANĚNÍ</span><span class="sxs-lookup"><span data-stu-id="dec93-358">CORRECT</span></span>

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="dec93-359">ODSTRANĚNÍ</span><span class="sxs-lookup"><span data-stu-id="dec93-359">CORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="dec93-360">ŠPATNÝ</span><span class="sxs-lookup"><span data-stu-id="dec93-360">INCORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="dec93-361">Součást MIME informačního dílu</span><span class="sxs-lookup"><span data-stu-id="dec93-361">Infoset MIME Part</span></span>
<span data-ttu-id="dec93-362">Obálka SOAP 1. x je zapouzdřená jako kořenová součást balíčku XOP MIME a často se nazývá `infoset` součást.</span><span class="sxs-lookup"><span data-stu-id="dec93-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="dec93-363">R4141: obálka SOAP 1. x musí být zapouzdřena jako kořenová část balíčku rozhraní XOP MIME, která se nazývá `infoset` součást a odkazuje na typ obsahu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dec93-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="dec93-364">R4142: část SOAP `Infoset` musí zahrnovat následující záhlaví MIME: `Content-ID` , `Content-Transfer-Encoding` a `Content-Type` .</span><span class="sxs-lookup"><span data-stu-id="dec93-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="dec93-365">Formát záhlaví Content-ID je definován v dokumentu RFC 2045 jako</span><span class="sxs-lookup"><span data-stu-id="dec93-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="dec93-366">kde `msg-id` je definován v dokumentu rfc 2822 (který nahrazuje specifikaci rfc 822, na kterou odkazuje rfc 2045) jako:</span><span class="sxs-lookup"><span data-stu-id="dec93-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="dec93-367">a je to efektivně e-mailová adresa uzavřená v rámci " \<" and  "> ".</span><span class="sxs-lookup"><span data-stu-id="dec93-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="dec93-368">`[CFWS]`Předpona a přípona byla přidána do RFC 2822, aby mohla přenášet komentáře a neměla by se používat k zachování interoperability.</span><span class="sxs-lookup"><span data-stu-id="dec93-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="dec93-369">R4143: hodnota hlavičky Content-ID pro součást MIME pro informační sadu musí splňovat `msg-id` produkci z dokumentu RFC 2822 s `[CFWS]` vynechánými částmi předpony a příponami.</span><span class="sxs-lookup"><span data-stu-id="dec93-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="dec93-370">Určitý počet implementací MIME má za následek, že pro hodnotu uzavřenou v rámci " \<" and "> " má být e-mailová adresa, která se používá `absoluteURI` \<" , "> společně s e-mailovou adresou.</span><span class="sxs-lookup"><span data-stu-id="dec93-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="dec93-371">Tato verze WCF používá hodnoty záhlaví MIME Content-ID ve formátu:</span><span class="sxs-lookup"><span data-stu-id="dec93-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="dec93-372">R4144: procesory MTOM by měly přijmout hodnoty hlaviček Content-ID, které odpovídají následujícímu uvolněnému `msg-id` .</span><span class="sxs-lookup"><span data-stu-id="dec93-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="dec93-373">MIME (RFC 2045) poskytuje hlavičku Content-Transfer-Encoding pro komunikaci s kódováním obsahu části MIME.</span><span class="sxs-lookup"><span data-stu-id="dec93-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="dec93-374">Výchozí hodnota definovaná pro kódování Content-Transfer-Encoding je 7 bitů, což není vhodné pro většinu zpráv SOAP, takže hlavička Content-Transfer-Encoding je nutná pro lepší interoperabilitu:</span><span class="sxs-lookup"><span data-stu-id="dec93-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="dec93-375">R4145: část informačního doplňku SOAP musí obsahovat hlavičku Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="dec93-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="dec93-376">R4146: Pokud kódování znaků obálky protokolu SOAP je UTF-8, hodnota hlavičky Content-Transfer-Encoding musí být 8 bitů.</span><span class="sxs-lookup"><span data-stu-id="dec93-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="dec93-377">R4147: Pokud je kódování znaků obálky protokolu SOAP UTF-16, hodnota hlavičky Content-Transfer-Encoding musí být binární.</span><span class="sxs-lookup"><span data-stu-id="dec93-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="dec93-378">Podle [XOP] sekce 5,</span><span class="sxs-lookup"><span data-stu-id="dec93-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="dec93-379">R4148: část s informačními zprávami SOAP 1.1 musí obsahovat hlavičku Content-Type s typem média Application/XOP + XML a Parameters Type = "text/XML" a charset</span><span class="sxs-lookup"><span data-stu-id="dec93-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="dec93-380">R4149: část s obsahem součásti SOAP 1,2 musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry Type = " `application/soap+xml` " a `charset` .</span><span class="sxs-lookup"><span data-stu-id="dec93-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="dec93-381">A když XOP definuje `charset` parametr pro `application/xop+xml` , aby byl volitelný, je potřeba pro interoperabilitu podobnou požadavku BP 1,1 u `charset` parametru pro `text/xml` typ média.</span><span class="sxs-lookup"><span data-stu-id="dec93-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="dec93-382">R41410: `type` parametry a se musí nacházet `charset` v hlavičce Content-Type součásti sady ODHLAŠOVÁNÍ protokolu SOAP 1. x.</span><span class="sxs-lookup"><span data-stu-id="dec93-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="dec93-383">Podpora koncových bodů WCF pro MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="dec93-384">Účelem MTOM je zakódovat zprávu SOAP pro optimalizaci dat kódovaných v kódování Base64.</span><span class="sxs-lookup"><span data-stu-id="dec93-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="dec93-385">Níže je seznam omezení:</span><span class="sxs-lookup"><span data-stu-id="dec93-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="dec93-386">R4151: je možné optimalizovat všechny informace o elementu, které obsahují data kódovaná pomocí Base64.</span><span class="sxs-lookup"><span data-stu-id="dec93-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="dec93-387">B4152: WCF optimalizuje položky informací o elementu, které obsahují data kódovaná pomocí Base64, a překračují 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="dec93-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="dec93-388">Koncový bod WCF nakonfigurovaný k použití MTOM bude vždycky odesílat zprávy kódované v rámci MTOM.</span><span class="sxs-lookup"><span data-stu-id="dec93-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="dec93-389">I když žádné části nesplňují požadovaná kritéria, zpráva je stále v kódování MTOM (serializovaná jako balíček MIME s jednou částí MIME obsahující obálku protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="dec93-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="dec93-390">Kontrolní výraz WS-Policy pro MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="dec93-391">Služba WCF používá následující kontrolní výraz zásad pro indikaci využití MTOM Endpoint:</span><span class="sxs-lookup"><span data-stu-id="dec93-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="dec93-392">R4211: kontrolní výraz předchozí zásady má předmět zásad koncového bodu, který určuje, že všechny zprávy odeslané do a přijaté z koncového bodu musí být optimalizované pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="dec93-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="dec93-393">B4212: Pokud je nakonfigurované použití optimalizace MTOM, koncový bod WCF přidá do zásady připojené k odpovídajícímu výrazu zásadu MTOM `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="dec93-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="dec93-394">Složení pomocí WS-Security</span><span class="sxs-lookup"><span data-stu-id="dec93-394">Composition with WS-Security</span></span>
<span data-ttu-id="dec93-395">MTOM je kódovací mechanismus, který se podobá `text/xml` a binární XML služby WCF.</span><span class="sxs-lookup"><span data-stu-id="dec93-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="dec93-396">MTOM nabízí přirozené složení pomocí WS-Security a dalších protokolů WS-\*: zpráva zabezpečená pomocí WS-Security se dá optimalizovat pomocí MTOM.</span><span class="sxs-lookup"><span data-stu-id="dec93-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="dec93-397">Příklady</span><span class="sxs-lookup"><span data-stu-id="dec93-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="dec93-398">Zpráva WCF SOAP 1,1 zakódovaná pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```http
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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="dec93-399">Zabezpečená zpráva SOAP 1,2 WCF kódovaná pomocí MTOM</span><span class="sxs-lookup"><span data-stu-id="dec93-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="dec93-400">V tomto příkladu je zpráva kódovaná pomocí MTOM a protokolu SOAP 1,2, který je chráněný pomocí WS-Security.</span><span class="sxs-lookup"><span data-stu-id="dec93-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="dec93-401">Binární části identifikované pro kódování jsou obsahem `BinarySecurityToken` , který `CipherValue` `EncryptedData` odpovídá zašifrovanému podpisu a šifrovanému textu.</span><span class="sxs-lookup"><span data-stu-id="dec93-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="dec93-402">Všimněte si, že `CipherValue` `EncryptedKey` služba nebyla identifikována pro optimalizaci pomocí služby WCF, protože její délka je menší než 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="dec93-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```http
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
