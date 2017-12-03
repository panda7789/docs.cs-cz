---
title: Architektura aktivace WAS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cfbda764984305c141fd416baea8efa6aef4591
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="was-activation-architecture"></a><span data-ttu-id="897fd-102">Architektura aktivace WAS</span><span class="sxs-lookup"><span data-stu-id="897fd-102">WAS Activation Architecture</span></span>
<span data-ttu-id="897fd-103">Toto téma rozepisuje a součástí aktivační služba procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="897fd-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="897fd-104">Aktivace součásti</span><span class="sxs-lookup"><span data-stu-id="897fd-104">Activation Components</span></span>  
 <span data-ttu-id="897fd-105">SE skládá z několika součástí architektury:</span><span class="sxs-lookup"><span data-stu-id="897fd-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="897fd-106">Naslouchací proces adaptéry.</span><span class="sxs-lookup"><span data-stu-id="897fd-106">Listener adapters.</span></span> <span data-ttu-id="897fd-107">Služby systému Windows, které přijímat zprávy na konkrétních síťových protokolech a komunikovat se službou WAS pro směrování příchozích zpráv do správné pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="897fd-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="897fd-108">BYLA.</span><span class="sxs-lookup"><span data-stu-id="897fd-108">WAS.</span></span> <span data-ttu-id="897fd-109">Služba systému Windows, která spravuje vytváření a dobu života pracovních procesů.</span><span class="sxs-lookup"><span data-stu-id="897fd-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="897fd-110">Obecný pracovní proces spustitelný soubor (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="897fd-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="897fd-111">Správce aplikací.</span><span class="sxs-lookup"><span data-stu-id="897fd-111">Application manager.</span></span> <span data-ttu-id="897fd-112">Spravuje vytváření a dobu života aplikační domény, které zpracovávají hostování aplikací v rámci pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="897fd-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="897fd-113">Obslužné rutiny protokolu.</span><span class="sxs-lookup"><span data-stu-id="897fd-113">Protocol handlers.</span></span> <span data-ttu-id="897fd-114">Protokol konkrétní součásti, které spustit v pracovním procesu a spravovat komunikaci mezi pracovního procesu a adaptéry pro jednotlivé naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="897fd-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="897fd-115">Existují dva typy obslužných rutin protokolů: zpracovat obslužných rutin protokolů a obslužných rutin protokolů doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="897fd-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="897fd-116">Když WAS aktivuje instance procesu pracovního procesu, obslužné rutiny protokolu proces vyžaduje do pracovní proces načítá a používá k vytvoření domény aplikace k hostování aplikace Správce aplikací.</span><span class="sxs-lookup"><span data-stu-id="897fd-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="897fd-117">Doména aplikace načte kódu aplikace a také protokol AppDomain obslužných rutin, které používá síťové protokoly aplikace potřebují.</span><span class="sxs-lookup"><span data-stu-id="897fd-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="897fd-118">![Architektura byla](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="897fd-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="897fd-119">Naslouchací proces adaptéry</span><span class="sxs-lookup"><span data-stu-id="897fd-119">Listener Adapters</span></span>  
 <span data-ttu-id="897fd-120">Naslouchací proces adaptéry jsou jednotlivé služby systému Windows, které implementují logiku komunikace sítě slouží k přijímání zpráv pomocí síťového protokolu, na kterém naslouchat.</span><span class="sxs-lookup"><span data-stu-id="897fd-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="897fd-121">Následující tabulka uvádí adaptéry naslouchací proces pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoly.</span><span class="sxs-lookup"><span data-stu-id="897fd-121">The following table lists the listener adapters for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocols.</span></span>  
  
|<span data-ttu-id="897fd-122">Název služby adaptér naslouchání</span><span class="sxs-lookup"><span data-stu-id="897fd-122">Listener adapter service name</span></span>|<span data-ttu-id="897fd-123">Protokol</span><span class="sxs-lookup"><span data-stu-id="897fd-123">Protocol</span></span>|<span data-ttu-id="897fd-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="897fd-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="897fd-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="897fd-125">W3SVC</span></span>|<span data-ttu-id="897fd-126">http</span><span class="sxs-lookup"><span data-stu-id="897fd-126">http</span></span>|<span data-ttu-id="897fd-127">Součást společné, která poskytuje aktivace protokolu HTTP pro obě služby IIS 7.0 a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="897fd-127">Common component that provides HTTP activation for both IIS 7.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>|  
|<span data-ttu-id="897fd-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="897fd-128">NetTcpActivator</span></span>|<span data-ttu-id="897fd-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="897fd-129">net.tcp</span></span>|<span data-ttu-id="897fd-130">Závisí na službě NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="897fd-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="897fd-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="897fd-131">NetPipeActivator</span></span>|<span data-ttu-id="897fd-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="897fd-132">net.pipe</span></span>||  
|<span data-ttu-id="897fd-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="897fd-133">NetMsmqActivator</span></span>|<span data-ttu-id="897fd-134">NET.MSMQ</span><span class="sxs-lookup"><span data-stu-id="897fd-134">net.msmq</span></span>|<span data-ttu-id="897fd-135">Pro použití s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]– na základě aplikací služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="897fd-135">For use with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="897fd-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="897fd-136">NetMsmqActivator</span></span>|<span data-ttu-id="897fd-137">MSMQ.formatname</span><span class="sxs-lookup"><span data-stu-id="897fd-137">msmq.formatname</span></span>|<span data-ttu-id="897fd-138">Poskytuje zpětné kompatibilitě se stávajícími aplikacemi služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="897fd-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="897fd-139">Adaptéry naslouchací proces pro konkrétní protokoly jsou registrované během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu kódu XML.</span><span class="sxs-lookup"><span data-stu-id="897fd-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="897fd-140">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="897fd-140">Protocol Handlers</span></span>  
 <span data-ttu-id="897fd-141">Proces a obslužných rutin protokolů doménu aplikace pro konkrétní protokoly jsou zaregistrovány v souboru Web.config úrovni počítače.</span><span class="sxs-lookup"><span data-stu-id="897fd-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="897fd-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="897fd-142">See Also</span></span>  
 [<span data-ttu-id="897fd-143">Konfigurace WAS pro použití s WCF</span><span class="sxs-lookup"><span data-stu-id="897fd-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="897fd-144">Hostování funkcí systému Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="897fd-144">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
