---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400469"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="071ad-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="071ad-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="071ad-102">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="071ad-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
<span data-ttu-id="071ad-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="071ad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="071ad-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="071ad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="071ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="071ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="071ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="071ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="071ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="071ad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="071ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedPipeTransport >** ](namedpipetransport.md)</span><span class="sxs-lookup"><span data-stu-id="071ad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)</span></span>\
<span data-ttu-id="071ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="071ad-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071ad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="071ad-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="071ad-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="071ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="071ad-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="071ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="071ad-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="071ad-113">Attributes</span></span>  
  
|<span data-ttu-id="071ad-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="071ad-114">Attribute</span></span>|<span data-ttu-id="071ad-115">Popis</span><span class="sxs-lookup"><span data-stu-id="071ad-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="071ad-116">Řetězec definující název fondu připojení, který se používá pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="071ad-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="071ad-117">V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="071ad-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="071ad-118">Výchozí hodnota je "výchozí" řetězec.</span><span class="sxs-lookup"><span data-stu-id="071ad-118">The default is a "default" string.</span></span> <span data-ttu-id="071ad-119">Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.</span><span class="sxs-lookup"><span data-stu-id="071ad-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="071ad-120">Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno.</span><span class="sxs-lookup"><span data-stu-id="071ad-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="071ad-121">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="071ad-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="071ad-122">Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou.</span><span class="sxs-lookup"><span data-stu-id="071ad-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="071ad-123">Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="071ad-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="071ad-124">`idleTimeout` Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="071ad-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="071ad-125">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="071ad-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="071ad-126">Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="071ad-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="071ad-127">Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta.</span><span class="sxs-lookup"><span data-stu-id="071ad-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="071ad-128">V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="071ad-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="071ad-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="071ad-129">Child Elements</span></span>  
 <span data-ttu-id="071ad-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="071ad-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="071ad-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="071ad-131">Parent Elements</span></span>  
  
|<span data-ttu-id="071ad-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="071ad-132">Element</span></span>|<span data-ttu-id="071ad-133">Popis</span><span class="sxs-lookup"><span data-stu-id="071ad-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="071ad-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="071ad-134">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="071ad-135">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="071ad-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="071ad-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="071ad-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="071ad-137">Přenosy</span><span class="sxs-lookup"><span data-stu-id="071ad-137">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="071ad-138">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="071ad-138">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="071ad-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="071ad-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="071ad-140">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="071ad-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="071ad-141">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="071ad-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="071ad-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="071ad-142">\<customBinding></span></span>](custombinding.md)
