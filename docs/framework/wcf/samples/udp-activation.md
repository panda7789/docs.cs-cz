---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 0f5d07e65abc0b29989834aff496f7c27ea557b5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715811"
---
# <a name="udp-activation"></a><span data-ttu-id="03da5-102">Aktivace UDP</span><span class="sxs-lookup"><span data-stu-id="03da5-102">UDP Activation</span></span>
<span data-ttu-id="03da5-103">Tato ukázka je založena na ukázce [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="03da5-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="03da5-104">Rozšiřuje ukázku [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) , aby podporovala aktivaci procesu pomocí aktivační služby procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="03da5-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="03da5-105">Ukázka se skládá ze tří hlavních částí:</span><span class="sxs-lookup"><span data-stu-id="03da5-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="03da5-106">Aktivátor protokolu UDP, samostatný proces, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.</span><span class="sxs-lookup"><span data-stu-id="03da5-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="03da5-107">Klient, který pro posílání zpráv používá vlastní přenos UDP</span><span class="sxs-lookup"><span data-stu-id="03da5-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="03da5-108">Služba (hostovaná v pracovním procesu byla aktivována), která přijímá zprávy přes vlastní přenos UDP.</span><span class="sxs-lookup"><span data-stu-id="03da5-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="03da5-109">Aktivační procedury protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="03da5-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="03da5-110">Aktivátor protokolu UDP je most mezi klientem WCF a službou WCF.</span><span class="sxs-lookup"><span data-stu-id="03da5-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="03da5-111">Poskytuje datovou komunikaci prostřednictvím protokolu UDP na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="03da5-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="03da5-112">Má dvě hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="03da5-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="03da5-113">WAS adaptér naslouchacího procesu (LA), který spolupracuje s nástrojem při aktivaci procesů v reakci na příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="03da5-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="03da5-114">Naslouchací proces protokolu UDP, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.</span><span class="sxs-lookup"><span data-stu-id="03da5-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="03da5-115">Aktivátor musí být spuštěn jako samostatný program na serverovém počítači.</span><span class="sxs-lookup"><span data-stu-id="03da5-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="03da5-116">Obvykle se adaptéry naslouchacího procesu (například službu NetTcpActivator a NetPipeActivator) implementují v dlouhotrvajících službách systému Windows.</span><span class="sxs-lookup"><span data-stu-id="03da5-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="03da5-117">Pro zjednodušení a přehlednost však tato ukázka implementuje jako samostatnou aplikaci Aktivátor protokolu.</span><span class="sxs-lookup"><span data-stu-id="03da5-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="03da5-118">Adaptér naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="03da5-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="03da5-119">Adaptér naslouchání pro protokol UDP je implementován ve třídě `UdpListenerAdapter`.</span><span class="sxs-lookup"><span data-stu-id="03da5-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="03da5-120">Je to modul, který spolupracuje s nástrojem k provedení aktivace aplikace pro protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="03da5-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="03da5-121">Toho dosáhnete voláním následujících rozhraní API webhosta:</span><span class="sxs-lookup"><span data-stu-id="03da5-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="03da5-122">Po počátečním volání `WebhostRegisterProtocol`obdrží adaptér naslouchacího procesu zpětné volání `ApplicationCreated` z programu pro všechny aplikace zaregistrované v souboru applicationHost. config (nacházející se v%windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="03da5-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="03da5-123">V této ukázce zpracujeme jenom aplikace s protokolem UDP (s ID protokolu, který je povolený jako NET. UDP).</span><span class="sxs-lookup"><span data-stu-id="03da5-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="03da5-124">Jiné implementace mohou nakládat jinak, pokud takové implementace reagují na změny dynamické konfigurace v aplikaci (například přechod aplikace z zakázáno na povoleno).</span><span class="sxs-lookup"><span data-stu-id="03da5-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="03da5-125">Když je přijat `ConfigManagerInitializationCompleted` zpětného volání, znamená to, že byla dokončena všechna oznámení pro inicializaci protokolu.</span><span class="sxs-lookup"><span data-stu-id="03da5-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="03da5-126">V tuto chvíli je adaptér naslouchacího procesu připravený zpracovat žádosti o aktivaci.</span><span class="sxs-lookup"><span data-stu-id="03da5-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="03da5-127">Při prvním přihlášení nové žádosti pro aplikaci zavolá adaptér naslouchacího procesu `WebhostOpenListenerChannelInstance`, který spustí pracovní proces, pokud ještě nebyl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="03da5-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="03da5-128">Pak se načtou obslužné rutiny protokolu a komunikace mezi adaptérem naslouchacího procesu a virtuální aplikací může začít.</span><span class="sxs-lookup"><span data-stu-id="03da5-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="03da5-129">Adaptér naslouchacího procesu je zaregistrován v%SystemRoot%\System32\inetsrv\ApplicationHost.config`listenerAdapters`< v části > následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="03da5-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="03da5-130">Naslouchací proces protokolu</span><span class="sxs-lookup"><span data-stu-id="03da5-130">Protocol Listener</span></span>  
 <span data-ttu-id="03da5-131">Naslouchací proces protokolu UDP je modul uvnitř aktivační procedury protokolu, která naslouchá za koncovým bodem UDP jménem virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="03da5-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="03da5-132">Je implementována ve třídě `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="03da5-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="03da5-133">Koncový bod je reprezentován jako `IPEndpoint`, pro který je číslo portu extrahováno z vazby protokolu pro lokalitu.</span><span class="sxs-lookup"><span data-stu-id="03da5-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="03da5-134">Řídicí služba</span><span class="sxs-lookup"><span data-stu-id="03da5-134">Control Service</span></span>  
 <span data-ttu-id="03da5-135">V této ukázce používáme WCF ke komunikaci mezi aktivátorem a pracovním procesem WAS.</span><span class="sxs-lookup"><span data-stu-id="03da5-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="03da5-136">Služba, která se nachází v Activator, se nazývá řídicí služba.</span><span class="sxs-lookup"><span data-stu-id="03da5-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="03da5-137">Obslužné rutiny protokolu</span><span class="sxs-lookup"><span data-stu-id="03da5-137">Protocol Handlers</span></span>  
 <span data-ttu-id="03da5-138">Jakmile adaptér naslouchacího procesu zavolá `WebhostOpenListenerChannelInstance`, měl by správce procesu pracovní proces spustit, pokud není spuštěný.</span><span class="sxs-lookup"><span data-stu-id="03da5-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="03da5-139">Správce aplikací v pracovním procesu potom načte popisovač protokolu UDP procesu (PPH) s požadavkem na tento `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="03da5-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="03da5-140">PPH v zapnete volání `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="03da5-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="03da5-141">pro spuštění obslužné rutiny protokolu UDP AppDomain (ADPH).</span><span class="sxs-lookup"><span data-stu-id="03da5-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="03da5-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="03da5-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="03da5-143">Informace jsou registrovány v souboru Web. config následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="03da5-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="03da5-144">Speciální nastavení pro tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="03da5-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="03da5-145">Tato ukázka se dá sestavit a spustit jenom v systémech Windows Vista, Windows Server 2008 nebo Windows 7.</span><span class="sxs-lookup"><span data-stu-id="03da5-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="03da5-146">Chcete-li spustit ukázku, je nutné nejprve načíst všechny součásti nastavené správně.</span><span class="sxs-lookup"><span data-stu-id="03da5-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="03da5-147">Ukázku nainstalujete pomocí následujícího postupu.</span><span class="sxs-lookup"><span data-stu-id="03da5-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="03da5-148">Nastavení této ukázky</span><span class="sxs-lookup"><span data-stu-id="03da5-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="03da5-149">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="03da5-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="03da5-150">Sestavte projekt v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="03da5-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="03da5-151">Po kompilaci provede také následující operace ve fázi po sestavení:</span><span class="sxs-lookup"><span data-stu-id="03da5-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="03da5-152">Nainstaluje vazbu UDP na web s názvem Default Web site.</span><span class="sxs-lookup"><span data-stu-id="03da5-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="03da5-153">Vytvoří virtuální aplikaci "ServiceModelSamples", která bude ukazovat na fyzickou cestu: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="03da5-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="03da5-154">Pro tuto virtuální aplikaci taky povoluje protokol "NET. UDP".</span><span class="sxs-lookup"><span data-stu-id="03da5-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="03da5-155">Spusťte aplikaci uživatelského rozhraní "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="03da5-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="03da5-156">Klikněte na kartu **Nastavení** , zaškrtněte následující políčka a kliknutím na tlačítko **nainstalovat** je nainstalujte:</span><span class="sxs-lookup"><span data-stu-id="03da5-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="03da5-157">Adaptér naslouchacího procesu UDP</span><span class="sxs-lookup"><span data-stu-id="03da5-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="03da5-158">Obslužné rutiny protokolu UDP</span><span class="sxs-lookup"><span data-stu-id="03da5-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="03da5-159">Klikněte na kartu **Aktivace** aplikace uživatelského rozhraní "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="03da5-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="03da5-160">Kliknutím na tlačítko **Spustit** spusťte adaptér naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="03da5-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="03da5-161">Nyní jste připraveni spustit program.</span><span class="sxs-lookup"><span data-stu-id="03da5-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="03da5-162">Až budete s touto ukázkou hotovi, je nutné spustit nástroj CleanUp. bat a odebrat vazbu NET. UDP z webu s názvem Default Web site.</span><span class="sxs-lookup"><span data-stu-id="03da5-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="03da5-163">Ukázkové použití</span><span class="sxs-lookup"><span data-stu-id="03da5-163">Sample Usage</span></span>  
 <span data-ttu-id="03da5-164">Po kompilaci jsou vygenerovány čtyři různé binární soubory:</span><span class="sxs-lookup"><span data-stu-id="03da5-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="03da5-165">Client. exe: klientský kód.</span><span class="sxs-lookup"><span data-stu-id="03da5-165">Client.exe: The client code.</span></span> <span data-ttu-id="03da5-166">Soubor App. config je zkompilován do konfiguračního souboru Client. exe. config.</span><span class="sxs-lookup"><span data-stu-id="03da5-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="03da5-167">UDPActivation. dll: knihovna, která obsahuje všechny hlavní implementace protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="03da5-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="03da5-168">Service. dll: kód služby.</span><span class="sxs-lookup"><span data-stu-id="03da5-168">Service.dll: The service code.</span></span> <span data-ttu-id="03da5-169">Tato kopie se zkopíruje do adresáře \Bin virtuální aplikace ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="03da5-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="03da5-170">Soubor služby je Service. svc a konfigurační soubor je web. config. Po kompilaci jsou zkopírovány do následujícího umístění:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="03da5-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="03da5-171">WasNetActivator: program UDP Activator.</span><span class="sxs-lookup"><span data-stu-id="03da5-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="03da5-172">Ujistěte se, že jsou správně nainstalovány všechny požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="03da5-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="03da5-173">Následující kroky ukazují, jak spustit ukázku:</span><span class="sxs-lookup"><span data-stu-id="03da5-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="03da5-174">Zajistěte, aby byly spuštěny následující služby systému Windows:</span><span class="sxs-lookup"><span data-stu-id="03da5-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="03da5-175">Aktivační služba procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="03da5-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="03da5-176">Internetová informační služba (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="03da5-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="03da5-177">Poté spusťte Activator, WasNetActivator. exe.</span><span class="sxs-lookup"><span data-stu-id="03da5-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="03da5-178">Na kartě **Aktivace** je v rozevíracím seznamu vybrán jediný protokol, **UDP**.</span><span class="sxs-lookup"><span data-stu-id="03da5-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="03da5-179">Kliknutím na tlačítko **Spustit** spusťte aktivátor.</span><span class="sxs-lookup"><span data-stu-id="03da5-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="03da5-180">Po spuštění aktivátoru můžete spustit kód klienta spuštěním souboru Client. exe z příkazového okna.</span><span class="sxs-lookup"><span data-stu-id="03da5-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="03da5-181">Následuje ukázkový výstup:</span><span class="sxs-lookup"><span data-stu-id="03da5-181">The following is the sample output:</span></span>  
  
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
> <span data-ttu-id="03da5-182">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="03da5-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03da5-183">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="03da5-183">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="03da5-184">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="03da5-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03da5-185">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="03da5-185">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
