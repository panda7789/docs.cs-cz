---
title: "Spolehlivá relace vlastních vazeb přes HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b68e5692122efbb79f8101079e721802c3dda42c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-binding-reliable-session-over-https"></a>Spolehlivá relace vlastních vazeb přes HTTPS
Tento příklad znázorňuje použití protokolu SSL zabezpečení přenosu s spolehlivé relace. Spolehlivé relace implementuje protokol WS-spolehlivé zasílání zpráv. Zabezpečené spolehlivé relace může mít podle skládání WS-zabezpečení přes spolehlivé relace. Ale v některých případech můžete místo toho použijte zabezpečení přenosu HTTP pomocí protokolu SSL.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 SSL zajistí, že jsou zabezpečené pakety sami. Je důležité si uvědomit, že se to neliší od zabezpečení spolehlivá relace WS zabezpečené konverzace pomocí.  
  
 Pokud chcete používat spolehlivé relace přes protokol HTTPS, musíte vytvořit vlastní vazby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. Vlastní vazby je vytvořený pomocí prvku vazby spolehlivé relace a [ \<httpsTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md). Vlastní vazby je následující konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Program kód v ukázce je shodná s [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) služby. Musíte vytvořit certifikát a přiřaďte ho pomocí Průvodce certifikátem webového serveru před vytváření a spouštění vzorku. Definice koncového bodu a vazba definice v souboru nastavení konfigurace povolit použití vlastní vazby, jak je znázorněno v následující ukázka konfigurace pro klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"   
                binding="customBinding"   
                bindingConfiguration="reliableSessionOverHttps"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>        
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Zadaná adresa používá schéma https://.  
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, zobrazí se výstraha zabezpečení při pokusu o přístup protokolu https: adresa, jako je například https://localhost/servicemodelsamples/service.svc z prohlížeče. Chcete-li povolit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta pro práci s testovací certifikát na místě, některé další kód byl přidán do klienta pro potlačení výstrahy zabezpečení. Tento kód a doprovodné třídy, je potřeba, není při použití provozní certifikáty.  
  
```  
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
