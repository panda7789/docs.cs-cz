---
title: Víc koncových bodů na jedné adrese ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: ea0cd0d8636f5301dab3fe60b181dfd36fc30d54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930336"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Víc koncových bodů na jedné adrese ListenUri
Tato ukázka demonstruje službu, která hostuje více koncových bodů v jednom `ListenUri`. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Jak je znázorněno v ukázce [více koncových bodů](../../../../docs/framework/wcf/samples/multiple-endpoints.md) , může služba hostovat více koncových bodů, každý s různými adresami a případně také různé vazby. Tento příklad ukazuje, že je možné hostovat více koncových bodů na stejné adrese. Tato ukázka také ukazuje rozdíly mezi dvěma druhy adres, které koncový bod služby obsahuje: `EndpointAddress` a. `ListenUri`  
  
 `EndpointAddress` Je logická adresa služby. Jedná se o adresu, na kterou jsou adresovány zprávy SOAP. `ListenUri` Je fyzickou adresou služby. Obsahuje informace o portu a adrese, kde koncový bod služby ve skutečnosti čeká na zprávy v aktuálním počítači. Ve většině případů není potřeba, aby se tyto adresy lišily. Pokud není explicitně zadáno, použije se výchozí identifikátor URI `EndpointAddress` koncového bodu. `ListenUri` V několika případech je vhodné je odlišit, například při konfigurování směrovače, který může přijímat zprávy s adresováním na několik různých služeb.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dvě smlouvy `ICalculator` a. `IEcho` Kromě vlastního `IMetadataExchange` koncového bodu existují tři koncové body aplikace, jak je znázorněno v následujícím kódu.  
  
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
  
 Všechny tři koncové body jsou hostovány na `ListenUri` stejné úrovni a používají `binding` stejné koncové body na stejné `ListenUri` úrovni, které musí mít stejnou vazbu, protože sdílejí jeden zásobník kanálů, který naslouchá zprávám na dané fyzické adrese. počítačové. U `address` každého koncového bodu je urn; i když obvykle adresy představuje fyzická umístění, adresa může být jakýkoli druh identifikátoru URI, protože adresa se používá pro účely porovnání a filtrování, jak je znázorněno v této ukázce.  
  
 Vzhledem k tomu, že všechny tři `ListenUri`koncové body mají stejné sdílení, když tam přijde zpráva, Windows Communication Foundation (WCF) musí rozhodnout, pro který koncový bod je zpráva určena. Každý koncový bod má filtr zpráv, který se skládá ze dvou částí: Filtr adres a filtr kontraktu. Filtr adres odpovídá `To` zprávě protokolu SOAP na adresu koncového bodu služby. Například pouze vyřešené `To "Urn:OtherEcho"` zprávy jsou kandidáty na třetí koncový bod této služby. Filtr kontraktu odpovídá akcím přidruženým k operacím konkrétní smlouvy. Například zprávy s akcí `IEcho`. `Echo`odpovídá filtrům kontraktu obou druhý i třetí koncových bodů této služby, protože oba z těchto koncových bodů `IEcho` hostují kontrakt.  
  
 Kombinace filtru adres a filtru kontraktů proto umožňuje směrovat každou zprávu, která dorazí na tuto službu `ListenUri` do správného koncového bodu. Třetí koncový bod se odlišuje od ostatních dvou, protože přijímá zprávy odeslané na jinou adresu z ostatních koncových bodů. První a druhý koncový bod se odlišuje od ostatních na základě jejich smluv (Akce příchozí zprávy).  
  
## <a name="client"></a>Klient  
 Stejně jako koncové body na serveru mají dvě různé adresy, koncové body klienta mají také dvě adresy. Na straně serveru i klienta se logická adresa nazývá `EndpointAddress`. Ale zatímco fyzická adresa se nazývá `ListenUri` na serveru, na straně klienta se fyzická adresa `Via`nazývá.  
  
 Stejně jako na serveru jsou tyto dvě adresy stejné. Pokud chcete zadat `Via` v klientovi, který se liší od adresy koncového bodu, `ClientViaBehavior` použije se:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 V obvyklých případech adresa pochází z konfiguračního souboru klienta, který byl vygenerován nástrojem Svcutil. exe. Rozhraní `Via` (které odpovídá `ListenUri` službě) se nezobrazí v metadatech služby, takže tyto informace musí být sdělovány klientovi mimo IP síť (stejně jako adresa metadat služby).  
  
 Klient v této ukázce odesílá zprávy do každého ze tří koncových bodů aplikace serveru, aby ukázal, že může komunikovat s (a odlišit) všechny tři koncové body, i když všechny mají stejnou `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  V případě více počítačů je třeba v souboru Client.cs nahradit localhost názvem počítače služby.  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
