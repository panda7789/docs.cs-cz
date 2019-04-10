---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 62d1d4206bd0595ac84cb5ec6942f914a89fbaae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221323"
---
# <a name="addressing"></a>Adresování
Příklad adresování ukazuje různé aspekty a vlastnosti adresy koncového bodu. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V této ukázce je služba v místním prostředí. Službu a klienta jsou konzolové aplikace. Služba definuje několik koncových bodů pomocí kombinace relativní a absolutní koncový bod adresy.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Konfigurační soubor služby definuje čtyři koncových bodů a základní adresa. Základní adresa určena pomocí elementu přidat v části service/hostitele/baseAddresses, jak je ukázáno v následující ukázková konfigurace.  
  
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
  
 První definice koncového bodu je znázorněno v následující ukázková konfigurace určuje relativní adresa, což znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresu dle pravidel složení identifikátoru URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 V takovém případě je relativní adresa prázdná (""), takže adresu koncového bodu je stejný jako základní adresu. Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service`.
  
 Druhá definice koncového bodu také určuje relativní adresa, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Relativní adresa "test", se připojí k základní adrese. Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service/test`.
  
 Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Základní adresa hraje žádná role v adrese. Adresa skutečný koncový bod je `http://localhost:8001/hello/servicemodelsamples`.
  
 Na čtvrté adresu koncového bodu určuje absolutní adresu a různé přenosové – TCP. Základní adresa hraje žádná role v adrese. Adresa skutečný koncový bod je `net.tcp://localhost:9000/servicemodelsamples/service`.
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 Klient přistupuje k právě jeden z koncových bodů služby čtyři, ale všechny čtyři jsou definovány v jeho konfiguračnímu souboru. Klient vybere koncový bod, když vytváří `CalculatorProxy` objektu. Tak, že změníte název konfigurace z `CalculatorEndpoint1` prostřednictvím `CalculatorEndpoint4`, je také možné získat jednotlivé koncové body.  
  
 Při spuštění ukázky služby zobrazí adresy, vazby název a název smlouvy pro každý z jeho koncových bodů. Koncový bod metadat exchange (MEX) je jenom další koncový bod z pohledu hostitele ServiceHost, zobrazí se v seznamu.  
  
```  
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
  
 Když spustíte klienta, operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
