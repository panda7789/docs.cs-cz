---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397696"
---
# <a name="nettcp"></a><span data-ttu-id="8d1ca-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="8d1ca-102">\<net.tcp></span></span>
<span data-ttu-id="8d1ca-103">Určuje nastavení konfigurace pro NET. Služba sdílení portů TCP, která umožňuje více procesů sdílet stejný port TCP.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
<span data-ttu-id="8d1ca-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d1ca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d1ca-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="8d1ca-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="8d1ca-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NET. TCP >**</span><span class="sxs-lookup"><span data-stu-id="8d1ca-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1ca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d1ca-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="8d1ca-108">type</span><span class="sxs-lookup"><span data-stu-id="8d1ca-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d1ca-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d1ca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8d1ca-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d1ca-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d1ca-111">Attributes</span></span>  
  
|<span data-ttu-id="8d1ca-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8d1ca-112">Attribute</span></span>|<span data-ttu-id="8d1ca-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8d1ca-113">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="8d1ca-114">Celé číslo určující maximální počet nevyřízených připojení, které jsou přijímány ze sdíleného připojení, ale ještě nebyly odeslány do služeb Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8d1ca-114">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="8d1ca-115">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-115">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="8d1ca-116">Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-116">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="8d1ca-117">Výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-117">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="8d1ca-118">Maximální počet připojení, která naslouchací proces mohl čekat na přijetí aplikací.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-118">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="8d1ca-119">Pokud je tato hodnota kvóty překročena, jsou nová příchozí připojení vynechána, ale čekají na přijetí.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-119">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="8d1ca-120">Funkce připojení, jako je například zabezpečení zprávy, mohou způsobit, že klient může otevřít více než jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-120">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="8d1ca-121">Správci služeb by měli při nastavení této kvóty brát v úvahu tato další připojení.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-121">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="8d1ca-122">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-122">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8d1ca-123">A <xref:System.TimeSpan> určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-123">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="8d1ca-124">Výchozí hodnota je "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="8d1ca-124">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="8d1ca-125">Logická hodnota, která označuje, zda služba sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP jménem služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-125">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="8d1ca-126">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d1ca-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d1ca-127">Child Elements</span></span>  
  
|<span data-ttu-id="8d1ca-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d1ca-128">Element</span></span>|<span data-ttu-id="8d1ca-129">Popis</span><span class="sxs-lookup"><span data-stu-id="8d1ca-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d1ca-130">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="8d1ca-130">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="8d1ca-131">Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-131">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d1ca-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d1ca-132">Parent Elements</span></span>  
  
|<span data-ttu-id="8d1ca-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d1ca-133">Element</span></span>|<span data-ttu-id="8d1ca-134">Popis</span><span class="sxs-lookup"><span data-stu-id="8d1ca-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d1ca-135">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="8d1ca-135">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="8d1ca-136">Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="8d1ca-136">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d1ca-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d1ca-137">Remarks</span></span>  
 <span data-ttu-id="8d1ca-138">Další informace o sdílení portů najdete v tématu [Sdílení portů Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="8d1ca-138">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="8d1ca-139">Informace o tom, jak nakonfigurovat službu sdílení portů, najdete v tématu [Konfigurace služby sdílení portů Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="8d1ca-139">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1ca-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d1ca-140">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="8d1ca-141">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="8d1ca-141">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="8d1ca-142">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="8d1ca-142">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
