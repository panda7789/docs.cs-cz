---
title: Víc koncových bodů na jedné adrese ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e26cc18ed35c446dda120c678dd7e879c756c0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183482"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Víc koncových bodů na jedné adrese ListenUri
Tato ukázka ukazuje službu, která hostuje více koncových bodů v jednom `ListenUri`. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Jak je znázorněno v [ukázce více koncových bodů,](../../../../docs/framework/wcf/samples/multiple-endpoints.md) služba může hostovat více koncových bodů, každý s různými adresami a případně také různé vazby. Tato ukázka ukazuje, že je možné hostovat více koncových bodů na stejné adrese. Tato ukázka také ukazuje rozdíly mezi dvěma druhy adres, které `EndpointAddress` `ListenUri`koncový bod služby má: a .  
  
 Je `EndpointAddress` logická adresa služby. Je adresa, která soap zprávy jsou určeny. Je `ListenUri` fyzická adresa služby. Má port a adresu informace, kde koncový bod služby skutečně naslouchá zprávy v aktuálním počítači. Ve většině případů není nutné, aby se tyto adresy lišily; pokud `ListenUri` a není explicitně zadán, výchozí uri `EndpointAddress` koncového bodu. V několika případech je užitečné je rozlišit, například při konfiguraci směrovače, který může přijímat zprávy adresované řadě různých služeb.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dvě smlouvy `ICalculator` a `IEcho`. Kromě obvyklékoncový `IMetadataExchange` bod existují tři koncové body aplikace, jak je znázorněno v následujícím kódu.  
  
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
  
 Všechny tři koncové body jsou `ListenUri` hostovány na `binding` stejné a používat `ListenUri` stejné - koncové body na stejné musí mít stejnou vazbu, protože jsou sdílení zásobníku jednoho kanálu, který naslouchá zprávy na tuto fyzickou adresu v počítači. Každý `address` koncový bod je URN; ačkoli obvykle adresy představují fyzické umístění, ve skutečnosti adresa může být jakýkoli druh identifikátoru URI, protože adresa se používá pro účely párování a filtrování, jak je prokázáno v této ukázce.  
  
 Vzhledem k tomu, `ListenUri`že všechny tři koncové body sdílejí stejné , když zpráva dorazí tam, Windows Communication Foundation (WCF) musí rozhodnout, který koncový bod zpráva je určena pro. Každý koncový bod má filtr zpráv, který se skládá ze dvou částí: filtr adresy a filtr smlouvy. Filtr adresy odpovídá `To` zprávě SOAP s adresou koncového bodu služby. Například pouze adresované `To "Urn:OtherEcho"` zprávy jsou kandidáty pro třetí koncový bod této služby. Filtr smlouvy odpovídá akcím přidruženým k operacím určité smlouvy. Například zprávy s akcí `IEcho`. `Echo`odpovídá filtry smlouvy druhé a třetí koncové body této služby, protože `IEcho` oba tyto koncové body hostitele smlouvy.  
  
 Kombinace filtru adres a filtru smlouvy tedy umožňuje směrovat každou zprávu, `ListenUri` která dorazí do služby, do správného koncového bodu. Třetí koncový bod se liší od ostatních dvou, protože přijímá zprávy odeslané na jinou adresu než ostatní koncové body. První a druhý koncový bod jsou od sebe odlišeny na základě jejich smluv (akce příchozí zprávy).  
  
## <a name="client"></a>Klient  
 Stejně jako koncové body na serveru mají dvě různé adresy, koncové body klienta mají také dvě adresy. Na serveru i klientovi se logická adresa nazývá `EndpointAddress`. Ale zatímco fyzická adresa `ListenUri` se nazývá na serveru, na straně klienta, fyzická adresa se `Via`nazývá .  
  
 Stejně jako na serveru jsou ve výchozím nastavení tyto dvě adresy stejné. Chcete-li `Via` zadat na klienta, který se liší `ClientViaBehavior` od adresy koncového bodu, se používá:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Jako obvykle, adresa pochází z konfiguračního souboru klienta, který byl generován Svcutil.exe. (což `Via` odpovídá `ListenUri` službě) se nezobrazí v metadatech služby, a proto musí být tyto informace sděleny klientovi mimo pásmo (stejně jako adresa metadat služby).  
  
 Klient v této ukázce odesílá zprávy každému ze tří koncových bodů aplikace serveru, aby prokázal, že může komunikovat `Via`se všemi třemi koncovými body (a rozlišovat), i když všechny mají stejné .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pro cross-machine, musíte nahradit localhost v souboru Client.cs názvem servisního stroje.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
