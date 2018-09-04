---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: e5f34dca83c8d3d08d27fb72bee5af2a89ac6b9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511911"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="42f50-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="42f50-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="42f50-103">Prvek konfigurace určuje nastavení Websocket.</span><span class="sxs-lookup"><span data-stu-id="42f50-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="42f50-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42f50-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="42f50-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="42f50-105">\<bindings></span></span>  
<span data-ttu-id="42f50-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="42f50-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f50-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42f50-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42f50-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42f50-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42f50-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42f50-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42f50-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42f50-110">Attributes</span></span>  
  
|<span data-ttu-id="42f50-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="42f50-111">Attribute</span></span>|<span data-ttu-id="42f50-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42f50-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42f50-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="42f50-113">createNotificationOnConnection</span></span>|<span data-ttu-id="42f50-114">Určuje, zda jsou oznámení odesílána při připojení.</span><span class="sxs-lookup"><span data-stu-id="42f50-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="42f50-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="42f50-115">disablePayloadMasking</span></span>|<span data-ttu-id="42f50-116">Určuje, zda je zakázaný maskování Websocket.</span><span class="sxs-lookup"><span data-stu-id="42f50-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="42f50-117">nastavení KeepAliveInterval protokolu</span><span class="sxs-lookup"><span data-stu-id="42f50-117">keepAliveInterval</span></span>|<span data-ttu-id="42f50-118">Určuje keep alive interval.</span><span class="sxs-lookup"><span data-stu-id="42f50-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="42f50-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="42f50-119">maxPendingConnections</span></span>|<span data-ttu-id="42f50-120">Určuje maximální počet připojení čeká na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="42f50-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="42f50-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="42f50-121">receiveBufferSize</span></span>|<span data-ttu-id="42f50-122">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="42f50-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="42f50-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="42f50-123">sendBufferSize</span></span>|<span data-ttu-id="42f50-124">Určuje velikost vyrovnávací paměti pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="42f50-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="42f50-125">dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="42f50-125">subProtocol</span></span>|<span data-ttu-id="42f50-126">Určuje dílčí protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="42f50-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="42f50-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="42f50-127">transportUsage</span></span>|<span data-ttu-id="42f50-128">Určuje, kdy se má použít objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="42f50-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="42f50-129">transportUsage atribut</span><span class="sxs-lookup"><span data-stu-id="42f50-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="42f50-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="42f50-130">Value</span></span>|<span data-ttu-id="42f50-131">Popis</span><span class="sxs-lookup"><span data-stu-id="42f50-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="42f50-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="42f50-132">WhenDuplex</span></span>|<span data-ttu-id="42f50-133">Protokol Websocket po duplexní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="42f50-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="42f50-134">Vždy</span><span class="sxs-lookup"><span data-stu-id="42f50-134">Always</span></span>|<span data-ttu-id="42f50-135">Vždy používejte protokol Websocket bez ohledu na to, kontrakt.</span><span class="sxs-lookup"><span data-stu-id="42f50-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="42f50-136">Nikdy</span><span class="sxs-lookup"><span data-stu-id="42f50-136">Never</span></span>|<span data-ttu-id="42f50-137">Nikdy nepoužívejte protokolu Websocket.</span><span class="sxs-lookup"><span data-stu-id="42f50-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42f50-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42f50-138">Child Elements</span></span>  
 <span data-ttu-id="42f50-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="42f50-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42f50-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42f50-140">Parent Elements</span></span>  
  
|<span data-ttu-id="42f50-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="42f50-141">Element</span></span>|<span data-ttu-id="42f50-142">Popis</span><span class="sxs-lookup"><span data-stu-id="42f50-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42f50-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="42f50-143">\<netHttpBinding></span></span>|<span data-ttu-id="42f50-144">Určuje vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="42f50-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42f50-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="42f50-145">Example</span></span>  
 <span data-ttu-id="42f50-146">Následující příklad ukazuje způsob použití \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="42f50-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42f50-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="42f50-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="42f50-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="42f50-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42f50-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="42f50-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="42f50-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="42f50-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="42f50-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="42f50-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
