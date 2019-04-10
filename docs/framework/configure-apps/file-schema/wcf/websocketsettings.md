---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226869"
---
# <a name="websocketsettings"></a><span data-ttu-id="99ef7-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="99ef7-101">\<webSocketSettings></span></span>
<span data-ttu-id="99ef7-102">Prvek konfigurace určuje nastavení Websocket.</span><span class="sxs-lookup"><span data-stu-id="99ef7-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="99ef7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99ef7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="99ef7-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="99ef7-104">\<bindings></span></span>  
<span data-ttu-id="99ef7-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="99ef7-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ef7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99ef7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99ef7-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99ef7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="99ef7-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99ef7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99ef7-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="99ef7-109">Attributes</span></span>  
  
|<span data-ttu-id="99ef7-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="99ef7-110">Attribute</span></span>|<span data-ttu-id="99ef7-111">Popis</span><span class="sxs-lookup"><span data-stu-id="99ef7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99ef7-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="99ef7-112">createNotificationOnConnection</span></span>|<span data-ttu-id="99ef7-113">Určuje, zda jsou oznámení odesílána při připojení.</span><span class="sxs-lookup"><span data-stu-id="99ef7-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="99ef7-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="99ef7-114">disablePayloadMasking</span></span>|<span data-ttu-id="99ef7-115">Určuje, zda je zakázaný maskování Websocket.</span><span class="sxs-lookup"><span data-stu-id="99ef7-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="99ef7-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="99ef7-116">keepAliveInterval</span></span>|<span data-ttu-id="99ef7-117">Určuje keep alive interval.</span><span class="sxs-lookup"><span data-stu-id="99ef7-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="99ef7-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="99ef7-118">maxPendingConnections</span></span>|<span data-ttu-id="99ef7-119">Určuje maximální počet připojení čeká na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="99ef7-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="99ef7-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="99ef7-120">receiveBufferSize</span></span>|<span data-ttu-id="99ef7-121">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="99ef7-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="99ef7-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="99ef7-122">sendBufferSize</span></span>|<span data-ttu-id="99ef7-123">Určuje velikost vyrovnávací paměti pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="99ef7-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="99ef7-124">dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="99ef7-124">subProtocol</span></span>|<span data-ttu-id="99ef7-125">Určuje dílčí protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="99ef7-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="99ef7-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="99ef7-126">transportUsage</span></span>|<span data-ttu-id="99ef7-127">Určuje, kdy se má použít objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="99ef7-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="99ef7-128">transportUsage atribut</span><span class="sxs-lookup"><span data-stu-id="99ef7-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="99ef7-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="99ef7-129">Value</span></span>|<span data-ttu-id="99ef7-130">Popis</span><span class="sxs-lookup"><span data-stu-id="99ef7-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99ef7-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="99ef7-131">WhenDuplex</span></span>|<span data-ttu-id="99ef7-132">Protokol Websocket po duplexní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="99ef7-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="99ef7-133">Vždy</span><span class="sxs-lookup"><span data-stu-id="99ef7-133">Always</span></span>|<span data-ttu-id="99ef7-134">Vždy používejte protokol Websocket bez ohledu na to, kontrakt.</span><span class="sxs-lookup"><span data-stu-id="99ef7-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="99ef7-135">Nikdy</span><span class="sxs-lookup"><span data-stu-id="99ef7-135">Never</span></span>|<span data-ttu-id="99ef7-136">Nikdy nepoužívejte protokolu Websocket.</span><span class="sxs-lookup"><span data-stu-id="99ef7-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99ef7-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99ef7-137">Child Elements</span></span>  
 <span data-ttu-id="99ef7-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="99ef7-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99ef7-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99ef7-139">Parent Elements</span></span>  
  
|<span data-ttu-id="99ef7-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="99ef7-140">Element</span></span>|<span data-ttu-id="99ef7-141">Popis</span><span class="sxs-lookup"><span data-stu-id="99ef7-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99ef7-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="99ef7-142">\<netHttpBinding></span></span>|<span data-ttu-id="99ef7-143">Určuje vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="99ef7-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99ef7-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="99ef7-144">Example</span></span>  
 <span data-ttu-id="99ef7-145">Následující příklad ukazuje způsob použití \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="99ef7-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99ef7-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99ef7-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="99ef7-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="99ef7-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="99ef7-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="99ef7-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="99ef7-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="99ef7-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="99ef7-150">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="99ef7-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
