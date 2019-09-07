---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399136"
---
# <a name="websocketsettings"></a><span data-ttu-id="c5bc2-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="c5bc2-101">\<webSocketSettings></span></span>
<span data-ttu-id="c5bc2-102">Prvek konfigurace, který slouží k zadání nastavení webového soketu.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="c5bc2-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5bc2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5bc2-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c5bc2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c5bc2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c5bc2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c5bc2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c5bc2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="c5bc2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="c5bc2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c5bc2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="c5bc2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bc2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5bc2-109">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5bc2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5bc2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5bc2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-112">Attributes</span></span>  
  
|<span data-ttu-id="c5bc2-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c5bc2-113">Attribute</span></span>|<span data-ttu-id="c5bc2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c5bc2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5bc2-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="c5bc2-115">createNotificationOnConnection</span></span>|<span data-ttu-id="c5bc2-116">Určuje, zda je při připojení odesláno oznámení.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="c5bc2-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="c5bc2-117">disablePayloadMasking</span></span>|<span data-ttu-id="c5bc2-118">Určuje, jestli je zakázané maskování webového soketu.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="c5bc2-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="c5bc2-119">keepAliveInterval</span></span>|<span data-ttu-id="c5bc2-120">Určuje interval Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="c5bc2-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c5bc2-121">maxPendingConnections</span></span>|<span data-ttu-id="c5bc2-122">Určuje maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c5bc2-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="c5bc2-123">receiveBufferSize</span></span>|<span data-ttu-id="c5bc2-124">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="c5bc2-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="c5bc2-125">sendBufferSize</span></span>|<span data-ttu-id="c5bc2-126">Určuje velikost vyrovnávací paměti pro odeslání.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="c5bc2-127">Dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="c5bc2-127">subProtocol</span></span>|<span data-ttu-id="c5bc2-128">Určuje dílčí protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="c5bc2-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="c5bc2-129">transportUsage</span></span>|<span data-ttu-id="c5bc2-130">Určuje, kdy se mají používat webové sokety.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="c5bc2-131">transportUsage – atribut</span><span class="sxs-lookup"><span data-stu-id="c5bc2-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="c5bc2-132">Value</span><span class="sxs-lookup"><span data-stu-id="c5bc2-132">Value</span></span>|<span data-ttu-id="c5bc2-133">Popis</span><span class="sxs-lookup"><span data-stu-id="c5bc2-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5bc2-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="c5bc2-134">WhenDuplex</span></span>|<span data-ttu-id="c5bc2-135">Protokol webového soketu použijte v případě, že je kontrakt duplexní.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="c5bc2-136">Vždy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-136">Always</span></span>|<span data-ttu-id="c5bc2-137">Vždy používejte protokol webového soketu bez ohledu na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="c5bc2-138">Nikdy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-138">Never</span></span>|<span data-ttu-id="c5bc2-139">Nikdy nepoužívejte protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5bc2-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-140">Child Elements</span></span>  
 <span data-ttu-id="c5bc2-141">Žádné</span><span class="sxs-lookup"><span data-stu-id="c5bc2-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5bc2-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5bc2-142">Parent Elements</span></span>  
  
|<span data-ttu-id="c5bc2-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5bc2-143">Element</span></span>|<span data-ttu-id="c5bc2-144">Popis</span><span class="sxs-lookup"><span data-stu-id="c5bc2-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5bc2-145">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c5bc2-145">\<netHttpBinding></span></span>|<span data-ttu-id="c5bc2-146">Určuje NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c5bc2-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5bc2-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5bc2-147">Example</span></span>  
 <span data-ttu-id="c5bc2-148">Následující příklad ukazuje použití \<prvku webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="c5bc2-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="c5bc2-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5bc2-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="c5bc2-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="c5bc2-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c5bc2-151">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c5bc2-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c5bc2-152">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c5bc2-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c5bc2-153">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c5bc2-153">\<binding></span></span>](../../../misc/binding.md)
