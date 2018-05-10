---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="udp-activation"></a>Aktivace UDP
Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka. Ji rozšiřuje [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku, který se podporují procesu aktivace pomocí služby Aktivace procesů systému Windows (WAS).  
  
 Ukázkový soubor obsahuje tři hlavní části:  
  
-   UDP protokol Aktivátor, samostatný proces, který přijímá zprávy UDP jménem aplikace, které mají být aktivována.  
  
-   Klient, který používá vlastní přenosu UDP k odesílání zpráv.  
  
-   Služba (hostovaného v pracovním procesu aktivován WAS), která přijímá zprávy pomocí přenosového vlastní UDP.  
  
## <a name="udp-protocol-activator"></a>Aktivátor protokolu UDP  
 Aktivátor protokolu UDP je most mezi klienta WCF a služby WCF. Poskytuje datovou komunikaci pomocí protokolu UDP v přenosové vrstvě. Má dvě hlavní funkce:  
  
-   BYL naslouchací proces adaptér (LA), která spolupracuje s WAS aktivovat procesy v reakci na příchozí zprávy.  
  
-   Naslouchání protokolu UDP, které přijímá zprávy UDP jménem aplikace, které mají být aktivována.  
  
 Aktivátor musí používat jako samostatný program na počítači serveru. Za normálních okolností WAS naslouchací proces adaptéry (například NetTcpActivator a NetPipeActivator) se implementují ve dlouho běžící služby systému Windows. Ale pro jednoduchost a přehlednost implementuje Tato ukázka Aktivátor protokol jako samostatná aplikace.  
  
### <a name="was-listener-adapter"></a>BYL adaptér naslouchání  
 BYL adaptér naslouchání pro protokol UDP je implementována ve `UdpListenerAdapter` třídy. Je modul, který komunikuje se službou WAS aktivace aplikace pro protokol UDP. Toho dosáhnete pomocí volání rozhraní API následující webového hostitele:  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 Po počátečním volání metody `WebhostRegisterProtocol`, adaptér naslouchání obdrží zpětné volání `ApplicationCreated` z WAS pro všechny aplikace zaregistrovat v souboru applicationHost.config (umístěný ve % windir%\system32\inetsrv). V této ukázce jsme zpracovat jenom aplikace s protokolem UDP (s id protokolu jako "net.udp") povoleno. Pokud takový implementace reagovat na změny konfigurace dynamické k aplikaci (například přechodu aplikace ze zakázaného na povolený okně) může jiných implementacích zpracovávat jinak.  
  
 Při zpětné volání `ConfigManagerInitializationCompleted` přijetí, znamená to, že WAS dokončil všechny oznámení pro inicializaci protokolu. V tomto okamžiku je připraven ke zpracování žádosti o aktivaci adaptér naslouchání.  
  
 Při přijetí nového požadavku v prvním pro aplikaci, volá adaptér naslouchání `WebhostOpenListenerChannelInstance` do WAS, které spustí pracovní proces Pokud ještě není spuštěna. Pak jsou načtena obslužných rutin protokolů a začít komunikace mezi adaptér naslouchání a virtuální aplikace.  
  
 Adaptér naslouchání je zaregistrován v %SystemRoot%\System32\inetsrv\ApplicationHost.config v <`listenerAdapters`> části jako následující:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Naslouchací proces protokolu  
 Naslouchací proces protokolu UDP je modul uvnitř Aktivátor protokolu, která naslouchá na koncový bod UDP jménem virtuální aplikace. Je implementována ve třídě `UdpSocketListener`. Koncový bod je reprezentován jako `IPEndpoint` pro které je extrahován číslo portu z vazby protokolu pro lokalitu.  
  
### <a name="control-service"></a>Služba Řízení  
 V této ukázce používáme WCF pro komunikaci mezi aktivátoru a WAS pracovní proces. Služba, která se nachází v aktivační procedura je volána službu řízení.  
  
## <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Po volání adaptér naslouchání `WebhostOpenListenerChannelInstance`, správce proces WAS spustí pracovní proces, pokud není spuštěna. Potom Správce aplikací uvnitř pracovního procesu se načte UDP proces protokol obslužné rutiny (PPH) s požadavkem, pro který `ListenerChannelId`. PPH ve voláních oplátku `IAdphManager`.`StartAppDomainProtocolListenerChannel` Spustit obslužnou rutinu pro protokol AppDomain UDP (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informace je zaregistrován v souboru Web.config následujícím způsobem:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Speciální nastavení pro tuto ukázku  
 Tato ukázka můžete pouze vytvořené a spustit v systému Windows Vista, Windows Server 2008 nebo Windows 7. Pokud chcete spustit ukázku, musíte nejprve získat všechny součásti správně nastavené. Ukázku nainstalujete pomocí následujících kroků.  
  
#### <a name="to-set-up-this-sample"></a>Nastavení této ukázky  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Sestavení projektu v systému Windows Vista. Po sestavení také provede následující operace ve fázi po sestavení:  
  
    -   Nainstaluje UDP vazbu k webu "Default Web Site".  
  
    -   Vytvoří virtuální aplikace "ServiceModelSamples" tak, aby odkazoval na fyzickou cestu: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    -   Umožňuje také protokol "net.udp" pro tuto virtuální aplikaci.  
  
3.  Spuštění aplikace v uživatelském rozhraní "WasNetActivator.exe". Klikněte na tlačítko **instalace** kartě, zaškrtněte následující zaškrtávací políčka a pak klikněte na tlačítko **nainstalovat** k instalaci:  
  
    -   Adaptér naslouchání UDP  
  
    -   Obslužné rutiny protokolu UDP  
  
4.  Klikněte **aktivace** uživatelské rozhraní aplikace "WasNetActivator.exe". Klikněte **spustit** tlačítko spusťte adaptér naslouchání. Nyní jste připraveni ke spuštění programu.  
  
    > [!NOTE]
    >  Po skončení této ukázce, je nutné spustit Cleanup.bat odebrat vazby net.udp z "výchozí web".  
  
## <a name="sample-usage"></a>Využití vzorků  
 Po sestavení existují čtyři různé binární soubory generované:  
  
-   Client.exe: Kód klienta. Souboru App.config se zkompiluje do konfiguračního souboru klienta Client.exe.config.  
  
-   UDPActivation.dll: knihovnu, která obsahuje všechny hlavní implementace UDP.  
  
-   Service.dll: Kódu služby. Je zkopírován do adresáře \bin ServiceModelSamples virtuální aplikace. Soubor služby je Service.svc a konfigurační soubor je soubor Web.config. Po sestavení, se zkopírují do následujícího umístění: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
-   WasNetActivator: UDP Aktivátor program.  
  
-   Ujistěte se, zda všechny požadované součásti jsou nainstalovány správně. Následující kroky ukazují, jak spustit ukázku:  
  
1.  Ujistěte se, že byly spuštěny následující služby systému Windows:  
  
    -   Aktivační služba procesů systému Windows (WAS).  
  
    -   Internetová informační služba (IIS): W3SVC.  
  
2.  Spusťte aktivátoru WasNetActivator.exe. V části **aktivace** kartě, bude jediným používaným protokolem, **UDP**, je vybraný v rozevíracím seznamu. Klikněte na tlačítko **spustit** tlačítko Spustit aktivační procedura.  
  
3.  Jakmile začne aktivátoru, můžete spustit kód klienta spuštěním Client.exe z příkazového okna. Následuje příklad výstupu:  
  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a>Viz také
