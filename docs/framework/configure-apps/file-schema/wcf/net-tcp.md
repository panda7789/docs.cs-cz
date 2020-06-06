---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397696"
---
# \<net.tcp>
<span data-ttu-id="d1b9f-102">Určuje nastavení konfigurace pro NET. Služba sdílení portů TCP, která umožňuje více procesů sdílet stejný port TCP.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-102">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="d1b9f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1b9f-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="d1b9f-104">Typ</span><span class="sxs-lookup"><span data-stu-id="d1b9f-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1b9f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1b9f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d1b9f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1b9f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1b9f-107">Attributes</span></span>  
  
|<span data-ttu-id="d1b9f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="d1b9f-108">Attribute</span></span>|<span data-ttu-id="d1b9f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d1b9f-109">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="d1b9f-110">Celé číslo určující maximální počet nevyřízených připojení, které jsou přijímány ze sdíleného připojení, ale ještě nebyly odeslány do služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d1b9f-110">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="d1b9f-111">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-111">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="d1b9f-112">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-112">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="d1b9f-113">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-113">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="d1b9f-114">Maximální počet připojení, která naslouchací proces mohl čekat na přijetí aplikací.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-114">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="d1b9f-115">Pokud je tato hodnota kvóty překročena, jsou nová příchozí připojení vynechána, ale čekají na přijetí.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-115">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="d1b9f-116">Funkce připojení, jako je například zabezpečení zprávy, mohou způsobit, že klient může otevřít více než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-116">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="d1b9f-117">Správci služeb by měli při nastavení této kvóty brát v úvahu tato další připojení.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-117">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="d1b9f-118">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-118">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d1b9f-119">A <xref:System.TimeSpan> Určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-119">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="d1b9f-120">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="d1b9f-120">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="d1b9f-121">Logická hodnota, která označuje, zda služba sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP jménem služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-121">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="d1b9f-122">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-122">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1b9f-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1b9f-123">Child Elements</span></span>  
  
|<span data-ttu-id="d1b9f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1b9f-124">Element</span></span>|<span data-ttu-id="d1b9f-125">Description</span><span class="sxs-lookup"><span data-stu-id="d1b9f-125">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="d1b9f-126">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-126">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1b9f-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1b9f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d1b9f-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1b9f-128">Element</span></span>|<span data-ttu-id="d1b9f-129">Description</span><span class="sxs-lookup"><span data-stu-id="d1b9f-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="d1b9f-130">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="d1b9f-130">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1b9f-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1b9f-131">Remarks</span></span>  
 <span data-ttu-id="d1b9f-132">Další informace o sdílení portů najdete v tématu [Sdílení portů Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9f-132">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="d1b9f-133">Informace o tom, jak nakonfigurovat službu sdílení portů, najdete v tématu [Konfigurace služby sdílení portů Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="d1b9f-133">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b9f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1b9f-134">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="d1b9f-135">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d1b9f-135">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="d1b9f-136">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d1b9f-136">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
