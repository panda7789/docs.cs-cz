---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940318"
---
# <a name="websocketsettings"></a><span data-ttu-id="db560-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="db560-101">\<webSocketSettings></span></span>
<span data-ttu-id="db560-102">Prvek konfigurace, který slouží k zadání nastavení webového soketu.</span><span class="sxs-lookup"><span data-stu-id="db560-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="db560-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db560-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="db560-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="db560-104">\<bindings></span></span>  
<span data-ttu-id="db560-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="db560-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db560-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db560-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db560-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db560-107">Attributes and Elements</span></span>  
 <span data-ttu-id="db560-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db560-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db560-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="db560-109">Attributes</span></span>  
  
|<span data-ttu-id="db560-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="db560-110">Attribute</span></span>|<span data-ttu-id="db560-111">Popis</span><span class="sxs-lookup"><span data-stu-id="db560-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db560-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="db560-112">createNotificationOnConnection</span></span>|<span data-ttu-id="db560-113">Určuje, zda je při připojení odesláno oznámení.</span><span class="sxs-lookup"><span data-stu-id="db560-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="db560-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="db560-114">disablePayloadMasking</span></span>|<span data-ttu-id="db560-115">Určuje, jestli je zakázané maskování webového soketu.</span><span class="sxs-lookup"><span data-stu-id="db560-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="db560-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="db560-116">keepAliveInterval</span></span>|<span data-ttu-id="db560-117">Určuje interval Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="db560-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="db560-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="db560-118">maxPendingConnections</span></span>|<span data-ttu-id="db560-119">Určuje maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="db560-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="db560-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="db560-120">receiveBufferSize</span></span>|<span data-ttu-id="db560-121">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="db560-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="db560-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="db560-122">sendBufferSize</span></span>|<span data-ttu-id="db560-123">Určuje velikost vyrovnávací paměti pro odeslání.</span><span class="sxs-lookup"><span data-stu-id="db560-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="db560-124">Dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="db560-124">subProtocol</span></span>|<span data-ttu-id="db560-125">Určuje dílčí protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="db560-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="db560-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="db560-126">transportUsage</span></span>|<span data-ttu-id="db560-127">Určuje, kdy se mají používat webové sokety.</span><span class="sxs-lookup"><span data-stu-id="db560-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="db560-128">transportUsage – atribut</span><span class="sxs-lookup"><span data-stu-id="db560-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="db560-129">Value</span><span class="sxs-lookup"><span data-stu-id="db560-129">Value</span></span>|<span data-ttu-id="db560-130">Popis</span><span class="sxs-lookup"><span data-stu-id="db560-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db560-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="db560-131">WhenDuplex</span></span>|<span data-ttu-id="db560-132">Protokol webového soketu použijte v případě, že je kontrakt duplexní.</span><span class="sxs-lookup"><span data-stu-id="db560-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="db560-133">Vždy</span><span class="sxs-lookup"><span data-stu-id="db560-133">Always</span></span>|<span data-ttu-id="db560-134">Vždy používejte protokol webového soketu bez ohledu na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="db560-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="db560-135">Nikdy</span><span class="sxs-lookup"><span data-stu-id="db560-135">Never</span></span>|<span data-ttu-id="db560-136">Nikdy nepoužívejte protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="db560-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db560-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db560-137">Child Elements</span></span>  
 <span data-ttu-id="db560-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="db560-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db560-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db560-139">Parent Elements</span></span>  
  
|<span data-ttu-id="db560-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="db560-140">Element</span></span>|<span data-ttu-id="db560-141">Popis</span><span class="sxs-lookup"><span data-stu-id="db560-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db560-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="db560-142">\<netHttpBinding></span></span>|<span data-ttu-id="db560-143">Určuje NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="db560-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db560-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="db560-144">Example</span></span>  
 <span data-ttu-id="db560-145">Následující příklad ukazuje použití \<prvku webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="db560-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db560-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db560-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="db560-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="db560-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="db560-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="db560-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="db560-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="db560-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="db560-150">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="db560-150">\<binding></span></span>](../../../misc/binding.md)
