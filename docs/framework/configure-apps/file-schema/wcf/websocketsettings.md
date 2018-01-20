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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01bc858aeeff750baa3f54e813dea5c9779143f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="8cb81-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="8cb81-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="8cb81-103">Element konfigurace slouží k zadání nastavení Websocket.</span><span class="sxs-lookup"><span data-stu-id="8cb81-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="8cb81-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cb81-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cb81-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8cb81-105">\<bindings></span></span>  
<span data-ttu-id="8cb81-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8cb81-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb81-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cb81-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cb81-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8cb81-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8cb81-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8cb81-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cb81-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8cb81-110">Attributes</span></span>  
  
|<span data-ttu-id="8cb81-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8cb81-111">Attribute</span></span>|<span data-ttu-id="8cb81-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8cb81-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cb81-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="8cb81-113">createNotificationOnConnection</span></span>|<span data-ttu-id="8cb81-114">Určuje, zda jsou oznámení odesílána při připojení.</span><span class="sxs-lookup"><span data-stu-id="8cb81-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="8cb81-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="8cb81-115">disablePayloadMasking</span></span>|<span data-ttu-id="8cb81-116">Určuje, zda je zakázána Websocket maskování.</span><span class="sxs-lookup"><span data-stu-id="8cb81-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="8cb81-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="8cb81-117">keepAliveInterval</span></span>|<span data-ttu-id="8cb81-118">Určuje interval zachovat zachování připojení.</span><span class="sxs-lookup"><span data-stu-id="8cb81-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="8cb81-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8cb81-119">maxPendingConnections</span></span>|<span data-ttu-id="8cb81-120">Určuje maximální počet připojení, které čekají na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="8cb81-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="8cb81-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="8cb81-121">receiveBufferSize</span></span>|<span data-ttu-id="8cb81-122">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="8cb81-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="8cb81-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="8cb81-123">sendBufferSize</span></span>|<span data-ttu-id="8cb81-124">Určuje velikost vyrovnávací paměti pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="8cb81-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="8cb81-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="8cb81-125">subProtocol</span></span>|<span data-ttu-id="8cb81-126">Určuje subprotocol Websocket.</span><span class="sxs-lookup"><span data-stu-id="8cb81-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="8cb81-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="8cb81-127">transportUsage</span></span>|<span data-ttu-id="8cb81-128">Určuje, kdy se mají použít objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="8cb81-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="8cb81-129">transportUsage atribut</span><span class="sxs-lookup"><span data-stu-id="8cb81-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="8cb81-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8cb81-130">Value</span></span>|<span data-ttu-id="8cb81-131">Popis</span><span class="sxs-lookup"><span data-stu-id="8cb81-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cb81-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="8cb81-132">WhenDuplex</span></span>|<span data-ttu-id="8cb81-133">Po duplexní kontrakt používejte protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="8cb81-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="8cb81-134">Vždy</span><span class="sxs-lookup"><span data-stu-id="8cb81-134">Always</span></span>|<span data-ttu-id="8cb81-135">Vždy používejte protokol Websocket bez ohledu na to, kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8cb81-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="8cb81-136">Nikdy</span><span class="sxs-lookup"><span data-stu-id="8cb81-136">Never</span></span>|<span data-ttu-id="8cb81-137">Nikdy používat protokol Websocket.</span><span class="sxs-lookup"><span data-stu-id="8cb81-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cb81-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8cb81-138">Child Elements</span></span>  
 <span data-ttu-id="8cb81-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cb81-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cb81-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cb81-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8cb81-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="8cb81-141">Element</span></span>|<span data-ttu-id="8cb81-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8cb81-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cb81-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8cb81-143">\<netHttpBinding></span></span>|<span data-ttu-id="8cb81-144">Určuje vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="8cb81-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8cb81-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cb81-145">Example</span></span>  
 <span data-ttu-id="8cb81-146">Následující příklad ukazuje, jak používat \<webSocketSettings > elementu.</span><span class="sxs-lookup"><span data-stu-id="8cb81-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8cb81-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cb81-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="8cb81-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="8cb81-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8cb81-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8cb81-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8cb81-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="8cb81-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8cb81-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="8cb81-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
