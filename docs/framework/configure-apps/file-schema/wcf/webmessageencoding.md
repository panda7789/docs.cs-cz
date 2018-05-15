---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: fc1f83128dacb588d8179dea95c132da1ab2be91
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="7c712-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="7c712-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="7c712-103">Umožňuje prostého textu XML, kódování zpráv JavaScript Object Notation (JSON) a "nezpracovaných" binární obsah čtení a zápis při použití ve vazbě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7c712-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="7c712-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c712-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7c712-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7c712-105">\<bindings></span></span>  
<span data-ttu-id="7c712-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7c712-106">\<customBinding></span></span>  
<span data-ttu-id="7c712-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="7c712-107">\<binding></span></span>  
<span data-ttu-id="7c712-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="7c712-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c712-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c712-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c712-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c712-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c712-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c712-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c712-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c712-112">Attributes</span></span>  
  
|<span data-ttu-id="7c712-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7c712-113">Attribute</span></span>|<span data-ttu-id="7c712-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7c712-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="7c712-115">Velikost zprávy, které lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="7c712-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="7c712-116">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="7c712-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7c712-117">Výchozí hodnota je 64 čtečky pro každou z vnitřní kodéry (text, JSON a "nezpracovaných").</span><span class="sxs-lookup"><span data-stu-id="7c712-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="7c712-118">Zvýšit číslo spotřeba paměti zvýší, ale připraví kodér jak nakládat s nečekané shluky příchozí zprávy, protože je možné používat čtečky z fondu, které jsou již vytvořeny místo vytvoření nové.</span><span class="sxs-lookup"><span data-stu-id="7c712-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="7c712-119">Velikost zprávy, které lze najednou odeslat bez přidělení nového zapisovače.</span><span class="sxs-lookup"><span data-stu-id="7c712-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="7c712-120">Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady.</span><span class="sxs-lookup"><span data-stu-id="7c712-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7c712-121">Výchozí hodnota je 16 zapisovače pro každou z vnitřní kodéry (text, JSON a "nezpracovaných").</span><span class="sxs-lookup"><span data-stu-id="7c712-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="7c712-122">Zvýšit číslo spotřeba paměti zvýší, ale připraví kodér jak nakládat s nečekané shluky odchozích zpráv, protože je možné použít zapisovače z fondu, které jsou již vytvořeny místo vytvoření nové.</span><span class="sxs-lookup"><span data-stu-id="7c712-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="7c712-123">Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby.</span><span class="sxs-lookup"><span data-stu-id="7c712-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7c712-124">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="7c712-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="7c712-125">-UnicodeFffeTextEncoding: Big Endian kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="7c712-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="7c712-126">-Utf16TextEncoding: Kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="7c712-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="7c712-127">-Utf8TextEncoding: 8bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="7c712-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="7c712-128">Výchozí hodnota je Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="7c712-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="7c712-129">Tento atribut je typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7c712-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c712-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c712-130">Child Elements</span></span>  
  
|<span data-ttu-id="7c712-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c712-131">Element</span></span>|<span data-ttu-id="7c712-132">Popis</span><span class="sxs-lookup"><span data-stu-id="7c712-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c712-133">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="7c712-133">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7c712-134">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7c712-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7c712-135">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7c712-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c712-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c712-136">Parent Elements</span></span>  
  
|<span data-ttu-id="7c712-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c712-137">Element</span></span>|<span data-ttu-id="7c712-138">Popis</span><span class="sxs-lookup"><span data-stu-id="7c712-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c712-139">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="7c712-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7c712-140">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7c712-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c712-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c712-141">Remarks</span></span>  
 <span data-ttu-id="7c712-142">Proces transformace zprávu do pořadí bajtů kódování je.</span><span class="sxs-lookup"><span data-stu-id="7c712-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="7c712-143">Dekódování je zpětné proces.</span><span class="sxs-lookup"><span data-stu-id="7c712-143">Decoding is the reverse process.</span></span> <span data-ttu-id="7c712-144">Tyto procesy vyžadují specifikaci kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="7c712-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="7c712-145">`webMessageEncoding` Element funguje tak, že delegování na řadu vnitřní kodéry pro zpracování formátu prostého textu XML a JSON kódování a "nezpracovaná" binární data.</span><span class="sxs-lookup"><span data-stu-id="7c712-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="7c712-146">Toto delegování je potřeba kodéru složené zprávy.</span><span class="sxs-lookup"><span data-stu-id="7c712-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="7c712-147">Tento element vazby a jeho složené kodér slouží k řízení kódování ve scénářích, které nepoužívají SOAP zasílání zpráv používané `webHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="7c712-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="7c712-148">Mezi tyto scénáře patří "Prostý formát XML" (POX), přenos REST (Representational State), skutečně jednoduché syndikace (RSS) a Atom syndikace a asynchronní JavaScript a XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="7c712-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="7c712-149">Kodér složené zpráv nepodporuje SOAP nebo WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="7c712-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="7c712-150">Můžete nakonfigurovat prvku vazby kódování znaků zápis pomocí `writeEncoding` atribut.</span><span class="sxs-lookup"><span data-stu-id="7c712-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="7c712-151">Zadaných <xref:System.Text.Encoding> hodnota určuje chování v zápisu JSON a XML textovou případech.</span><span class="sxs-lookup"><span data-stu-id="7c712-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="7c712-152">Na čtení se rozumí všechny platné zprávy kódování a kódování textu.</span><span class="sxs-lookup"><span data-stu-id="7c712-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="7c712-153">`maxReadPoolSize` a `maxWritePoolSize` lze také nastavit maximální počet čtení a zápis, která bude přidělena v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7c712-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="7c712-154">Ve výchozím nastavení jsou přiděleny 64 čtení a zápis 16.</span><span class="sxs-lookup"><span data-stu-id="7c712-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="7c712-155">Výchozí omezení složitost jsou nastaveny také, pomocí [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elementu, který chcete chránit proti třídu odepření služby (DOS) před útoky tento pokus pomocí zpráv složitost vytížit zpracování koncového bodu prostředky.</span><span class="sxs-lookup"><span data-stu-id="7c712-155">Default complexity constraints are also set using the [\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c712-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c712-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c712-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c712-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="7c712-158">Kódování zpráv</span><span class="sxs-lookup"><span data-stu-id="7c712-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="7c712-159">Výběr kodéru zprávy</span><span class="sxs-lookup"><span data-stu-id="7c712-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="7c712-160">Vazby</span><span class="sxs-lookup"><span data-stu-id="7c712-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7c712-161">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7c712-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7c712-162">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7c712-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7c712-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7c712-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
