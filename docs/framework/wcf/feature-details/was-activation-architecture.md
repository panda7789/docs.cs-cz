---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184243"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="2a0f3-102">Architektura aktivace WAS</span><span class="sxs-lookup"><span data-stu-id="2a0f3-102">WAS Activation Architecture</span></span>
<span data-ttu-id="2a0f3-103">Toto téma rozepisuje a popisuje součásti služby aktivace procesů systému Windows (označované také jako WAS).</span><span class="sxs-lookup"><span data-stu-id="2a0f3-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="2a0f3-104">Aktivační součásti</span><span class="sxs-lookup"><span data-stu-id="2a0f3-104">Activation Components</span></span>  
 <span data-ttu-id="2a0f3-105">WAS se skládá z několika architektonických složek:</span><span class="sxs-lookup"><span data-stu-id="2a0f3-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="2a0f3-106">Adaptéry naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-106">Listener adapters.</span></span> <span data-ttu-id="2a0f3-107">Služby systému Windows, které přijímají zprávy na konkrétních síťových protokolech a komunikují s službou WAS směrovat příchozí zprávy do správného pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="2a0f3-108">Byl.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-108">WAS.</span></span> <span data-ttu-id="2a0f3-109">Služba systému Windows, která spravuje vytváření a životnost pracovních procesů.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="2a0f3-110">Spustitelný soubor obecného pracovního procesu (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="2a0f3-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="2a0f3-111">Správce aplikací.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-111">Application manager.</span></span> <span data-ttu-id="2a0f3-112">Spravuje vytváření a životnost aplikačních domén, které hostují aplikace v rámci pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="2a0f3-113">Obslužné rutiny protokolu.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-113">Protocol handlers.</span></span> <span data-ttu-id="2a0f3-114">Součásti specifické pro protokol, které se spouštějí v pracovním procesu a spravují komunikaci mezi pracovníproces a adaptéry jednotlivých naslouchacích procesů.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="2a0f3-115">Existují dva typy obslužných rutin protokolu: obslužné rutiny protokolu procesu a obslužné rutiny protokolu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="2a0f3-116">Když služba WAS aktivuje instanci pracovního procesu, načte obslužné rutiny protokolu procesu požadované do pracovního procesu a pomocí správce aplikací vytvoří doménu aplikace pro hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="2a0f3-117">Doména aplikace načte kód aplikace a obslužné rutiny protokolu AppDomain, které vyžadují síťové protokoly používané aplikací.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje architekturu WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="2a0f3-119">Adaptéry posluchače</span><span class="sxs-lookup"><span data-stu-id="2a0f3-119">Listener Adapters</span></span>  
 <span data-ttu-id="2a0f3-120">Naslouchací proces adaptéry jsou jednotlivé služby systému Windows, které implementují logiku síťové komunikace používané k přijímání zpráv pomocí síťového protokolu, na kterém naslouchají.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="2a0f3-121">V následující tabulce jsou uvedeny adaptéry naslouchacího procesu pro protokoly WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="2a0f3-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="2a0f3-122">Název služby adaptéru naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="2a0f3-122">Listener adapter service name</span></span>|<span data-ttu-id="2a0f3-123">Protocol (Protokol)</span><span class="sxs-lookup"><span data-stu-id="2a0f3-123">Protocol</span></span>|<span data-ttu-id="2a0f3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a0f3-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="2a0f3-125">W3svc</span><span class="sxs-lookup"><span data-stu-id="2a0f3-125">W3SVC</span></span>|<span data-ttu-id="2a0f3-126">HTTP</span><span class="sxs-lookup"><span data-stu-id="2a0f3-126">http</span></span>|<span data-ttu-id="2a0f3-127">Běžná součást, která poskytuje aktivaci protokolu HTTP pro iis 7.0 a WCF.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="2a0f3-128">NetTcpAktivátor</span><span class="sxs-lookup"><span data-stu-id="2a0f3-128">NetTcpActivator</span></span>|<span data-ttu-id="2a0f3-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="2a0f3-129">net.tcp</span></span>|<span data-ttu-id="2a0f3-130">Závisí na službě NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="2a0f3-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="2a0f3-131">NetPipeActivator</span></span>|<span data-ttu-id="2a0f3-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="2a0f3-132">net.pipe</span></span>||  
|<span data-ttu-id="2a0f3-133">NetMsmqAktivátor</span><span class="sxs-lookup"><span data-stu-id="2a0f3-133">NetMsmqActivator</span></span>|<span data-ttu-id="2a0f3-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="2a0f3-134">net.msmq</span></span>|<span data-ttu-id="2a0f3-135">Pro použití s aplikacemi služby Řízení front zpráv založených na wcf.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="2a0f3-136">NetMsmqAktivátor</span><span class="sxs-lookup"><span data-stu-id="2a0f3-136">NetMsmqActivator</span></span>|<span data-ttu-id="2a0f3-137">název formátu msmq.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-137">msmq.formatname</span></span>|<span data-ttu-id="2a0f3-138">Poskytuje zpětnou kompatibilitu s existujícími aplikacemi služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="2a0f3-139">Adaptéry naslouchacího procesu pro určité protokoly jsou registrovány během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu XML.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="2a0f3-140">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="2a0f3-140">Protocol Handlers</span></span>  
 <span data-ttu-id="2a0f3-141">Obslužné rutiny protokolu Process a AppDomain pro určité protokoly jsou registrovány v souboru Web.config na úrovni počítače.</span><span class="sxs-lookup"><span data-stu-id="2a0f3-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a0f3-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a0f3-142">See also</span></span>

- [<span data-ttu-id="2a0f3-143">Konfigurace WAS pro použití s WCF</span><span class="sxs-lookup"><span data-stu-id="2a0f3-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="2a0f3-144">[Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2a0f3-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
