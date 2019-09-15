---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: a94e6dd50fb4a7326666c7843e20964b35f957c6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990209"
---
# <a name="addressing"></a>Adresování
Ukázka adresování znázorňuje různé aspekty a funkce adres koncových bodů. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V této ukázce je služba hostovaná v místním prostředí. Služba i klient jsou konzolové aplikace. Služba definuje více koncových bodů pomocí kombinace relativních a absolutních adres koncových bodů.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Konfigurační soubor služby určuje základní adresu a čtyři koncové body. Základní adresa je určena pomocí elementu add v části Služba/Hostitel/adres BaseAddresses, jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
 První definice koncového bodu uvedená v následující ukázkové konfiguraci Určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 V tomto případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejná jako základní adresa. Skutečná adresa koncového bodu `http://localhost:8000/servicemodelsamples/service`je.
  
 Druhá definice koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Relativní adresa "test" se připojí k základní adrese. Skutečná adresa koncového bodu `http://localhost:8000/servicemodelsamples/service/test`je.
  
 Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Základní adresa nehraje v adrese žádnou roli. Skutečná adresa koncového bodu `http://localhost:8001/hello/servicemodelsamples`je.
  
 Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP. Základní adresa nehraje v adrese žádnou roli. Skutečná adresa koncového bodu `net.tcp://localhost:9000/servicemodelsamples/service`je.
  
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
  
 Klient přistupuje pouze k jednomu ze čtyř koncových bodů služby, ale všechny čtyři jsou definovány v konfiguračním souboru. Klient vybere koncový bod při vytváření `CalculatorProxy` objektu. Změnou názvu konfigurace z `CalculatorEndpoint1` `CalculatorEndpoint4`nástroje můžete uplatnit jednotlivé koncové body.  
  
 Při spuštění ukázky služba vytvoří výčet adresy, názvu vazby a názvu kontraktu pro každý z jeho koncových bodů. Koncový bod výměny metadat (MEX) je pouze jiný koncový bod od perspektivy hostitele, takže se zobrazí v seznamu.  
  
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
  
 Když spustíte klienta nástroje, požadavky na operace a odpovědi se zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
