---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400469"
---
# \<connectionPoolSettings>
<span data-ttu-id="7ded5-101">Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="7ded5-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="7ded5-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ded5-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ded5-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ded5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7ded5-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7ded5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ded5-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ded5-105">Attributes</span></span>  
  
|<span data-ttu-id="7ded5-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="7ded5-106">Attribute</span></span>|<span data-ttu-id="7ded5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ded5-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="7ded5-108">Řetězec definující název fondu připojení, který se používá pro odchozí kanály.</span><span class="sxs-lookup"><span data-stu-id="7ded5-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="7ded5-109">V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="7ded5-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="7ded5-110">Výchozí hodnota je "výchozí" řetězec.</span><span class="sxs-lookup"><span data-stu-id="7ded5-110">The default is a "default" string.</span></span> <span data-ttu-id="7ded5-111">Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.</span><span class="sxs-lookup"><span data-stu-id="7ded5-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="7ded5-112">Kladná hodnota <xref:System.TimeSpan> , která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno.</span><span class="sxs-lookup"><span data-stu-id="7ded5-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="7ded5-113">Výchozí hodnota je 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="7ded5-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="7ded5-114">Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou.</span><span class="sxs-lookup"><span data-stu-id="7ded5-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="7ded5-115">Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="7ded5-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="7ded5-116">`idleTimeout`Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7ded5-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="7ded5-117">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="7ded5-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="7ded5-118">Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="7ded5-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="7ded5-119">Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta.</span><span class="sxs-lookup"><span data-stu-id="7ded5-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="7ded5-120">V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="7ded5-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ded5-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ded5-121">Child Elements</span></span>  
 <span data-ttu-id="7ded5-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7ded5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ded5-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ded5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7ded5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ded5-124">Element</span></span>|<span data-ttu-id="7ded5-125">Description</span><span class="sxs-lookup"><span data-stu-id="7ded5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="7ded5-126">Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="7ded5-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ded5-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ded5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7ded5-128">Přenosy</span><span class="sxs-lookup"><span data-stu-id="7ded5-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="7ded5-129">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="7ded5-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7ded5-130">Vazby</span><span class="sxs-lookup"><span data-stu-id="7ded5-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ded5-131">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7ded5-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7ded5-132">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7ded5-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
