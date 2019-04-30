---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769743"
---
# <a name="websocketsettings"></a><span data-ttu-id="d1b0a-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="d1b0a-101">\<webSocketSettings></span></span>
<span data-ttu-id="d1b0a-102">Prvek konfigurace určuje nastavení Websocket.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="d1b0a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1b0a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1b0a-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d1b0a-104">\<bindings></span></span>  
<span data-ttu-id="d1b0a-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d1b0a-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b0a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1b0a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1b0a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d1b0a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1b0a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-109">Attributes</span></span>  
  
|<span data-ttu-id="d1b0a-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="d1b0a-110">Attribute</span></span>|<span data-ttu-id="d1b0a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d1b0a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1b0a-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="d1b0a-112">createNotificationOnConnection</span></span>|<span data-ttu-id="d1b0a-113">Určuje, zda jsou oznámení odesílána při připojení.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="d1b0a-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="d1b0a-114">disablePayloadMasking</span></span>|<span data-ttu-id="d1b0a-115">Určuje, zda je zakázaný maskování Websocket.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="d1b0a-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="d1b0a-116">keepAliveInterval</span></span>|<span data-ttu-id="d1b0a-117">Určuje keep alive interval.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="d1b0a-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d1b0a-118">maxPendingConnections</span></span>|<span data-ttu-id="d1b0a-119">Určuje maximální počet připojení čeká na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="d1b0a-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="d1b0a-120">receiveBufferSize</span></span>|<span data-ttu-id="d1b0a-121">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="d1b0a-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="d1b0a-122">sendBufferSize</span></span>|<span data-ttu-id="d1b0a-123">Určuje velikost vyrovnávací paměti pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="d1b0a-124">dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="d1b0a-124">subProtocol</span></span>|<span data-ttu-id="d1b0a-125">Určuje dílčí protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="d1b0a-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="d1b0a-126">transportUsage</span></span>|<span data-ttu-id="d1b0a-127">Určuje, kdy se má použít objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="d1b0a-128">transportUsage atribut</span><span class="sxs-lookup"><span data-stu-id="d1b0a-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="d1b0a-129">Value</span><span class="sxs-lookup"><span data-stu-id="d1b0a-129">Value</span></span>|<span data-ttu-id="d1b0a-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d1b0a-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d1b0a-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="d1b0a-131">WhenDuplex</span></span>|<span data-ttu-id="d1b0a-132">Protokol Websocket po duplexní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="d1b0a-133">Vždy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-133">Always</span></span>|<span data-ttu-id="d1b0a-134">Vždy používejte protokol Websocket bez ohledu na to, kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="d1b0a-135">Nikdy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-135">Never</span></span>|<span data-ttu-id="d1b0a-136">Nikdy nepoužívejte protokolu Websocket.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1b0a-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-137">Child Elements</span></span>  
 <span data-ttu-id="d1b0a-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="d1b0a-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1b0a-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1b0a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d1b0a-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1b0a-140">Element</span></span>|<span data-ttu-id="d1b0a-141">Popis</span><span class="sxs-lookup"><span data-stu-id="d1b0a-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1b0a-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d1b0a-142">\<netHttpBinding></span></span>|<span data-ttu-id="d1b0a-143">Určuje vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d1b0a-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1b0a-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1b0a-144">Example</span></span>  
 <span data-ttu-id="d1b0a-145">Následující příklad ukazuje způsob použití \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="d1b0a-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1b0a-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1b0a-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="d1b0a-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="d1b0a-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d1b0a-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d1b0a-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d1b0a-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d1b0a-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d1b0a-150">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d1b0a-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
