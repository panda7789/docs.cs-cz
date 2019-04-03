---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: a61b7fce891ea1ab68f48f836ffaae2b96c8e25d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836321"
---
# <a name="udp-activation"></a><span data-ttu-id="e623f-102">Aktivace UDP</span><span class="sxs-lookup"><span data-stu-id="e623f-102">UDP Activation</span></span>
<span data-ttu-id="e623f-103">Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="e623f-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="e623f-104">Rozšiřuje [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku pro podporu proces aktivace pomocí služby Aktivace procesu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="e623f-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="e623f-105">Vzorek se skládá ze tří hlavních částí:</span><span class="sxs-lookup"><span data-stu-id="e623f-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="e623f-106">UDP protokolu Aktivátor, samostatným procesem, který přijímá zprávy protokolu UDP jménem aplikace, které se mají aktivovat.</span><span class="sxs-lookup"><span data-stu-id="e623f-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="e623f-107">Klient, který používá vlastní přenos UDP k zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="e623f-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="e623f-108">Služba (prostředí v pracovním procesu aktivoval WAS), která přijímá zprávy přes vlastní přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="e623f-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="e623f-109">Aktivátor protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="e623f-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="e623f-110">Aktivátor protokolu UDP je most mezi klienta WCF a služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e623f-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="e623f-111">Poskytuje datovou komunikaci prostřednictvím protokolu UDP v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="e623f-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="e623f-112">Má dvě hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="e623f-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="e623f-113">BYL naslouchací proces adaptéru (LA), který spolupracuje s WAS aktivovat procesy odpověď na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="e623f-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="e623f-114">UDP protokolu naslouchací proces, který dokáže akceptovat nezadání zpráv UDP jménem aplikace, které se mají aktivovat.</span><span class="sxs-lookup"><span data-stu-id="e623f-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="e623f-115">Aktivátor musí běžet jako samostatná aplikace na počítači serveru.</span><span class="sxs-lookup"><span data-stu-id="e623f-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="e623f-116">Za normálních okolností adaptéry listener WAS (například NetTcpActivator a NetPipeActivator) jsou implementovány v dlouhotrvajících služby Windows.</span><span class="sxs-lookup"><span data-stu-id="e623f-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="e623f-117">Ale pro zjednodušení a srozumitelnost implementuje Tato ukázka Aktivátor protokol jako samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="e623f-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="e623f-118">BYL adaptér naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="e623f-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="e623f-119">Adaptér naslouchání bylo pro UDP je implementován v `UdpListenerAdapter` třídy.</span><span class="sxs-lookup"><span data-stu-id="e623f-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="e623f-120">Je modul, který komunikuje s WAS provádět aktivace aplikací pro protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="e623f-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="e623f-121">Toho dosáhnete pomocí volání následujícího rozhraní API webového hostitele:</span><span class="sxs-lookup"><span data-stu-id="e623f-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="e623f-122">Po počátečním volání `WebhostRegisterProtocol`, adaptér naslouchací proces obdrží zpětné volání `ApplicationCreated` z WAS pro všechny aplikace zaregistrovaný v souboru applicationHost.config (umístěné v % windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="e623f-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="e623f-123">V této ukázce jsme zpracovat pouze aplikace s protokolem UDP (s id protokolu jako "net.udp") povolena.</span><span class="sxs-lookup"><span data-stu-id="e623f-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="e623f-124">Pokud takové implementace reagovat na změny konfigurace dynamické aplikace (například přechodu aplikace ze zakázaného na povolený okně) může v jiných implementacích zpracovávají jinak.</span><span class="sxs-lookup"><span data-stu-id="e623f-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="e623f-125">Při zpětném volání `ConfigManagerInitializationCompleted` přijetí, znamená to této WAS dokončil všechny oznámení pro inicializaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="e623f-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="e623f-126">Adaptér naslouchací proces je v tuto chvíli připravena na zpracování žádosti o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="e623f-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="e623f-127">Jakmile novou žádost o prvním pro aplikaci, adaptér naslouchací proces volá `WebhostOpenListenerChannelInstance` do WAS, které spustí pracovní proces Pokud ještě není spuštěný.</span><span class="sxs-lookup"><span data-stu-id="e623f-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="e623f-128">Potom se načtou obslužné rutiny protokolu a může začít komunikace mezi adaptérem naslouchací proces a virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="e623f-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="e623f-129">Adaptér naslouchání je zaregistrován v %SystemRoot%\System32\inetsrv\ApplicationHost.config v <`listenerAdapters`> části následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e623f-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="e623f-130">Naslouchací proces protokolu</span><span class="sxs-lookup"><span data-stu-id="e623f-130">Protocol Listener</span></span>  
 <span data-ttu-id="e623f-131">Naslouchací proces protokolu UDP je modul uvnitř Aktivátor protokolu, která naslouchá na koncový bod UDP jménem virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="e623f-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="e623f-132">Je implementován ve třídě `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="e623f-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="e623f-133">Koncový bod je vyjádřena jako `IPEndpoint` pro které je extrahován číslo portu z vazby protokolu pro lokalitu.</span><span class="sxs-lookup"><span data-stu-id="e623f-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="e623f-134">Služba Řízení</span><span class="sxs-lookup"><span data-stu-id="e623f-134">Control Service</span></span>  
 <span data-ttu-id="e623f-135">V této ukázce používáme pro komunikaci mezi Aktivátor a pracovní proces WAS WCF.</span><span class="sxs-lookup"><span data-stu-id="e623f-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="e623f-136">Služba, která se nachází v Aktivátor se nazývá řízení služby.</span><span class="sxs-lookup"><span data-stu-id="e623f-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="e623f-137">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="e623f-137">Protocol Handlers</span></span>  
 <span data-ttu-id="e623f-138">Po volání adaptér naslouchací proces `WebhostOpenListenerChannelInstance`, správce procesu WAS spustí pracovní proces, pokud není spuštěný.</span><span class="sxs-lookup"><span data-stu-id="e623f-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="e623f-139">Správce aplikace uvnitř pracovní proces pak načte UDP procesu protokol obslužné rutiny (PPH) s požadavkem pro daný `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="e623f-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="e623f-140">PPH ve voláních Zapne `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="e623f-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="e623f-141">spuštění obslužné rutiny protokolu domény aplikace UDP (ADPH).</span><span class="sxs-lookup"><span data-stu-id="e623f-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="e623f-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="e623f-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="e623f-143">Informace je zaregistrovaný v souboru Web.config následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e623f-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="e623f-144">Speciální instalační program pro tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="e623f-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="e623f-145">Tato ukázka dají pouze vytvořit a spustit na Windows Vista, Windows Server 2008 nebo Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e623f-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="e623f-146">Ke spuštění ukázky, musíte nejprve získat všechny součásti zařídit správné nastavení.</span><span class="sxs-lookup"><span data-stu-id="e623f-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="e623f-147">Ukázku nainstalujete pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="e623f-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="e623f-148">Nastavit tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="e623f-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="e623f-149">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="e623f-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="e623f-150">Sestavení projektu v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="e623f-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="e623f-151">Po kompilaci toho provádí následující operace ve fázi po sestavení:</span><span class="sxs-lookup"><span data-stu-id="e623f-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="e623f-152">Nainstaluje UDP vazba k webu "výchozí webový server".</span><span class="sxs-lookup"><span data-stu-id="e623f-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="e623f-153">Vytvoří virtuální aplikace "ServiceModelSamples" tak, aby odkazoval na fyzickou cestu: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="e623f-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="e623f-154">Umožňuje také protokol "net.udp" pro tuto virtuální aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e623f-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="e623f-155">Spuštění aplikace v uživatelském rozhraní "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="e623f-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="e623f-156">Klikněte na tlačítko **nastavení** kartu, zaškrtněte následující políčka a klikněte na **nainstalovat** k instalaci:</span><span class="sxs-lookup"><span data-stu-id="e623f-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="e623f-157">Adaptér naslouchání UDP</span><span class="sxs-lookup"><span data-stu-id="e623f-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="e623f-158">Obslužné rutiny protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="e623f-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="e623f-159">Klikněte na tlačítko **aktivace** kartě aplikaci uživatelského rozhraní "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="e623f-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="e623f-160">Klikněte na tlačítko **Start** tlačítko spustit adaptér naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="e623f-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="e623f-161">Nyní jste připraveni ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="e623f-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e623f-162">Po skončení této ukázce, je nutné spustit Cleanup.bat Odstranit vazbu net.udp z "výchozí web".</span><span class="sxs-lookup"><span data-stu-id="e623f-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="e623f-163">Využití vzorků</span><span class="sxs-lookup"><span data-stu-id="e623f-163">Sample Usage</span></span>  
 <span data-ttu-id="e623f-164">Po kompilaci existují čtyři různé binární soubory generované:</span><span class="sxs-lookup"><span data-stu-id="e623f-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="e623f-165">Client.exe: Klientský kód.</span><span class="sxs-lookup"><span data-stu-id="e623f-165">Client.exe: The client code.</span></span> <span data-ttu-id="e623f-166">Souboru App.config je zkompilován do konfiguračního souboru Client.exe.config klienta.</span><span class="sxs-lookup"><span data-stu-id="e623f-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="e623f-167">UDPActivation.dll: knihovnu, která obsahuje všechny hlavní implementace UDP.</span><span class="sxs-lookup"><span data-stu-id="e623f-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="e623f-168">Service.dll: Kód služby.</span><span class="sxs-lookup"><span data-stu-id="e623f-168">Service.dll: The service code.</span></span> <span data-ttu-id="e623f-169">K adresáři \bin sady ServiceModelSamples virtuální aplikace je zkopírován.</span><span class="sxs-lookup"><span data-stu-id="e623f-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="e623f-170">Soubor služby je Service.svc a konfigurační soubor je soubor Web.config. Po kompilaci se zkopírují do následujícího umístění: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="e623f-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="e623f-171">WasNetActivator: Aktivátor program UDP.</span><span class="sxs-lookup"><span data-stu-id="e623f-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="e623f-172">Ujistěte se, že všechny požadované údaje jsou správně nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="e623f-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="e623f-173">Následující kroky ukazují, jak ke spuštění ukázky:</span><span class="sxs-lookup"><span data-stu-id="e623f-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="e623f-174">Ujistěte se, že byly spuštěné tyto služby Windows:</span><span class="sxs-lookup"><span data-stu-id="e623f-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="e623f-175">Aktivační služba procesů Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="e623f-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="e623f-176">Internetová informační služba (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="e623f-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="e623f-177">Potom spusťte Aktivátor WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="e623f-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="e623f-178">V části **aktivace** kartu, pouze protokol **UDP**, je vybrali v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="e623f-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="e623f-179">Klikněte na tlačítko **Start** tlačítko Zahájit aktivátor.</span><span class="sxs-lookup"><span data-stu-id="e623f-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="e623f-180">Po zahájení Aktivátor můžete spustit kód klienta pomocí příkazu Client.exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="e623f-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="e623f-181">Následuje ukázkový výstup:</span><span class="sxs-lookup"><span data-stu-id="e623f-181">The following is the sample output:</span></span>  
  
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
>  <span data-ttu-id="e623f-182">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e623f-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e623f-183">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e623f-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e623f-184">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e623f-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e623f-185">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e623f-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
