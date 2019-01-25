---
title: Aktivace UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 09b208f88b456b6d98e45fc34db3857f8938cd6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715514"
---
# <a name="udp-activation"></a>Aktivace UDP
Tato ukázka je založena na [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku. Rozšiřuje [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku pro podporu proces aktivace pomocí služby Aktivace procesu Windows (WAS).  
  
 Vzorek se skládá ze tří hlavních částí:  
  
-   UDP protokolu Aktivátor, samostatným procesem, který přijímá zprávy protokolu UDP jménem aplikace, které se mají aktivovat.  
  
-   Klient, který používá vlastní přenos UDP k zasílání zpráv.  
  
-   Služba (prostředí v pracovním procesu aktivoval WAS), která přijímá zprávy přes vlastní přenos UDP.  
  
## <a name="udp-protocol-activator"></a>Aktivátor protokolu UDP  
 Aktivátor protokolu UDP je most mezi klienta WCF a služby WCF. Poskytuje datovou komunikaci prostřednictvím protokolu UDP v přenosové vrstvě. Má dvě hlavní funkce:  
  
-   BYL naslouchací proces adaptéru (LA), který spolupracuje s WAS aktivovat procesy odpověď na příchozí zprávy.  
  
-   UDP protokolu naslouchací proces, který dokáže akceptovat nezadání zpráv UDP jménem aplikace, které se mají aktivovat.  
  
 Aktivátor musí běžet jako samostatná aplikace na počítači serveru. Za normálních okolností adaptéry listener WAS (například NetTcpActivator a NetPipeActivator) jsou implementovány v dlouhotrvajících služby Windows. Ale pro zjednodušení a srozumitelnost implementuje Tato ukázka Aktivátor protokol jako samostatné aplikace.  
  
### <a name="was-listener-adapter"></a>BYL adaptér naslouchací proces  
 Adaptér naslouchání bylo pro UDP je implementován v `UdpListenerAdapter` třídy. Je modul, který komunikuje s WAS provádět aktivace aplikací pro protokol UDP. Toho dosáhnete pomocí volání následujícího rozhraní API webového hostitele:  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 Po počátečním volání `WebhostRegisterProtocol`, adaptér naslouchací proces obdrží zpětné volání `ApplicationCreated` z WAS pro všechny aplikace zaregistrovaný v souboru applicationHost.config (umístěné v % windir%\system32\inetsrv). V této ukázce jsme zpracovat pouze aplikace s protokolem UDP (s id protokolu jako "net.udp") povolena. Pokud takové implementace reagovat na změny konfigurace dynamické aplikace (například přechodu aplikace ze zakázaného na povolený okně) může v jiných implementacích zpracovávají jinak.  
  
 Při zpětném volání `ConfigManagerInitializationCompleted` přijetí, znamená to této WAS dokončil všechny oznámení pro inicializaci protokolu. Adaptér naslouchací proces je v tuto chvíli připravena na zpracování žádosti o aktivaci.  
  
 Jakmile novou žádost o prvním pro aplikaci, adaptér naslouchací proces volá `WebhostOpenListenerChannelInstance` do WAS, které spustí pracovní proces Pokud ještě není spuštěný. Potom se načtou obslužné rutiny protokolu a může začít komunikace mezi adaptérem naslouchací proces a virtuální aplikace.  
  
 Adaptér naslouchání je zaregistrován v %SystemRoot%\System32\inetsrv\ApplicationHost.config v <`listenerAdapters`> části následujícím způsobem:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Naslouchací proces protokolu  
 Naslouchací proces protokolu UDP je modul uvnitř Aktivátor protokolu, která naslouchá na koncový bod UDP jménem virtuální aplikace. Je implementován ve třídě `UdpSocketListener`. Koncový bod je vyjádřena jako `IPEndpoint` pro které je extrahován číslo portu z vazby protokolu pro lokalitu.  
  
### <a name="control-service"></a>Služba Řízení  
 V této ukázce používáme pro komunikaci mezi Aktivátor a pracovní proces WAS WCF. Služba, která se nachází v Aktivátor se nazývá řízení služby.  
  
## <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Po volání adaptér naslouchací proces `WebhostOpenListenerChannelInstance`, správce procesu WAS spustí pracovní proces, pokud není spuštěný. Správce aplikace uvnitř pracovní proces pak načte UDP procesu protokol obslužné rutiny (PPH) s požadavkem pro daný `ListenerChannelId`. PPH ve voláních Zapne `IAdphManager`.`StartAppDomainProtocolListenerChannel` spuštění obslužné rutiny protokolu domény aplikace UDP (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informace je zaregistrovaný v souboru Web.config následujícím způsobem:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Speciální instalační program pro tuto ukázku  
 Tato ukázka dají pouze vytvořit a spustit na Windows Vista, Windows Server 2008 nebo Windows 7. Ke spuštění ukázky, musíte nejprve získat všechny součásti zařídit správné nastavení. Ukázku nainstalujete pomocí následujících kroků.  
  
#### <a name="to-set-up-this-sample"></a>Nastavit tuto ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Sestavení projektu v systému Windows Vista. Po kompilaci toho provádí následující operace ve fázi po sestavení:  
  
    -   Nainstaluje UDP vazba k webu "výchozí webový server".  
  
    -   Vytvoří virtuální aplikace "ServiceModelSamples" tak, aby odkazoval na fyzickou cestu: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    -   Umožňuje také protokol "net.udp" pro tuto virtuální aplikaci.  
  
3.  Spuštění aplikace v uživatelském rozhraní "WasNetActivator.exe". Klikněte na tlačítko **nastavení** kartu, zaškrtněte následující políčka a klikněte na **nainstalovat** k instalaci:  
  
    -   Adaptér naslouchání UDP  
  
    -   Obslužné rutiny protokolu UDP  
  
4.  Klikněte na tlačítko **aktivace** kartě aplikaci uživatelského rozhraní "WasNetActivator.exe". Klikněte na tlačítko **Start** tlačítko spustit adaptér naslouchací proces. Nyní jste připraveni ke spuštění programu.  
  
    > [!NOTE]
    >  Po skončení této ukázce, je nutné spustit Cleanup.bat Odstranit vazbu net.udp z "výchozí web".  
  
## <a name="sample-usage"></a>Využití vzorků  
 Po kompilaci existují čtyři různé binární soubory generované:  
  
-   Client.exe: Klientský kód. Souboru App.config je zkompilován do konfiguračního souboru Client.exe.config klienta.  
  
-   UDPActivation.dll: knihovnu, která obsahuje všechny hlavní implementace UDP.  
  
-   Service.dll: Kód služby. K adresáři \bin sady ServiceModelSamples virtuální aplikace je zkopírován. Soubor služby je Service.svc a konfigurační soubor je soubor Web.config. Po kompilaci se zkopírují do následujícího umístění: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
-   WasNetActivator: Aktivátor program UDP.  
  
-   Ujistěte se, že všechny požadované údaje jsou správně nainstalovány. Následující kroky ukazují, jak ke spuštění ukázky:  
  
1.  Ujistěte se, že byly spuštěné tyto služby Windows:  
  
    -   Aktivační služba procesů Windows (WAS).  
  
    -   Internetová informační služba (IIS): W3SVC.  
  
2.  Potom spusťte Aktivátor WasNetActivator.exe. V části **aktivace** kartu, pouze protokol **UDP**, je vybrali v rozevíracím seznamu. Klikněte na tlačítko **Start** tlačítko Zahájit aktivátor.  
  
3.  Po zahájení Aktivátor můžete spustit kód klienta pomocí příkazu Client.exe z příkazového okna. Následuje ukázkový výstup:  
  
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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a>Viz také:
