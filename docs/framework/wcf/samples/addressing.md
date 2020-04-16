---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 55bb30ba3df80e41986b1337f8732dd8ad3231ff
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463772"
---
# <a name="addressing"></a>Adresování
Adresování ukázka ukazuje různé aspekty a funkce adresy koncového bodu. Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V této ukázce je služba hostována samostatně. Služba i klient jsou konzolové aplikace. Služba definuje více koncových bodů pomocí kombinace relativní a absolutní adresy koncového bodu.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Konfigurační soubor služby určuje základní adresu a čtyři koncové body. Základní adresa je určena pomocí prvku add, v části service/host/baseAddresses, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 První definice koncového bodu zobrazená v následující konfiguraci ukázky určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 V tomto případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejná jako základní adresa. Skutečná adresa koncového `http://localhost:8000/servicemodelsamples/service`bodu je .
  
 Definice druhého koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Relativní adresa "test", je připojen k základní adrese. Skutečná adresa koncového `http://localhost:8000/servicemodelsamples/service/test`bodu je .
  
 Definice třetího koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Základní adresa nehraje žádnou roli v adrese. Skutečná adresa koncového `http://localhost:8001/hello/servicemodelsamples`bodu je .
  
 Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP. Základní adresa nehraje žádnou roli v adrese. Skutečná adresa koncového `net.tcp://localhost:9000/servicemodelsamples/service`bodu je .
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Klient přistupuje pouze k jednomu ze čtyř koncových bodů služby, ale všechny čtyři jsou definovány v konfiguračním souboru. Klient vybere koncový bod při vytvoření `CalculatorProxy` objektu. Změnou názvu konfigurace `CalculatorEndpoint1` `CalculatorEndpoint4`z aplikace můžete uplatnit každý z koncových bodů.  
  
 Při spuštění ukázky služba výčet adresu, název vazby a název smlouvy pro každý z jeho koncových bodů. Koncový bod výměny metadat (MEX) je pouze další koncový bod z pohledu ServiceHost, takže se zobrazí v seznamu.  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 Při spuštění klienta jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
