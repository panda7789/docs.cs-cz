---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 13444ab1be440c8e1a5f945cd512afa33772ea57
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044643"
---
# <a name="udp-activation"></a>Aktivace UDP
Tato ukázka je založena na [přenosu: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP Rozšiřuje [přenos: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP pro podporu aktivace procesu pomocí aktivační služby procesů systému Windows (WAS).  
  
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
 Adaptér naslouchání pro protokol UDP je implementován ve `UdpListenerAdapter` třídě. Je to modul, který spolupracuje s nástrojem k provedení aktivace aplikace pro protokol UDP. Toho dosáhnete voláním následujících rozhraní API webhosta:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Po počátečním `WebhostRegisterProtocol`volání přijme adaptér naslouchacího procesu zpětné volání `ApplicationCreated` pro všechny aplikace zaregistrované v souboru ApplicationHost. config (nacházející se v%windir%\system32\inetsrv). V této ukázce zpracujeme jenom aplikace s protokolem UDP (s ID protokolu, který je povolený jako NET. UDP). Jiné implementace mohou nakládat jinak, pokud takové implementace reagují na změny dynamické konfigurace v aplikaci (například přechod aplikace z zakázáno na povoleno).  
  
 Po přijetí zpětného volání `ConfigManagerInitializationCompleted` indikuje, že bylo dokončeno všech oznámení pro inicializaci protokolu. V tuto chvíli je adaptér naslouchacího procesu připravený zpracovat žádosti o aktivaci.  
  
 Při prvním přihlášení nové žádosti pro aplikaci zavolá `WebhostOpenListenerChannelInstance` adaptér naslouchacího procesu do was, který spustí pracovní proces, pokud ještě není spuštěný. Pak se načtou obslužné rutiny protokolu a komunikace mezi adaptérem naslouchacího procesu a virtuální aplikací může začít.  
  
 Adaptér naslouchacího procesu je zaregistrován v%SystemRoot%\System32\inetsrv\ApplicationHost.config > oddílu <`listenerAdapters`následujícím způsobem:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Naslouchací proces protokolu  
 Naslouchací proces protokolu UDP je modul uvnitř aktivační procedury protokolu, která naslouchá za koncovým bodem UDP jménem virtuální aplikace. Je implementován ve třídě `UdpSocketListener`. Koncový bod je reprezentován, `IPEndpoint` pro které se číslo portu extrahuje z vazby protokolu pro lokalitu.  
  
### <a name="control-service"></a>Řídicí služba  
 V této ukázce používáme WCF ke komunikaci mezi aktivátorem a pracovním procesem WAS. Služba, která se nachází v Activator, se nazývá řídicí služba.  
  
## <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Po volání `WebhostOpenListenerChannelInstance`adaptéru naslouchacího procesu spustil správce procesů pracovní proces, pokud není spuštěn. Správce aplikací v rámci pracovního procesu potom načte obslužnou rutinu procesu protokolu UDP (PPH) s požadavkem na to `ListenerChannelId`. PPH v zapíná volání `IAdphManager`.`StartAppDomainProtocolListenerChannel` pro spuštění obslužné rutiny protokolu UDP AppDomain (ADPH).  
  
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
  
    ```  
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
  
- Client. exe: Kód klienta. Soubor App. config je zkompilován do konfiguračního souboru Client. exe. config.  
  
- UDPActivation. dll: knihovna, která obsahuje všechny hlavní implementace protokolu UDP.  
  
- Service.dll: Kód služby. Tato kopie se zkopíruje do adresáře \Bin virtuální aplikace ServiceModelSamples. Soubor služby je Service. svc a konfigurační soubor je web. config. Po kompilaci jsou zkopírovány do následujícího umístění:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: Program UDP Activator.  
  
- Ujistěte se, že jsou správně nainstalovány všechny požadované součásti. Následující kroky ukazují, jak spustit ukázku:  
  
1. Zajistěte, aby byly spuštěny následující služby systému Windows:  
  
    - Aktivační služba procesů systému Windows (WAS).  
  
    - Internetová informační služba (IIS): SLUŽBU.  
  
2. Poté spusťte Activator, WasNetActivator. exe. Na kartě **Aktivace** je v rozevíracím seznamu vybrán jediný protokol, **UDP**. Kliknutím na tlačítko **Spustit** spusťte aktivátor.  
  
3. Po spuštění aktivátoru můžete spustit kód klienta spuštěním souboru Client. exe z příkazového okna. Následuje ukázkový výstup:  
  
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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
