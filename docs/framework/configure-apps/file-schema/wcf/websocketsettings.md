---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732551"
---
# <a name="websocketsettings"></a><span data-ttu-id="d5fed-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="d5fed-101">\<webSocketSettings></span></span>
<span data-ttu-id="d5fed-102">Prvek konfigurace, který slouží k zadání nastavení webového soketu.</span><span class="sxs-lookup"><span data-stu-id="d5fed-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="d5fed-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d5fed-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d5fed-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d5fed-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d5fed-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d5fed-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d5fed-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d5fed-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="d5fed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="d5fed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d5fed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="d5fed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fed-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5fed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5fed-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d5fed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d5fed-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d5fed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5fed-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d5fed-112">Attributes</span></span>  
  
|<span data-ttu-id="d5fed-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d5fed-113">Attribute</span></span>|<span data-ttu-id="d5fed-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d5fed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5fed-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="d5fed-115">createNotificationOnConnection</span></span>|<span data-ttu-id="d5fed-116">Určuje, zda je při připojení odesláno oznámení.</span><span class="sxs-lookup"><span data-stu-id="d5fed-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="d5fed-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="d5fed-117">disablePayloadMasking</span></span>|<span data-ttu-id="d5fed-118">Určuje, jestli je zakázané maskování webového soketu.</span><span class="sxs-lookup"><span data-stu-id="d5fed-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="d5fed-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="d5fed-119">keepAliveInterval</span></span>|<span data-ttu-id="d5fed-120">Určuje interval Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="d5fed-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="d5fed-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d5fed-121">maxPendingConnections</span></span>|<span data-ttu-id="d5fed-122">Určuje maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="d5fed-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="d5fed-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="d5fed-123">receiveBufferSize</span></span>|<span data-ttu-id="d5fed-124">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="d5fed-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="d5fed-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="d5fed-125">sendBufferSize</span></span>|<span data-ttu-id="d5fed-126">Určuje velikost vyrovnávací paměti pro odeslání.</span><span class="sxs-lookup"><span data-stu-id="d5fed-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="d5fed-127">Dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="d5fed-127">subProtocol</span></span>|<span data-ttu-id="d5fed-128">Určuje dílčí protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="d5fed-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="d5fed-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="d5fed-129">transportUsage</span></span>|<span data-ttu-id="d5fed-130">Určuje, kdy se mají používat webové sokety.</span><span class="sxs-lookup"><span data-stu-id="d5fed-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="d5fed-131">transportUsage – atribut</span><span class="sxs-lookup"><span data-stu-id="d5fed-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="d5fed-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d5fed-132">Value</span></span>|<span data-ttu-id="d5fed-133">Popis</span><span class="sxs-lookup"><span data-stu-id="d5fed-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d5fed-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="d5fed-134">WhenDuplex</span></span>|<span data-ttu-id="d5fed-135">Protokol webového soketu použijte v případě, že je kontrakt duplexní.</span><span class="sxs-lookup"><span data-stu-id="d5fed-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="d5fed-136">stál</span><span class="sxs-lookup"><span data-stu-id="d5fed-136">Always</span></span>|<span data-ttu-id="d5fed-137">Vždy používejte protokol webového soketu bez ohledu na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d5fed-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="d5fed-138">Už</span><span class="sxs-lookup"><span data-stu-id="d5fed-138">Never</span></span>|<span data-ttu-id="d5fed-139">Nikdy nepoužívejte protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="d5fed-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5fed-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d5fed-140">Child Elements</span></span>  
 <span data-ttu-id="d5fed-141">Žádné</span><span class="sxs-lookup"><span data-stu-id="d5fed-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5fed-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d5fed-142">Parent Elements</span></span>  
  
|<span data-ttu-id="d5fed-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5fed-143">Element</span></span>|<span data-ttu-id="d5fed-144">Popis</span><span class="sxs-lookup"><span data-stu-id="d5fed-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5fed-145">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d5fed-145">\<netHttpBinding></span></span>|<span data-ttu-id="d5fed-146">Určuje NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d5fed-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d5fed-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5fed-147">Example</span></span>  
 <span data-ttu-id="d5fed-148">Následující příklad ukazuje použití prvku \<webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="d5fed-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5fed-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5fed-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="d5fed-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="d5fed-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d5fed-151">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d5fed-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d5fed-152">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d5fed-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d5fed-153">vazba \<</span><span class="sxs-lookup"><span data-stu-id="d5fed-153">\<binding></span></span>](bindings.md)
