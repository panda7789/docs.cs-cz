---
title: Víc koncových bodů na jedné adrese ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: ef4212fa0989f80393f62119d9b2b6cda370ef94
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714738"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Víc koncových bodů na jedné adrese ListenUri
Tato ukázka demonstruje službu, která hostuje více koncových bodů v jednom `ListenUri`. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Jak je znázorněno v ukázce [více koncových bodů](../../../../docs/framework/wcf/samples/multiple-endpoints.md) , může služba hostovat více koncových bodů, každý s různými adresami a případně také různé vazby. Tento příklad ukazuje, že je možné hostovat více koncových bodů na stejné adrese. Tato ukázka také ukazuje rozdíly mezi dvěma druhy adres, které koncový bod služby obsahuje: `EndpointAddress` a `ListenUri`.  
  
 `EndpointAddress` je logická adresa služby. Jedná se o adresu, na kterou jsou adresovány zprávy SOAP. `ListenUri` je fyzická adresa služby. Obsahuje informace o portu a adrese, kde koncový bod služby ve skutečnosti čeká na zprávy v aktuálním počítači. Ve většině případů není potřeba, aby se tyto adresy lišily. Pokud `ListenUri` explicitně neurčíte, použije se výchozí identifikátor URI `EndpointAddress` koncového bodu. V několika případech je vhodné je odlišit, například při konfigurování směrovače, který může přijímat zprávy s adresováním na několik různých služeb.  
  
## <a name="service"></a>Service  
 Služba v této ukázce má dvě kontrakty, `ICalculator` a `IEcho`. Kromě vlastního koncového bodu `IMetadataExchange` existují tři koncové body aplikace, jak je znázorněno v následujícím kódu.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Všechny tři koncové body jsou hostovány na stejném `ListenUri` a používají stejné `binding`-koncové body na stejném `ListenUri` musí mít stejnou vazbu, protože sdílejí jeden zásobník kanálů, který naslouchá zprávám na dané fyzické adrese v počítači. `address` každého koncového bodu je URN; i když adresy obvykle představuje fyzická umístění, adresa může být jakýkoli druh identifikátoru URI, protože adresa se používá pro účely porovnání a filtrování, jak je znázorněno v této ukázce.  
  
 Vzhledem k tomu, že všechny tři koncové body sdílí stejné `ListenUri`, když tam přijde zpráva, Windows Communication Foundation (WCF) musí rozhodnout, pro který koncový bod je zpráva určena. Každý koncový bod má filtr zpráv, který se skládá ze dvou částí: Filtr adres a filtr kontraktu. Filtr adres odpovídá `To` zprávy SOAP na adresu koncového bodu služby. Například pouze zprávy s adresou `To "Urn:OtherEcho"` jsou kandidáty na třetí koncový bod této služby. Filtr kontraktu odpovídá akcím přidruženým k operacím konkrétní smlouvy. Například zprávy s akcí `IEcho`. `Echo` odpovídá filtrům kontraktu obou druhý i třetí koncových bodů této služby, protože oba tyto koncové body hostují `IEcho` kontrakt.  
  
 Kombinace filtru adres a filtru kontraktů proto umožňuje směrovat každou zprávu, která dorazí na `ListenUri` této služby do správného koncového bodu. Třetí koncový bod se odlišuje od ostatních dvou, protože přijímá zprávy odeslané na jinou adresu z ostatních koncových bodů. První a druhý koncový bod se odlišuje od ostatních na základě jejich smluv (Akce příchozí zprávy).  
  
## <a name="client"></a>Klient  
 Stejně jako koncové body na serveru mají dvě různé adresy, koncové body klienta mají také dvě adresy. Na straně serveru i klienta se logická adresa označuje jako `EndpointAddress`. Ale zatímco se fyzická adresa nazývá `ListenUri` na serveru, na klientovi se fyzická adresa nazývá `Via`.  
  
 Stejně jako na serveru jsou tyto dvě adresy stejné. Pokud chcete určit `Via` v klientovi, který se liší od adresy koncového bodu, `ClientViaBehavior` se používá:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 V obvyklých případech adresa pochází z konfiguračního souboru klienta, který byl vygenerován nástrojem Svcutil. exe. `Via` (který odpovídá `ListenUri` služby) se nezobrazuje v metadatech služby, takže tyto informace musí být předávány klientovi mimo IP síť (stejně jako adresa metadat služby).  
  
 Klient v této ukázce odesílá zprávy do každého ze tří koncových bodů aplikace serveru, aby ukázal, že může komunikovat s (a odlišit) všechny tři koncové body, i když všechny mají stejné `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > V případě více počítačů je třeba v souboru Client.cs nahradit localhost názvem počítače služby.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
