---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143717"
---
# <a name="udp-activation"></a><span data-ttu-id="5b291-102">Aktivace UDP</span><span class="sxs-lookup"><span data-stu-id="5b291-102">UDP Activation</span></span>
<span data-ttu-id="5b291-103">Tato ukázka je založena na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="5b291-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="5b291-104">Rozšiřuje [transport: Ukázka UDP](../../../../docs/framework/wcf/samples/transport-udp.md) pro podporu aktivace procesu pomocí služby aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="5b291-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="5b291-105">Vzorek se skládá ze tří hlavních kusů:</span><span class="sxs-lookup"><span data-stu-id="5b291-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="5b291-106">Aktivátor protokolu UDP, samostatný proces, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.</span><span class="sxs-lookup"><span data-stu-id="5b291-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="5b291-107">Klient, který používá vlastní přenos UDP k odesílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="5b291-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="5b291-108">Služba (hostovaná v pracovním procesu aktivovaném službou WAS), která přijímá zprávy prostřednictvím vlastního přenosu UDP.</span><span class="sxs-lookup"><span data-stu-id="5b291-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="5b291-109">Aktivátor protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="5b291-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="5b291-110">Aktivátor protokolu UDP je most mezi klientem WCF a službou WCF.</span><span class="sxs-lookup"><span data-stu-id="5b291-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="5b291-111">Poskytuje datovou komunikaci prostřednictvím protokolu UDP na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="5b291-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="5b291-112">Má dvě hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="5b291-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="5b291-113">WAS Listener Adapter (LA), který spolupracuje s WAS na aktivaci procesů v reakci na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="5b291-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="5b291-114">Naslouchací proces protokolu UDP, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.</span><span class="sxs-lookup"><span data-stu-id="5b291-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="5b291-115">Aktivátor musí být spuštěn jako samostatný program v počítači serveru.</span><span class="sxs-lookup"><span data-stu-id="5b291-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="5b291-116">Za normálních okolností was naslouchací proces adaptéry (například NetTcpActivator a NetPipeActivator) jsou implementovány v dlouhotrvající služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b291-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="5b291-117">Pro jednoduchost a srozumitelnost však tato ukázka implementuje aktivátor protokolu jako samostatnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b291-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="5b291-118">Adaptér naslouchacího procesu SLUŽBY</span><span class="sxs-lookup"><span data-stu-id="5b291-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="5b291-119">Adaptér naslouchacího procesu `UdpListenerAdapter` WAS pro UDP je implementován ve třídě.</span><span class="sxs-lookup"><span data-stu-id="5b291-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="5b291-120">Jedná se o modul, který spolupracuje s WAS k provedení aktivace aplikace pro protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="5b291-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="5b291-121">Toho je dosaženo voláním následujícíwebhost API:</span><span class="sxs-lookup"><span data-stu-id="5b291-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="5b291-122">Po počátečním volání `WebhostRegisterProtocol`adaptér posluchače `ApplicationCreated` přijme zpětné volání od služby WAS pro všechny aplikace registrované v souboru applicationHost.config (umístěnév %windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="5b291-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="5b291-123">V této ukázce zpracováváme pouze aplikace s protokolem UDP (s id protokolu jako "net.udp") povoleno.</span><span class="sxs-lookup"><span data-stu-id="5b291-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="5b291-124">Jiné implementace to mohou zpracovat jinak, pokud tyto implementace reagují na změny dynamické konfigurace aplikace (například přechod aplikace ze zakázané na povolenou).</span><span class="sxs-lookup"><span data-stu-id="5b291-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="5b291-125">Po přijetí `ConfigManagerInitializationCompleted` zpětného volání označuje, že služba WAS dokončila všechna oznámení pro inicializaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="5b291-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="5b291-126">V tomto okamžiku je adaptér naslouchací proces připraven ke zpracování požadavků na aktivaci.</span><span class="sxs-lookup"><span data-stu-id="5b291-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="5b291-127">Při prvním požadavku na aplikaci přijde nový požadavek, adaptér naslouchacího procesu volá do služby `WebhostOpenListenerChannelInstance` WAS, která spustí pracovní proces, pokud ještě není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="5b291-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="5b291-128">Poté jsou načteny obslužné rutiny protokolu a komunikace mezi adaptérem naslouchacího procesu a virtuální aplikací může být zahájena.</span><span class="sxs-lookup"><span data-stu-id="5b291-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="5b291-129">Adaptér naslouchacího procesu je registrován v části %SystemRoot%\System32\inetsrv\ApplicationHost.config v části <`listenerAdapters`> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b291-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="5b291-130">Naslouchací proces protokolu</span><span class="sxs-lookup"><span data-stu-id="5b291-130">Protocol Listener</span></span>  
 <span data-ttu-id="5b291-131">Naslouchací proces protokolu UDP je modul uvnitř aktivátoru protokolu, který naslouchá koncovému bodu UDP jménem virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b291-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="5b291-132">Je implementována `UdpSocketListener`ve třídě .</span><span class="sxs-lookup"><span data-stu-id="5b291-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="5b291-133">Koncový bod je `IPEndpoint` reprezentován jako pro které je číslo portu extrahovánzující z vazby protokolu pro lokalitu.</span><span class="sxs-lookup"><span data-stu-id="5b291-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="5b291-134">Kontrolní služba</span><span class="sxs-lookup"><span data-stu-id="5b291-134">Control Service</span></span>  
 <span data-ttu-id="5b291-135">V této ukázce používáme WCF ke komunikaci mezi aktivátorem a pracovníproces WAS.</span><span class="sxs-lookup"><span data-stu-id="5b291-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="5b291-136">Služba, která je umístěna v aktivátoru se nazývá řídicí služba.</span><span class="sxs-lookup"><span data-stu-id="5b291-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="5b291-137">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="5b291-137">Protocol Handlers</span></span>  
 <span data-ttu-id="5b291-138">Po volání `WebhostOpenListenerChannelInstance`adaptéru naslouchací proces , správce procesu WAS spustí pracovní proces, pokud není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="5b291-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="5b291-139">Správce aplikací uvnitř pracovního procesu pak načte obslužnou rutinu `ListenerChannelId`protokolu procesu UDP (PPH) s požadavkem na tento .</span><span class="sxs-lookup"><span data-stu-id="5b291-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="5b291-140">PPH v zase `IAdphManager`volání .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="5b291-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="5b291-141">spuštění obslužné rutiny protokolu UDP AppDomain Protocol (ADPH).</span><span class="sxs-lookup"><span data-stu-id="5b291-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="5b291-142">HostedUDPTransportKonfigurace</span><span class="sxs-lookup"><span data-stu-id="5b291-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="5b291-143">Informace jsou registrovány v souboru Web.config následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b291-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="5b291-144">Speciální nastavení pro tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="5b291-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="5b291-145">Tuto ukázku lze sestavit a spustit pouze v systémech Windows Vista, Windows Server 2008 nebo Windows 7.</span><span class="sxs-lookup"><span data-stu-id="5b291-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="5b291-146">Chcete-li spustit ukázku, musíte nejprve získat všechny součásti správně nastavit.</span><span class="sxs-lookup"><span data-stu-id="5b291-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="5b291-147">K instalaci ukázky použijte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="5b291-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="5b291-148">Chcete-li nastavit tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="5b291-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="5b291-149">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b291-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5b291-150">Vytvořte projekt v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="5b291-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="5b291-151">Po kompilaci také provádí následující operace ve fázi po sestavení:</span><span class="sxs-lookup"><span data-stu-id="5b291-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="5b291-152">Nainstaluje vazbu UDP na web "Výchozí web".</span><span class="sxs-lookup"><span data-stu-id="5b291-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="5b291-153">Vytvoří virtuální aplikaci ServiceModelSamples tak, aby ukazovala na fyzickou cestu: %SystemDrive%\inetpub\wwwroot\servicemodelsamples.Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="5b291-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="5b291-154">Umožňuje také protokol net.udp pro tuto virtuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5b291-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="5b291-155">Spusťte aplikaci uživatelského rozhraní "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="5b291-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="5b291-156">Klikněte na kartu **Instalace,** zaškrtněte následující políčka a potom je nainstalujte kliknutím na **Instalovat:**</span><span class="sxs-lookup"><span data-stu-id="5b291-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="5b291-157">Adaptér naslouchacího procesu UDP</span><span class="sxs-lookup"><span data-stu-id="5b291-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="5b291-158">Obslužné rutiny protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="5b291-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="5b291-159">Klikněte na kartu **Aktivace** aplikace uživatelského rozhraní "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="5b291-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="5b291-160">Klepnutím na tlačítko **Start** spusťte adaptér naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="5b291-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="5b291-161">Nyní jste připraveni spustit program.</span><span class="sxs-lookup"><span data-stu-id="5b291-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5b291-162">Po dokončení této ukázky je nutné spustit soubor Cleanup.bat a odebrat vazbu net.udp z "Výchozího webu".</span><span class="sxs-lookup"><span data-stu-id="5b291-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="5b291-163">Ukázka použití</span><span class="sxs-lookup"><span data-stu-id="5b291-163">Sample Usage</span></span>  
 <span data-ttu-id="5b291-164">Po kompilaci jsou generovány čtyři různé binární soubory:</span><span class="sxs-lookup"><span data-stu-id="5b291-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="5b291-165">Client.exe: Kód klienta.</span><span class="sxs-lookup"><span data-stu-id="5b291-165">Client.exe: The client code.</span></span> <span data-ttu-id="5b291-166">Nástroj App.config je zkompilován do konfiguračního souboru klienta Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="5b291-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="5b291-167">UDPActivation.dll: knihovna, která obsahuje všechny hlavní implementace UDP.</span><span class="sxs-lookup"><span data-stu-id="5b291-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="5b291-168">Service.dll: Kód služby.</span><span class="sxs-lookup"><span data-stu-id="5b291-168">Service.dll: The service code.</span></span> <span data-ttu-id="5b291-169">Tato možnost je zkopírována do adresáře \bin virtuální aplikace ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5b291-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="5b291-170">Soubor služby je Service.svc a konfigurační soubor je Web.config. Po kompilaci jsou zkopírovány do následujícího umístění: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5b291-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="5b291-171">WasNetActivator: Aktivátor UDP program.</span><span class="sxs-lookup"><span data-stu-id="5b291-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="5b291-172">Ujistěte se, že jsou všechny požadované kusy nainstalovány správně.</span><span class="sxs-lookup"><span data-stu-id="5b291-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="5b291-173">Následující kroky ukazují, jak spustit ukázku:</span><span class="sxs-lookup"><span data-stu-id="5b291-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="5b291-174">Ujistěte se, že byly spuštěny následující služby systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5b291-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="5b291-175">Služba aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="5b291-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="5b291-176">Internetové informační služby (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="5b291-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="5b291-177">Potom spusťte aktivátor WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="5b291-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="5b291-178">Na kartě **Aktivace** je v rozevíracím seznamu vybrán pouze protokol **UDP**.</span><span class="sxs-lookup"><span data-stu-id="5b291-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="5b291-179">Kliknutím na tlačítko **Start** spusťte aktivátor.</span><span class="sxs-lookup"><span data-stu-id="5b291-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="5b291-180">Po spuštění aktivátoru můžete spustit kód klienta spuštěním Client.exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="5b291-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="5b291-181">Ukázkový výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5b291-181">The following is the sample output:</span></span>  
  
    ```console  
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
> <span data-ttu-id="5b291-182">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="5b291-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b291-183">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5b291-183">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b291-184">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5b291-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b291-185">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b291-185">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
