---
title: Spolehlivá relace s vlastními vazbami
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463929"
---
# <a name="custom-binding-reliable-session"></a>Spolehlivá relace s vlastními vazbami

Vlastní vazba je definována seřazeným seznamem samostatných prvků vazby. Tato ukázka ukazuje, jak nakonfigurovat vlastní vazby s různými prvky přenosu a kódování zpráv, zejména povolení spolehlivé relace.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a>Podrobnosti ukázky

Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv opakuje komunikaci o selhání a umožňuje zajištění doručení, jako je například doručení zpráv v pořadí, které mají být určeny. Relace udržovat stav pro klienty mezi voláními. Ukázka implementuje relace pro udržování stavu klienta a určuje záruky doručení v pořadí. Ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. Spolehlivé funkce relace jsou povoleny a konfigurovány v konfiguračních souborech aplikace pro klienta a službu.

> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.

Řazení elementů vazby je důležité při definování vlastní vazby, protože každý představuje vrstvu v zásobníku kanálu (viz [Vlastní vazby).](../../../../docs/framework/wcf/extending/custom-bindings.md)

Konfigurace služby pro ukázku je definována tak, jak je znázorněno v následujícím příkladu kódu.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

Při spuštění ve scénáři mezi počítači je nutné změnit adresu koncového bodu klienta tak, aby odrážela název hostitele služby.

Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

    > [!IMPORTANT]
    > Při spuštění klienta v konfiguraci mezi počítači, nezapomeňte nahradit `address` "localhost" v atributu `clientBaseAddress` [ \<koncového bodu>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) prvek a atribut [ \<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) s názvem příslušného počítače, jak je znázorněno v následujícím příkladu.

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
