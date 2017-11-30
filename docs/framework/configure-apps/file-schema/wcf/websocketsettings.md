---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2714b27916a47ae8e002ea857c93377736c4eff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="6a7ee-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="6a7ee-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="6a7ee-103">Element konfigurace slouží k zadání nastavení Websocket.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="6a7ee-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6a7ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a7ee-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6a7ee-105">\<bindings></span></span>  
<span data-ttu-id="6a7ee-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6a7ee-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7ee-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a7ee-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a7ee-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6a7ee-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a7ee-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-110">Attributes</span></span>  
  
|<span data-ttu-id="6a7ee-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6a7ee-111">Attribute</span></span>|<span data-ttu-id="6a7ee-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6a7ee-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a7ee-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="6a7ee-113">createNotificationOnConnection</span></span>|<span data-ttu-id="6a7ee-114">Určuje, zda jsou oznámení odesílána při připojení.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="6a7ee-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="6a7ee-115">disablePayloadMasking</span></span>|<span data-ttu-id="6a7ee-116">Určuje, zda je zakázána Websocket maskování.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="6a7ee-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="6a7ee-117">keepAliveInterval</span></span>|<span data-ttu-id="6a7ee-118">Určuje interval zachovat zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="6a7ee-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="6a7ee-119">maxPendingConnections</span></span>|<span data-ttu-id="6a7ee-120">Určuje maximální počet připojení, které čekají na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="6a7ee-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6a7ee-121">receiveBufferSize</span></span>|<span data-ttu-id="6a7ee-122">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="6a7ee-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="6a7ee-123">sendBufferSize</span></span>|<span data-ttu-id="6a7ee-124">Určuje velikost vyrovnávací paměti pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="6a7ee-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="6a7ee-125">subProtocol</span></span>|<span data-ttu-id="6a7ee-126">Určuje subprotocol Websocket.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="6a7ee-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="6a7ee-127">transportUsage</span></span>|<span data-ttu-id="6a7ee-128">Určuje, kdy se mají použít objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="6a7ee-129">transportUsage atribut</span><span class="sxs-lookup"><span data-stu-id="6a7ee-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="6a7ee-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a7ee-130">Value</span></span>|<span data-ttu-id="6a7ee-131">Popis</span><span class="sxs-lookup"><span data-stu-id="6a7ee-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6a7ee-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="6a7ee-132">WhenDuplex</span></span>|<span data-ttu-id="6a7ee-133">Po duplexní kontrakt používejte protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="6a7ee-134">Vždy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-134">Always</span></span>|<span data-ttu-id="6a7ee-135">Vždy používejte protokol Websocket bez ohledu na to, kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="6a7ee-136">Nikdy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-136">Never</span></span>|<span data-ttu-id="6a7ee-137">Nikdy používat protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a7ee-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-138">Child Elements</span></span>  
 <span data-ttu-id="6a7ee-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="6a7ee-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a7ee-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a7ee-140">Parent Elements</span></span>  
  
|<span data-ttu-id="6a7ee-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a7ee-141">Element</span></span>|<span data-ttu-id="6a7ee-142">Popis</span><span class="sxs-lookup"><span data-stu-id="6a7ee-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a7ee-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6a7ee-143">\<netHttpBinding></span></span>|<span data-ttu-id="6a7ee-144">Určuje vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6a7ee-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a7ee-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a7ee-145">Example</span></span>  
 <span data-ttu-id="6a7ee-146">Následující příklad ukazuje, jak používat \<webSocketSettings > elementu.</span><span class="sxs-lookup"><span data-stu-id="6a7ee-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a7ee-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a7ee-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="6a7ee-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="6a7ee-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6a7ee-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6a7ee-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6a7ee-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="6a7ee-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6a7ee-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="6a7ee-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
