---
title: Spolehlivá relace vlastních vazeb přes HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183877"
---
# <a name="custom-binding-reliable-session-over-https"></a>Spolehlivá relace vlastních vazeb přes HTTPS
Tato ukázka ukazuje použití zabezpečení přenosu SSL se spolehlivými relacemi. Spolehlivé relace implementuje ws spolehlivé zasílání zpráv protokol. Můžete mít zabezpečené spolehlivé relace tím, že skládá WS-Security přes spolehlivé relace. Někdy se však můžete rozhodnout místo toho použít zabezpečení přenosu HTTP s protokolem SSL.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Podrobnosti ukázky  
 SSL zajišťuje, že pakety samotné jsou zabezpečeny. Je důležité si uvědomit, že se liší od zabezpečení spolehlivé relace pomocí konverzace WS Zabezpečené.  
  
 Chcete-li použít spolehlivé relace přes protokol HTTPS, musíte vytvořit vlastní vazbu. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. Vlastní vazba je vytvořena pomocí elementu vazby spolehlivé relace a [ \<>httpsTransport ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md). Následující konfigurace je vlastní vazby.  
  
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
  
 Kód programu v ukázce je shodný se službou [Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Před sestavením a spuštěním ukázky je nutné vytvořit certifikát a přiřadit jej pomocí Průvodce certifikátem webového serveru. Definice koncového bodu a definice vazby v nastavení konfiguračního souboru umožňují použití vlastní vazby, jak je znázorněno v následující ukázkové konfiguraci pro klienta.  
  
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
  
 Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí programu Makecert.exe, zobrazí se při pokusu o přístup k adrese https: adresa, například https://localhost/servicemodelsamples/service.svc, z prohlížeče. Chcete-li umožnit klientovi Windows Communication Foundation (WCF) pracovat s certifikátem test na místě, některé další kód byl přidán do klienta potlačit výstrahu zabezpečení. Tento kód a doprovodná třída se nevyžadují při použití produkčních certifikátů.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Zkontrolujte, zda jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
