---
title: "Adresování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05fe983832eb3931549bbda5ee7db7c70766cd3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="addressing"></a>Adresování
Ukázka Addressing ukazuje různé aspekty a funkce adresy koncových bodů. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). V této ukázce se hostuje sama službu. Službu a klienta jsou konzolové aplikace. Služby definuje víc koncových bodů pomocí kombinace adresy relativní a absolutní koncových bodů.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Konfigurační soubor služby definuje čtyři koncové body a základní adresu. Základní adresa je zadán pomocí elementu přidat pod služby nebo hostitele nebo baseAddresses, jak je předvedeno v následující ukázka konfigurace.  
  
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
  
 První koncový bod definice znázorňuje následující ukázka konfigurace určuje relativní adresu, která znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresy následující pravidla složení identifikátor URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 V takovém případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejný jako základní adresu. Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples nebo služby.  
  
 Druhý definice služby endpoint také určuje relativní adresu, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Relativní adresu "test", připojí se k základní adresu. Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples/service/testování.  
  
 Třetí definice služby endpoint určuje absolutní adresu, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Základní adresa hraje žádný atribut role v adrese. Adresa skutečný koncový bod je http://localhost:8001/hello nebo servicemodelsamples.  
  
 Čtvrtý adresa koncového bodu určuje absolutní adresu a různé přenosové – TCP. Základní adresa hraje žádný atribut role v adrese. Adresa skutečný koncový bod je net.tcp://localhost: 9000/servicemodelsamples nebo služby.  
  
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
  
 Klient přistupuje k právě jeden z koncových bodů služby čtyři, ale všechny čtyři jsou definovány v konfiguračního souboru. Klient vybere koncový bod, když vytváří `CalculatorProxy` objektu. Změna názvu konfigurace z `CalculatorEndpoint1` prostřednictvím `CalculatorEndpoint4`, mohou vykonávat všechny koncové body.  
  
 Při spuštění ukázky, zobrazí služba adresy, vazby název a název kontraktu pro každý z jeho koncových bodů. Koncový bod metadat exchange (MEX) je právě jiným koncovým bodem z hlediska hostiteli služby, takže se zobrazí v seznamu.  
  
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
  
 Při spuštění klienta operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a>Viz také
