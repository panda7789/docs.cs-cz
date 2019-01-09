---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: e8b45075c7c07efc49f84526382352a5b1a556b1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148666"
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="0a898-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="0a898-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="0a898-103">Umožňuje prostého textu XML, zpráv kodovaných zápis JSON (JavaScript Object) a "neupravené" binární obsah ke čtení a zápis v vazby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0a898-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="0a898-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0a898-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0a898-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0a898-105">\<bindings></span></span>  
<span data-ttu-id="0a898-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="0a898-106">\<customBinding></span></span>  
<span data-ttu-id="0a898-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0a898-107">\<binding></span></span>  
<span data-ttu-id="0a898-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="0a898-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a898-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a898-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a898-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a898-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a898-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a898-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a898-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a898-112">Attributes</span></span>  
  
|<span data-ttu-id="0a898-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a898-113">Attribute</span></span>|<span data-ttu-id="0a898-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0a898-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="0a898-115">Počet zpráv, které lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="0a898-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="0a898-116">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="0a898-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a898-117">Výchozí hodnota je 64 čtecí zařízení pro každou z vnitřní kodérů (text JSON a "neupravené").</span><span class="sxs-lookup"><span data-stu-id="0a898-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="0a898-118">Zvýšit počet spotřeba paměti zvýší, ale připravuje kodér řešit náhlým nárůstům příchozí zprávy, protože je možné použít čtenáři z fondu, které budou vytvořeny již místo vytvoření nové.</span><span class="sxs-lookup"><span data-stu-id="0a898-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="0a898-119">Počet zpráv, které lze souběžně odesílat bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="0a898-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="0a898-120">Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu.</span><span class="sxs-lookup"><span data-stu-id="0a898-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="0a898-121">Výchozí hodnota je 16 zapisovače pro každou z vnitřní kodérů (text JSON a "neupravené").</span><span class="sxs-lookup"><span data-stu-id="0a898-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="0a898-122">Zvýšit počet spotřeba paměti zvýší, ale připravuje kodér řešit náhlým nárůstům odchozí zprávy, protože je možné použít zapisovače z fondu, které budou vytvořeny již místo vytvoření nové.</span><span class="sxs-lookup"><span data-stu-id="0a898-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="0a898-123">Určuje znakovou sadu kódování pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="0a898-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0a898-124">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0a898-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="0a898-125">-UnicodeFffeTextEncoding: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="0a898-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="0a898-126">-Utf16TextEncoding: Kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="0a898-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="0a898-127">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="0a898-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="0a898-128">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="0a898-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="0a898-129">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="0a898-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a898-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a898-130">Child Elements</span></span>  
  
|<span data-ttu-id="0a898-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a898-131">Element</span></span>|<span data-ttu-id="0a898-132">Popis</span><span class="sxs-lookup"><span data-stu-id="0a898-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a898-133">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="0a898-133">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="0a898-134">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="0a898-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0a898-135">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0a898-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a898-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a898-136">Parent Elements</span></span>  
  
|<span data-ttu-id="0a898-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a898-137">Element</span></span>|<span data-ttu-id="0a898-138">Popis</span><span class="sxs-lookup"><span data-stu-id="0a898-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a898-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0a898-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0a898-140">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="0a898-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a898-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a898-141">Remarks</span></span>  
 <span data-ttu-id="0a898-142">Kódování je proces transformace zprávu do sekvence bajtů.</span><span class="sxs-lookup"><span data-stu-id="0a898-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="0a898-143">Dekódování je opačný proces.</span><span class="sxs-lookup"><span data-stu-id="0a898-143">Decoding is the reverse process.</span></span> <span data-ttu-id="0a898-144">Tyto procesy vyžadují specifikaci kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="0a898-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="0a898-145">`webMessageEncoding` Element funguje tak, že delegováno na řadu vnitřní kodérů pro zpracování XML a JSON kódování prostého textu a "neupravené" binární data.</span><span class="sxs-lookup"><span data-stu-id="0a898-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="0a898-146">Složená zpráva Kodér provádí toto delegování.</span><span class="sxs-lookup"><span data-stu-id="0a898-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="0a898-147">Tento element vazby a jeho složené kodér se používají k řízení kódování ve scénářích, které nepoužívají používá zasílání zpráv SOAP `webHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="0a898-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="0a898-148">Mezi tyto scénáře patří "Plain Old XML" (POX), Representational State Transfer (REST), syndikace RSS (Really Simple) a Atom syndikace a asynchronní JavaScript a XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="0a898-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="0a898-149">Složená zpráva kodér nepodporuje SOAP nebo WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="0a898-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="0a898-150">Element vazby se dá nakonfigurovat s kódováním znaků zápisu s použitím `writeEncoding` atribut.</span><span class="sxs-lookup"><span data-stu-id="0a898-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="0a898-151">Zadané <xref:System.Text.Encoding> hodnota určuje chování v zápisu JSON a XML textové případů.</span><span class="sxs-lookup"><span data-stu-id="0a898-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="0a898-152">Pro čtení je srozumitelný žádné kódování zpráv a kódování textu.</span><span class="sxs-lookup"><span data-stu-id="0a898-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="0a898-153">`maxReadPoolSize` a `maxWritePoolSize` slouží také k nastavení maximálního počtu čtečky a zapisovače, které mají být přiděleny v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0a898-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="0a898-154">Ve výchozím nastavení jsou přiděleny 64 čtečky a zapisovače 16.</span><span class="sxs-lookup"><span data-stu-id="0a898-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="0a898-155">Výchozí omezení složitost jsou také nastavit pomocí [ \<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) útoků, které se pokusí použít složitosti zpráv a jejich zapojení koncového bodu zpracování elementu pro ochranu před třídy s cílem odepření služby (DOS) prostředky.</span><span class="sxs-lookup"><span data-stu-id="0a898-155">Default complexity constraints are also set using the [\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a898-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a898-156">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="0a898-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a898-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="0a898-158">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="0a898-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="0a898-159">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="0a898-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="0a898-160">Vazby</span><span class="sxs-lookup"><span data-stu-id="0a898-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0a898-161">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="0a898-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0a898-162">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0a898-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0a898-163">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="0a898-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
