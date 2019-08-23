---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940389"
---
# <a name="webmessageencoding"></a><span data-ttu-id="e9923-101">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="e9923-101">\<webMessageEncoding></span></span>
<span data-ttu-id="e9923-102">Povoluje čtení a zápis zpráv ve formátu prostého textu XML, JavaScript Object Notation (JSON) a "nezpracovaných" binárních obsahu při použití ve vazbě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e9923-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="e9923-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9923-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e9923-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="e9923-104">\<bindings></span></span>  
<span data-ttu-id="e9923-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e9923-105">\<customBinding></span></span>  
<span data-ttu-id="e9923-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e9923-106">\<binding></span></span>  
<span data-ttu-id="e9923-107">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="e9923-107">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9923-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9923-108">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9923-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9923-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9923-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9923-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9923-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9923-111">Attributes</span></span>  
  
|<span data-ttu-id="e9923-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e9923-112">Attribute</span></span>|<span data-ttu-id="e9923-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e9923-113">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="e9923-114">Množství zpráv, které lze číst souběžně bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="e9923-114">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="e9923-115">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="e9923-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9923-116">Výchozí hodnota je 64 čtenářů pro každý z vnitřních kodérů (text, JSON a "raw").</span><span class="sxs-lookup"><span data-stu-id="e9923-116">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="e9923-117">Zvýšením tohoto počtu se zvyšuje spotřeba paměti, ale připravuje kodér, aby dokázal řešit náhlé shluky příchozích zpráv, protože umožňuje použít čtenáře z fondu, které jsou už vytvořené, a ne vytvářet nové.</span><span class="sxs-lookup"><span data-stu-id="e9923-117">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="e9923-118">Množství zpráv, které lze odesílat souběžně bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="e9923-118">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="e9923-119">Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="e9923-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9923-120">Výchozí hodnota je 16 zapisovačů pro každý z vnitřních kodérů (text, JSON a "raw").</span><span class="sxs-lookup"><span data-stu-id="e9923-120">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="e9923-121">Zvýšením tohoto počtu se zvyšuje spotřeba paměti, ale připravuje kodér, aby dokázal řešit náhlé shluky odchozích zpráv, protože dokáže použít zapisovače z fondu, který je už vytvořený, a ne vytvářet nové.</span><span class="sxs-lookup"><span data-stu-id="e9923-121">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="e9923-122">Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="e9923-122">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e9923-123">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="e9923-123">Valid values are:</span></span><br /><br /> <span data-ttu-id="e9923-124">- UnicodeFffeTextEncoding: Kódování Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="e9923-124">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="e9923-125">- Utf16TextEncoding: Kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="e9923-125">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="e9923-126">- Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="e9923-126">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e9923-127">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="e9923-127">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="e9923-128">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e9923-128">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9923-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9923-129">Child Elements</span></span>  
  
|<span data-ttu-id="e9923-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9923-130">Element</span></span>|<span data-ttu-id="e9923-131">Popis</span><span class="sxs-lookup"><span data-stu-id="e9923-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9923-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9923-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e9923-133">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="e9923-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e9923-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e9923-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9923-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9923-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e9923-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9923-136">Element</span></span>|<span data-ttu-id="e9923-137">Popis</span><span class="sxs-lookup"><span data-stu-id="e9923-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9923-138">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="e9923-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e9923-139">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="e9923-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9923-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9923-140">Remarks</span></span>  
 <span data-ttu-id="e9923-141">Kódování je proces transformace zprávy na sekvenci bajtů.</span><span class="sxs-lookup"><span data-stu-id="e9923-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="e9923-142">Dekódování je zpětný proces.</span><span class="sxs-lookup"><span data-stu-id="e9923-142">Decoding is the reverse process.</span></span> <span data-ttu-id="e9923-143">Tyto procesy vyžadují specifikaci kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="e9923-143">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="e9923-144">`webMessageEncoding` Element funguje tak, že se přiděluje na řadu vnitřních kodérů, aby bylo možné zpracovávat kódování ve formátu XML a JSON a "nezpracované" binární data.</span><span class="sxs-lookup"><span data-stu-id="e9923-144">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="e9923-145">Toto delegování provádí složený kodér zpráv.</span><span class="sxs-lookup"><span data-stu-id="e9923-145">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="e9923-146">Tento prvek vazby a jeho složený kodér slouží k řízení kódování ve scénářích, které nepoužívají zprávy protokolu SOAP používané `webHttpBinding` prvkem.</span><span class="sxs-lookup"><span data-stu-id="e9923-146">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="e9923-147">Mezi tyto scénáře patří "obyčejné staré XML" (POX), representational state transfer (REST), Really Simple Syndication (RSS) a syndikace Atom a Asynchronous JavaScript and XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="e9923-147">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="e9923-148">Kodér kompozitní zprávy nepodporuje SOAP ani WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="e9923-148">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="e9923-149">Element Binding lze nakonfigurovat s kódováním znaků Write pomocí `writeEncoding` atributu.</span><span class="sxs-lookup"><span data-stu-id="e9923-149">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="e9923-150">Zadaná <xref:System.Text.Encoding> hodnota určuje chování při zápisu JSON a textové případy XML.</span><span class="sxs-lookup"><span data-stu-id="e9923-150">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="e9923-151">Při čtení se rozumí jakékoli platné kódování zprávy a kódování textu.</span><span class="sxs-lookup"><span data-stu-id="e9923-151">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="e9923-152">`maxReadPoolSize`a `maxWritePoolSize` lze ji také použít k nastavení maximálního počtu čtenářů a zapisovačů, které mají být přiděleny.</span><span class="sxs-lookup"><span data-stu-id="e9923-152">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="e9923-153">Ve 64 výchozím nastavení jsou přidělována čtecí zařízení a 16 zapisovače.</span><span class="sxs-lookup"><span data-stu-id="e9923-153">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="e9923-154">Výchozí omezení složitosti se také nastavují pomocí [ \<elementu readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) pro ochranu proti třídě útoků DOS (Denial of Service), které se pokoušejí složitou složitost zpráv použít k propojení prostředků zpracování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e9923-154">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9923-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9923-155">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="e9923-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9923-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="e9923-157">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="e9923-157">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e9923-158">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="e9923-158">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e9923-159">Vazby</span><span class="sxs-lookup"><span data-stu-id="e9923-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9923-160">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="e9923-160">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9923-161">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="e9923-161">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e9923-162">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e9923-162">\<customBinding></span></span>](custombinding.md)
