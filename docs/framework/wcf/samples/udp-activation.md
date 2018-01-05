---
title: Aktivace UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65bbc7d8b6b4cb74be12e9460b173e73e1873765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="udp-activation"></a><span data-ttu-id="fb8d7-102">Aktivace UDP</span><span class="sxs-lookup"><span data-stu-id="fb8d7-102">UDP Activation</span></span>
<span data-ttu-id="fb8d7-103">Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="fb8d7-104">Ji rozšiřuje [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku, který se podporují procesu aktivace pomocí služby Aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="fb8d7-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="fb8d7-105">Ukázkový soubor obsahuje tři hlavní části:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="fb8d7-106">UDP protokol Aktivátor, samostatný proces, který přijímá zprávy UDP jménem aplikace, které mají být aktivována.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="fb8d7-107">Klient, který používá vlastní přenosu UDP k odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="fb8d7-108">Služba (hostovaného v pracovním procesu aktivován WAS), která přijímá zprávy pomocí přenosového vlastní UDP.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="fb8d7-109">Aktivátor protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="fb8d7-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="fb8d7-110">Aktivátor protokolu UDP je most mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-110">The UDP Protocol Activator is a bridge between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="fb8d7-111">Poskytuje datovou komunikaci pomocí protokolu UDP v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="fb8d7-112">Má dvě hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="fb8d7-113">BYL naslouchací proces adaptér (LA), která spolupracuje s WAS aktivovat procesy v reakci na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="fb8d7-114">Naslouchání protokolu UDP, které přijímá zprávy UDP jménem aplikace, které mají být aktivována.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="fb8d7-115">Aktivátor musí používat jako samostatný program na počítači serveru.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="fb8d7-116">Za normálních okolností WAS naslouchací proces adaptéry (například NetTcpActivator a NetPipeActivator) se implementují ve dlouho běžící služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="fb8d7-117">Ale pro jednoduchost a přehlednost implementuje Tato ukázka Aktivátor protokol jako samostatná aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="fb8d7-118">BYL adaptér naslouchání</span><span class="sxs-lookup"><span data-stu-id="fb8d7-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="fb8d7-119">BYL adaptér naslouchání pro protokol UDP je implementována ve `UdpListenerAdapter` třídy.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="fb8d7-120">Je modul, který komunikuje se službou WAS aktivace aplikace pro protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="fb8d7-121">Toho dosáhnete pomocí volání rozhraní API následující webového hostitele:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="fb8d7-122">Po počátečním volání metody `WebhostRegisterProtocol`, adaptér naslouchání obdrží zpětné volání `ApplicationCreated` z WAS pro všechny aplikace zaregistrovat v souboru applicationHost.config (umístěný ve % windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="fb8d7-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="fb8d7-123">V této ukázce jsme zpracovat jenom aplikace s protokolem UDP (s id protokolu jako "net.udp") povoleno.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="fb8d7-124">Pokud takový implementace reagovat na změny konfigurace dynamické k aplikaci (například přechodu aplikace ze zakázaného na povolený okně) může jiných implementacích zpracovávat jinak.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="fb8d7-125">Při zpětné volání `ConfigManagerInitializationCompleted` přijetí, znamená to, že WAS dokončil všechny oznámení pro inicializaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="fb8d7-126">V tomto okamžiku je připraven ke zpracování žádosti o aktivaci adaptér naslouchání.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="fb8d7-127">Při přijetí nového požadavku v prvním pro aplikaci, volá adaptér naslouchání `WebhostOpenListenerChannelInstance` do WAS, které spustí pracovní proces Pokud ještě není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="fb8d7-128">Pak jsou načtena obslužných rutin protokolů a začít komunikace mezi adaptér naslouchání a virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="fb8d7-129">Adaptér naslouchání je zaregistrován v %SystemRoot%\System32\inetsrv\ApplicationHost.config v <`listenerAdapters`> části jako následující:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="fb8d7-130">Naslouchací proces protokolu</span><span class="sxs-lookup"><span data-stu-id="fb8d7-130">Protocol Listener</span></span>  
 <span data-ttu-id="fb8d7-131">Naslouchací proces protokolu UDP je modul uvnitř Aktivátor protokolu, která naslouchá na koncový bod UDP jménem virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="fb8d7-132">Je implementována ve třídě `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="fb8d7-133">Koncový bod je reprezentován jako `IPEndpoint` pro které je extrahován číslo portu z vazby protokolu pro lokalitu.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="fb8d7-134">Služba Řízení</span><span class="sxs-lookup"><span data-stu-id="fb8d7-134">Control Service</span></span>  
 <span data-ttu-id="fb8d7-135">V této ukázce používáme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ke komunikaci mezi aktivátoru a WAS pracovní proces.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-135">In this sample, we use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="fb8d7-136">Služba, která se nachází v aktivační procedura je volána službu řízení.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="fb8d7-137">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="fb8d7-137">Protocol Handlers</span></span>  
 <span data-ttu-id="fb8d7-138">Po volání adaptér naslouchání `WebhostOpenListenerChannelInstance`, správce proces WAS spustí pracovní proces, pokud není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="fb8d7-139">Potom Správce aplikací uvnitř pracovního procesu se načte UDP proces protokol obslužné rutiny (PPH) s požadavkem, pro který `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="fb8d7-140">PPH ve voláních oplátku `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="fb8d7-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="fb8d7-141">Spustit obslužnou rutinu pro protokol AppDomain UDP (ADPH).</span><span class="sxs-lookup"><span data-stu-id="fb8d7-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="fb8d7-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb8d7-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="fb8d7-143">Informace je zaregistrován v souboru Web.config následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="fb8d7-144">Speciální nastavení pro tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="fb8d7-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="fb8d7-145">Tato ukázka můžete pouze vytvořené a spustit v systému Windows Vista, Windows Server 2008 nebo Windows 7.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="fb8d7-146">Pokud chcete spustit ukázku, musíte nejprve získat všechny součásti správně nastavené.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="fb8d7-147">Ukázku nainstalujete pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="fb8d7-148">Nastavení této ukázky</span><span class="sxs-lookup"><span data-stu-id="fb8d7-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="fb8d7-149">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="fb8d7-150">Sestavení projektu v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="fb8d7-151">Po sestavení také provede následující operace ve fázi po sestavení:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="fb8d7-152">Nainstaluje UDP vazbu k webu "Default Web Site".</span><span class="sxs-lookup"><span data-stu-id="fb8d7-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="fb8d7-153">Vytvoří virtuální aplikace "ServiceModelSamples" tak, aby odkazoval na fyzickou cestu: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="fb8d7-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="fb8d7-154">Umožňuje také protokol "net.udp" pro tuto virtuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="fb8d7-155">Spuštění aplikace v uživatelském rozhraní "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="fb8d7-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="fb8d7-156">Klikněte na tlačítko **instalace** kartě, zaškrtněte následující zaškrtávací políčka a pak klikněte na tlačítko **nainstalovat** k instalaci:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="fb8d7-157">Adaptér naslouchání UDP</span><span class="sxs-lookup"><span data-stu-id="fb8d7-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="fb8d7-158">Obslužné rutiny protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="fb8d7-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="fb8d7-159">Klikněte **aktivace** uživatelské rozhraní aplikace "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="fb8d7-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="fb8d7-160">Klikněte **spustit** tlačítko spusťte adaptér naslouchání.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="fb8d7-161">Nyní jste připraveni ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb8d7-162">Po skončení této ukázce, je nutné spustit Cleanup.bat odebrat vazby net.udp z "výchozí web".</span><span class="sxs-lookup"><span data-stu-id="fb8d7-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="fb8d7-163">Využití vzorků</span><span class="sxs-lookup"><span data-stu-id="fb8d7-163">Sample Usage</span></span>  
 <span data-ttu-id="fb8d7-164">Po sestavení existují čtyři různé binární soubory generované:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="fb8d7-165">Client.exe: Kód klienta.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-165">Client.exe: The client code.</span></span> <span data-ttu-id="fb8d7-166">Souboru App.config se zkompiluje do konfiguračního souboru klienta Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="fb8d7-167">UDPActivation.dll: knihovnu, která obsahuje všechny hlavní implementace UDP.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="fb8d7-168">Service.dll: Kódu služby.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-168">Service.dll: The service code.</span></span> <span data-ttu-id="fb8d7-169">Je zkopírován do adresáře \bin ServiceModelSamples virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="fb8d7-170">Soubor služby je Service.svc a konfigurační soubor je soubor Web.config. Po sestavení, se zkopírují do následujícího umístění: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="fb8d7-171">WasNetActivator: UDP Aktivátor program.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="fb8d7-172">Ujistěte se, zda všechny požadované součásti jsou nainstalovány správně.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="fb8d7-173">Následující kroky ukazují, jak spustit ukázku:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="fb8d7-174">Ujistěte se, že byly spuštěny následující služby systému Windows:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="fb8d7-175">Aktivační služba procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="fb8d7-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="fb8d7-176">Internetová informační služba (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="fb8d7-177">Spusťte aktivátoru WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="fb8d7-178">V části **aktivace** kartě, bude jediným používaným protokolem, **UDP**, je vybraný v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="fb8d7-179">Klikněte na tlačítko **spustit** tlačítko Spustit aktivační procedura.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="fb8d7-180">Jakmile začne aktivátoru, můžete spustit kód klienta spuštěním Client.exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="fb8d7-181">Následuje příklad výstupu:</span><span class="sxs-lookup"><span data-stu-id="fb8d7-181">The following is the sample output:</span></span>  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb8d7-182">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb8d7-183">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="fb8d7-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fb8d7-184">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb8d7-185">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fb8d7-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="fb8d7-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb8d7-186">See Also</span></span>
