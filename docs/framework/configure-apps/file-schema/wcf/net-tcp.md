---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 63cef2b85aa57b5c1c0e0add1794ebedc73d96c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933053"
---
# <a name="nettcp"></a><span data-ttu-id="3e098-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="3e098-102">\<net.tcp></span></span>
<span data-ttu-id="3e098-103">Určuje nastavení konfigurace pro NET. Služba sdílení portů TCP, která umožňuje více procesů sdílet stejný port TCP.</span><span class="sxs-lookup"><span data-stu-id="3e098-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="3e098-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3e098-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="3e098-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="3e098-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e098-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e098-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="3e098-107">type</span><span class="sxs-lookup"><span data-stu-id="3e098-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e098-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3e098-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e098-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3e098-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e098-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3e098-110">Attributes</span></span>  
  
|<span data-ttu-id="3e098-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3e098-111">Attribute</span></span>|<span data-ttu-id="3e098-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3e098-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="3e098-113">Celé číslo určující maximální počet nevyřízených připojení, které jsou přijímány ze sdíleného připojení, ale ještě nebyly odeslány do služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3e098-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="3e098-114">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="3e098-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="3e098-115">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="3e098-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="3e098-116">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="3e098-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="3e098-117">Maximální počet připojení, která naslouchací proces mohl čekat na přijetí aplikací.</span><span class="sxs-lookup"><span data-stu-id="3e098-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="3e098-118">Pokud je tato hodnota kvóty překročena, jsou nová příchozí připojení vynechána, ale čekají na přijetí.</span><span class="sxs-lookup"><span data-stu-id="3e098-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="3e098-119">Funkce připojení, jako je například zabezpečení zprávy, mohou způsobit, že klient může otevřít více než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="3e098-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="3e098-120">Správci služeb by měli při nastavení této kvóty brát v úvahu tato další připojení.</span><span class="sxs-lookup"><span data-stu-id="3e098-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="3e098-121">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="3e098-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3e098-122">A <xref:System.TimeSpan> určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="3e098-122">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="3e098-123">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="3e098-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="3e098-124">Logická hodnota, která označuje, zda služba sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP jménem služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="3e098-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="3e098-125">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3e098-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e098-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3e098-126">Child Elements</span></span>  
  
|<span data-ttu-id="3e098-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="3e098-127">Element</span></span>|<span data-ttu-id="3e098-128">Popis</span><span class="sxs-lookup"><span data-stu-id="3e098-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e098-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="3e098-129">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="3e098-130">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="3e098-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e098-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3e098-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3e098-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="3e098-132">Element</span></span>|<span data-ttu-id="3e098-133">Popis</span><span class="sxs-lookup"><span data-stu-id="3e098-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e098-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3e098-134">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="3e098-135">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="3e098-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e098-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e098-136">Remarks</span></span>  
 <span data-ttu-id="3e098-137">Další informace o sdílení portů najdete v tématu [Sdílení portů Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="3e098-137">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="3e098-138">Informace o tom, jak nakonfigurovat službu sdílení portů, najdete v tématu [Konfigurace služby sdílení portů Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="3e098-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e098-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e098-139">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="3e098-140">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="3e098-140">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="3e098-141">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="3e098-141">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
