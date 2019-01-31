---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 85a9112def77fc31c8e4b826454894fe7372b31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257652"
---
# <a name="nettcp"></a><span data-ttu-id="e4ec6-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="e4ec6-102">\<net.tcp></span></span>
<span data-ttu-id="e4ec6-103">Určuje nastavení konfigurace sítě. TCP služba Sdílení portů, která umožňuje sdílet stejný port TCP mezi více procesy.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="e4ec6-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e4ec6-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="e4ec6-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="e4ec6-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ec6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4ec6-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="e4ec6-107">Typ</span><span class="sxs-lookup"><span data-stu-id="e4ec6-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4ec6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4ec6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4ec6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4ec6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4ec6-110">Attributes</span></span>  
  
|<span data-ttu-id="e4ec6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4ec6-111">Attribute</span></span>|<span data-ttu-id="e4ec6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ec6-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="e4ec6-113">Celé číslo určující maximální počet nevyřízených připojení, které jsou přijaty od sdíleného připojení, ale ještě nebyly odeslány do služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4ec6-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="e4ec6-114">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="e4ec6-115">Celé číslo, které určuje maximální počet souběžně otevřených přijímacích vláken na koncový bod naslouchací služby pro sdílení.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="e4ec6-116">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="e4ec6-117">Maximální počet připojení, která mohou v naslouchacím čekat na přijetí aplikací.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="e4ec6-118">Při překročení této kvóty hodnoty nové příchozí připojení jsou vynechány místo čekat na přijetí.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="e4ec6-119">Připojení funkce, jako je zabezpečení zpráv můžete donutit klienta k otevření více než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="e4ec6-120">Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="e4ec6-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e4ec6-122">A `TimeSpan` , který určuje časový limit pro vytváření datových rámců a jejich odesílání z přidružených připojení.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="e4ec6-123">Výchozí hodnota je "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="e4ec6-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="e4ec6-124">Logická hodnota, která označuje, zda služba Sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP, jménem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="e4ec6-125">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4ec6-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ec6-126">Child Elements</span></span>  
  
|<span data-ttu-id="e4ec6-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4ec6-127">Element</span></span>|<span data-ttu-id="e4ec6-128">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ec6-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ec6-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="e4ec6-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="e4ec6-130">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4ec6-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4ec6-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e4ec6-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4ec6-132">Element</span></span>|<span data-ttu-id="e4ec6-133">Popis</span><span class="sxs-lookup"><span data-stu-id="e4ec6-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4ec6-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e4ec6-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="e4ec6-135">Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="e4ec6-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4ec6-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4ec6-136">Remarks</span></span>  
 <span data-ttu-id="e4ec6-137">Další informace o sdílení portů najdete v tématu [sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="e4ec6-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="e4ec6-138">Postup konfigurace služby Sdílení portů najdete v tématu [konfigurace služby Sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="e4ec6-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ec6-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4ec6-139">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="e4ec6-140">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="e4ec6-140">Net.TCP Port Sharing</span></span>](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="e4ec6-141">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="e4ec6-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
