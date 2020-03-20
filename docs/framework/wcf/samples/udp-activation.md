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
# <a name="udp-activation"></a>Aktivace UDP
Tato ukázka je založena na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku. Rozšiřuje [transport: Ukázka UDP](../../../../docs/framework/wcf/samples/transport-udp.md) pro podporu aktivace procesu pomocí služby aktivace procesů systému Windows (WAS).  
  
 Vzorek se skládá ze tří hlavních kusů:  
  
- Aktivátor protokolu UDP, samostatný proces, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.  
  
- Klient, který používá vlastní přenos UDP k odesílání zpráv.  
  
- Služba (hostovaná v pracovním procesu aktivovaném službou WAS), která přijímá zprávy prostřednictvím vlastního přenosu UDP.  
  
## <a name="udp-protocol-activator"></a>Aktivátor protokolu UDP  
 Aktivátor protokolu UDP je most mezi klientem WCF a službou WCF. Poskytuje datovou komunikaci prostřednictvím protokolu UDP na transportní vrstvě. Má dvě hlavní funkce:  
  
- WAS Listener Adapter (LA), který spolupracuje s WAS na aktivaci procesů v reakci na příchozí zprávy.  
  
- Naslouchací proces protokolu UDP, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.  
  
 Aktivátor musí být spuštěn jako samostatný program v počítači serveru. Za normálních okolností was naslouchací proces adaptéry (například NetTcpActivator a NetPipeActivator) jsou implementovány v dlouhotrvající služby systému Windows. Pro jednoduchost a srozumitelnost však tato ukázka implementuje aktivátor protokolu jako samostatnou aplikaci.  
  
### <a name="was-listener-adapter"></a>Adaptér naslouchacího procesu SLUŽBY  
 Adaptér naslouchacího procesu `UdpListenerAdapter` WAS pro UDP je implementován ve třídě. Jedná se o modul, který spolupracuje s WAS k provedení aktivace aplikace pro protokol UDP. Toho je dosaženo voláním následujícíwebhost API:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Po počátečním volání `WebhostRegisterProtocol`adaptér posluchače `ApplicationCreated` přijme zpětné volání od služby WAS pro všechny aplikace registrované v souboru applicationHost.config (umístěnév %windir%\system32\inetsrv). V této ukázce zpracováváme pouze aplikace s protokolem UDP (s id protokolu jako "net.udp") povoleno. Jiné implementace to mohou zpracovat jinak, pokud tyto implementace reagují na změny dynamické konfigurace aplikace (například přechod aplikace ze zakázané na povolenou).  
  
 Po přijetí `ConfigManagerInitializationCompleted` zpětného volání označuje, že služba WAS dokončila všechna oznámení pro inicializaci protokolu. V tomto okamžiku je adaptér naslouchací proces připraven ke zpracování požadavků na aktivaci.  
  
 Při prvním požadavku na aplikaci přijde nový požadavek, adaptér naslouchacího procesu volá do služby `WebhostOpenListenerChannelInstance` WAS, která spustí pracovní proces, pokud ještě není spuštěna. Poté jsou načteny obslužné rutiny protokolu a komunikace mezi adaptérem naslouchacího procesu a virtuální aplikací může být zahájena.  
  
 Adaptér naslouchacího procesu je registrován v části %SystemRoot%\System32\inetsrv\ApplicationHost.config v části <`listenerAdapters`> následujícím způsobem:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Naslouchací proces protokolu  
 Naslouchací proces protokolu UDP je modul uvnitř aktivátoru protokolu, který naslouchá koncovému bodu UDP jménem virtuální aplikace. Je implementována `UdpSocketListener`ve třídě . Koncový bod je `IPEndpoint` reprezentován jako pro které je číslo portu extrahovánzující z vazby protokolu pro lokalitu.  
  
### <a name="control-service"></a>Kontrolní služba  
 V této ukázce používáme WCF ke komunikaci mezi aktivátorem a pracovníproces WAS. Služba, která je umístěna v aktivátoru se nazývá řídicí služba.  
  
## <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Po volání `WebhostOpenListenerChannelInstance`adaptéru naslouchací proces , správce procesu WAS spustí pracovní proces, pokud není spuštěn. Správce aplikací uvnitř pracovního procesu pak načte obslužnou rutinu `ListenerChannelId`protokolu procesu UDP (PPH) s požadavkem na tento . PPH v zase `IAdphManager`volání .`StartAppDomainProtocolListenerChannel` spuštění obslužné rutiny protokolu UDP AppDomain Protocol (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportKonfigurace  
 Informace jsou registrovány v souboru Web.config následujícím způsobem:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Speciální nastavení pro tuto ukázku  
 Tuto ukázku lze sestavit a spustit pouze v systémech Windows Vista, Windows Server 2008 nebo Windows 7. Chcete-li spustit ukázku, musíte nejprve získat všechny součásti správně nastavit. K instalaci ukázky použijte následující kroky.  
  
#### <a name="to-set-up-this-sample"></a>Chcete-li nastavit tuto ukázku  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Vytvořte projekt v systému Windows Vista. Po kompilaci také provádí následující operace ve fázi po sestavení:  
  
    - Nainstaluje vazbu UDP na web "Výchozí web".  
  
    - Vytvoří virtuální aplikaci ServiceModelSamples tak, aby ukazovala na fyzickou cestu: %SystemDrive%\inetpub\wwwroot\servicemodelsamples.Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Umožňuje také protokol net.udp pro tuto virtuální aplikaci.  
  
3. Spusťte aplikaci uživatelského rozhraní "WasNetActivator.exe". Klikněte na kartu **Instalace,** zaškrtněte následující políčka a potom je nainstalujte kliknutím na **Instalovat:**  
  
    - Adaptér naslouchacího procesu UDP  
  
    - Obslužné rutiny protokolu UDP  
  
4. Klikněte na kartu **Aktivace** aplikace uživatelského rozhraní "WasNetActivator.exe". Klepnutím na tlačítko **Start** spusťte adaptér naslouchacího procesu. Nyní jste připraveni spustit program.  
  
    > [!NOTE]
    > Po dokončení této ukázky je nutné spustit soubor Cleanup.bat a odebrat vazbu net.udp z "Výchozího webu".  
  
## <a name="sample-usage"></a>Ukázka použití  
 Po kompilaci jsou generovány čtyři různé binární soubory:  
  
- Client.exe: Kód klienta. Nástroj App.config je zkompilován do konfiguračního souboru klienta Client.exe.config.  
  
- UDPActivation.dll: knihovna, která obsahuje všechny hlavní implementace UDP.  
  
- Service.dll: Kód služby. Tato možnost je zkopírována do adresáře \bin virtuální aplikace ServiceModelSamples. Soubor služby je Service.svc a konfigurační soubor je Web.config. Po kompilaci jsou zkopírovány do následujícího umístění: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: Aktivátor UDP program.  
  
- Ujistěte se, že jsou všechny požadované kusy nainstalovány správně. Následující kroky ukazují, jak spustit ukázku:  
  
1. Ujistěte se, že byly spuštěny následující služby systému Windows:  
  
    - Služba aktivace procesů systému Windows (WAS).  
  
    - Internetové informační služby (IIS): W3SVC.  
  
2. Potom spusťte aktivátor WasNetActivator.exe. Na kartě **Aktivace** je v rozevíracím seznamu vybrán pouze protokol **UDP**. Kliknutím na tlačítko **Start** spusťte aktivátor.  
  
3. Po spuštění aktivátoru můžete spustit kód klienta spuštěním Client.exe z příkazového okna. Ukázkový výstup je následující:  
  
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
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
