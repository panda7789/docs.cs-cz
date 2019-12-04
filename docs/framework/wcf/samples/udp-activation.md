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
# <a name="udp-activation"></a>Aktivace UDP
Tato ukázka je založena na ukázce [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) . Rozšiřuje ukázku [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) , aby podporovala aktivaci procesu pomocí aktivační služby procesů systému Windows (WAS).  
  
 Ukázka se skládá ze tří hlavních částí:  
  
- Aktivátor protokolu UDP, samostatný proces, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.  
  
- Klient, který pro posílání zpráv používá vlastní přenos UDP  
  
- Služba (hostovaná v pracovním procesu byla aktivována), která přijímá zprávy přes vlastní přenos UDP.  
  
## <a name="udp-protocol-activator"></a>Aktivační procedury protokolu UDP  
 Aktivátor protokolu UDP je most mezi klientem WCF a službou WCF. Poskytuje datovou komunikaci prostřednictvím protokolu UDP na transportní vrstvě. Má dvě hlavní funkce:  
  
- WAS adaptér naslouchacího procesu (LA), který spolupracuje s nástrojem při aktivaci procesů v reakci na příchozí zprávy.  
  
- Naslouchací proces protokolu UDP, který přijímá zprávy UDP jménem aplikací, které mají být aktivovány.  
  
 Aktivátor musí být spuštěn jako samostatný program na serverovém počítači. Obvykle se adaptéry naslouchacího procesu (například službu NetTcpActivator a NetPipeActivator) implementují v dlouhotrvajících službách systému Windows. Pro zjednodušení a přehlednost však tato ukázka implementuje jako samostatnou aplikaci Aktivátor protokolu.  
  
### <a name="was-listener-adapter"></a>Adaptér naslouchacího procesu  
 Adaptér naslouchání pro protokol UDP je implementován ve třídě `UdpListenerAdapter`. Je to modul, který spolupracuje s nástrojem k provedení aktivace aplikace pro protokol UDP. Toho dosáhnete voláním následujících rozhraní API webhosta:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Po počátečním volání `WebhostRegisterProtocol`obdrží adaptér naslouchacího procesu zpětné volání `ApplicationCreated` z programu pro všechny aplikace zaregistrované v souboru applicationHost. config (nacházející se v%windir%\system32\inetsrv). V této ukázce zpracujeme jenom aplikace s protokolem UDP (s ID protokolu, který je povolený jako NET. UDP). Jiné implementace mohou nakládat jinak, pokud takové implementace reagují na změny dynamické konfigurace v aplikaci (například přechod aplikace z zakázáno na povoleno).  
  
 Když je přijat `ConfigManagerInitializationCompleted` zpětného volání, znamená to, že byla dokončena všechna oznámení pro inicializaci protokolu. V tuto chvíli je adaptér naslouchacího procesu připravený zpracovat žádosti o aktivaci.  
  
 Při prvním přihlášení nové žádosti pro aplikaci zavolá adaptér naslouchacího procesu `WebhostOpenListenerChannelInstance`, který spustí pracovní proces, pokud ještě nebyl spuštěn. Pak se načtou obslužné rutiny protokolu a komunikace mezi adaptérem naslouchacího procesu a virtuální aplikací může začít.  
  
 Adaptér naslouchacího procesu je zaregistrován v%SystemRoot%\System32\inetsrv\ApplicationHost.config`listenerAdapters`< v části > následujícím způsobem:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Naslouchací proces protokolu  
 Naslouchací proces protokolu UDP je modul uvnitř aktivační procedury protokolu, která naslouchá za koncovým bodem UDP jménem virtuální aplikace. Je implementována ve třídě `UdpSocketListener`. Koncový bod je reprezentován jako `IPEndpoint`, pro který je číslo portu extrahováno z vazby protokolu pro lokalitu.  
  
### <a name="control-service"></a>Řídicí služba  
 V této ukázce používáme WCF ke komunikaci mezi aktivátorem a pracovním procesem WAS. Služba, která se nachází v Activator, se nazývá řídicí služba.  
  
## <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Jakmile adaptér naslouchacího procesu zavolá `WebhostOpenListenerChannelInstance`, měl by správce procesu pracovní proces spustit, pokud není spuštěný. Správce aplikací v pracovním procesu potom načte popisovač protokolu UDP procesu (PPH) s požadavkem na tento `ListenerChannelId`. PPH v zapnete volání `IAdphManager`.`StartAppDomainProtocolListenerChannel` pro spuštění obslužné rutiny protokolu UDP AppDomain (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informace jsou registrovány v souboru Web. config následujícím způsobem:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Speciální nastavení pro tuto ukázku  
 Tato ukázka se dá sestavit a spustit jenom v systémech Windows Vista, Windows Server 2008 nebo Windows 7. Chcete-li spustit ukázku, je nutné nejprve načíst všechny součásti nastavené správně. Ukázku nainstalujete pomocí následujícího postupu.  
  
#### <a name="to-set-up-this-sample"></a>Nastavení této ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Sestavte projekt v systému Windows Vista. Po kompilaci provede také následující operace ve fázi po sestavení:  
  
    - Nainstaluje vazbu UDP na web s názvem Default Web site.  
  
    - Vytvoří virtuální aplikaci "ServiceModelSamples", která bude ukazovat na fyzickou cestu: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Pro tuto virtuální aplikaci taky povoluje protokol "NET. UDP".  
  
3. Spusťte aplikaci uživatelského rozhraní "WasNetActivator. exe". Klikněte na kartu **Nastavení** , zaškrtněte následující políčka a kliknutím na tlačítko **nainstalovat** je nainstalujte:  
  
    - Adaptér naslouchacího procesu UDP  
  
    - Obslužné rutiny protokolu UDP  
  
4. Klikněte na kartu **Aktivace** aplikace uživatelského rozhraní "WasNetActivator. exe". Kliknutím na tlačítko **Spustit** spusťte adaptér naslouchacího procesu. Nyní jste připraveni spustit program.  
  
    > [!NOTE]
    > Až budete s touto ukázkou hotovi, je nutné spustit nástroj CleanUp. bat a odebrat vazbu NET. UDP z webu s názvem Default Web site.  
  
## <a name="sample-usage"></a>Ukázkové použití  
 Po kompilaci jsou vygenerovány čtyři různé binární soubory:  
  
- Client. exe: klientský kód. Soubor App. config je zkompilován do konfiguračního souboru Client. exe. config.  
  
- UDPActivation. dll: knihovna, která obsahuje všechny hlavní implementace protokolu UDP.  
  
- Service. dll: kód služby. Tato kopie se zkopíruje do adresáře \Bin virtuální aplikace ServiceModelSamples. Soubor služby je Service. svc a konfigurační soubor je web. config. Po kompilaci jsou zkopírovány do následujícího umístění:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: program UDP Activator.  
  
- Ujistěte se, že jsou správně nainstalovány všechny požadované součásti. Následující kroky ukazují, jak spustit ukázku:  
  
1. Zajistěte, aby byly spuštěny následující služby systému Windows:  
  
    - Aktivační služba procesů systému Windows (WAS).  
  
    - Internetová informační služba (IIS): W3SVC.  
  
2. Poté spusťte Activator, WasNetActivator. exe. Na kartě **Aktivace** je v rozevíracím seznamu vybrán jediný protokol, **UDP**. Kliknutím na tlačítko **Spustit** spusťte aktivátor.  
  
3. Po spuštění aktivátoru můžete spustit kód klienta spuštěním souboru Client. exe z příkazového okna. Následuje ukázkový výstup:  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
