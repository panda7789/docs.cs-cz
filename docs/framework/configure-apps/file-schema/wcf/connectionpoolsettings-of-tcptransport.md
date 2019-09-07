---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398100"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="47304-102">\<connectionPoolSettings > \<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="47304-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="47304-103">Určuje další nastavení fondu připojení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="47304-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
<span data-ttu-id="47304-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="47304-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47304-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="47304-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="47304-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="47304-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="47304-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="47304-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="47304-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="47304-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="47304-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tcpTransport >** ](tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="47304-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)</span></span>\
<span data-ttu-id="47304-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="47304-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47304-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47304-111">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47304-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47304-112">Attributes and Elements</span></span>  
 <span data-ttu-id="47304-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47304-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47304-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="47304-114">Attributes</span></span>  
  
|<span data-ttu-id="47304-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="47304-115">Attribute</span></span>|<span data-ttu-id="47304-116">Popis</span><span class="sxs-lookup"><span data-stu-id="47304-116">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="47304-117">Řetězec definující název fondu připojení, který se používá pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="47304-117">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="47304-118">V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="47304-118">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="47304-119">Výchozí hodnota je "výchozí" řetězec.</span><span class="sxs-lookup"><span data-stu-id="47304-119">The default is a "default" string.</span></span> <span data-ttu-id="47304-120">Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.</span><span class="sxs-lookup"><span data-stu-id="47304-120">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="47304-121">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno.</span><span class="sxs-lookup"><span data-stu-id="47304-121">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="47304-122">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="47304-122">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="47304-123">A <xref:System.TimeSpan> určuje dobu, po jejímž uplynutí je aktivní připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="47304-123">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="47304-124">Výchozí hodnota je 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="47304-124">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="47304-125">Po návratu do mezipaměti připojení a při aktivním přenosu se připojení zavře.</span><span class="sxs-lookup"><span data-stu-id="47304-125">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="47304-126">Mezipaměť připojení, kterou přenos TCP používá, vytvoří nová připojení podle požadavků pro každý koncový bod až do limitu mezipaměti, který nastaví.`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="47304-126">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="47304-127">Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou.</span><span class="sxs-lookup"><span data-stu-id="47304-127">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="47304-128">Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="47304-128">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="47304-129">`idleTimeout` Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="47304-129">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="47304-130">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="47304-130">The default is 10.</span></span><br /><br /> <span data-ttu-id="47304-131">Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="47304-131">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="47304-132">Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta.</span><span class="sxs-lookup"><span data-stu-id="47304-132">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="47304-133">V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="47304-133">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47304-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47304-134">Child Elements</span></span>  
 <span data-ttu-id="47304-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="47304-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47304-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47304-136">Parent Elements</span></span>  
  
|<span data-ttu-id="47304-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="47304-137">Element</span></span>|<span data-ttu-id="47304-138">Popis</span><span class="sxs-lookup"><span data-stu-id="47304-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47304-139">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="47304-139">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="47304-140">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="47304-140">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47304-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47304-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="47304-142">Přenosy</span><span class="sxs-lookup"><span data-stu-id="47304-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="47304-143">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="47304-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="47304-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="47304-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="47304-145">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="47304-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="47304-146">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="47304-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="47304-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="47304-147">\<customBinding></span></span>](custombinding.md)
