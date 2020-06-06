---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732551"
---
# \<webSocketSettings>
<span data-ttu-id="9f8b4-101">Prvek konfigurace, který slouží k zadání nastavení webového soketu.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9f8b4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f8b4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f8b4-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9f8b4-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f8b4-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-105">Attributes</span></span>  
  
|<span data-ttu-id="9f8b4-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f8b4-106">Attribute</span></span>|<span data-ttu-id="9f8b4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9f8b4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f8b4-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="9f8b4-108">createNotificationOnConnection</span></span>|<span data-ttu-id="9f8b4-109">Určuje, zda je při připojení odesláno oznámení.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="9f8b4-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="9f8b4-110">disablePayloadMasking</span></span>|<span data-ttu-id="9f8b4-111">Určuje, jestli je zakázané maskování webového soketu.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="9f8b4-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="9f8b4-112">keepAliveInterval</span></span>|<span data-ttu-id="9f8b4-113">Určuje interval Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="9f8b4-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="9f8b4-114">maxPendingConnections</span></span>|<span data-ttu-id="9f8b4-115">Určuje maximální počet připojení čekajících na odeslání ve službě.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="9f8b4-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="9f8b4-116">receiveBufferSize</span></span>|<span data-ttu-id="9f8b4-117">Určuje velikost vyrovnávací paměti pro příjem.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="9f8b4-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="9f8b4-118">sendBufferSize</span></span>|<span data-ttu-id="9f8b4-119">Určuje velikost vyrovnávací paměti pro odeslání.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="9f8b4-120">Dílčí protokol</span><span class="sxs-lookup"><span data-stu-id="9f8b4-120">subProtocol</span></span>|<span data-ttu-id="9f8b4-121">Určuje dílčí protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="9f8b4-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="9f8b4-122">transportUsage</span></span>|<span data-ttu-id="9f8b4-123">Určuje, kdy se mají používat webové sokety.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="9f8b4-124">transportUsage – atribut</span><span class="sxs-lookup"><span data-stu-id="9f8b4-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="9f8b4-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f8b4-125">Value</span></span>|<span data-ttu-id="9f8b4-126">Description</span><span class="sxs-lookup"><span data-stu-id="9f8b4-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f8b4-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="9f8b4-127">WhenDuplex</span></span>|<span data-ttu-id="9f8b4-128">Protokol webového soketu použijte v případě, že je kontrakt duplexní.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="9f8b4-129">Vždy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-129">Always</span></span>|<span data-ttu-id="9f8b4-130">Vždy používejte protokol webového soketu bez ohledu na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="9f8b4-131">Nikdy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-131">Never</span></span>|<span data-ttu-id="9f8b4-132">Nikdy nepoužívejte protokol webového soketu.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f8b4-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-133">Child Elements</span></span>  
 <span data-ttu-id="9f8b4-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f8b4-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f8b4-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f8b4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9f8b4-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f8b4-136">Element</span></span>|<span data-ttu-id="9f8b4-137">Description</span><span class="sxs-lookup"><span data-stu-id="9f8b4-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="9f8b4-138">Určuje NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9f8b4-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f8b4-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f8b4-139">Example</span></span>  
 <span data-ttu-id="9f8b4-140">Následující příklad ukazuje, jak použít \<webSocketSettings> element.</span><span class="sxs-lookup"><span data-stu-id="9f8b4-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f8b4-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f8b4-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="9f8b4-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="9f8b4-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f8b4-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="9f8b4-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9f8b4-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9f8b4-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
