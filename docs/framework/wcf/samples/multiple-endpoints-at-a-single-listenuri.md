---
title: Víc koncových bodů na jedné adrese ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: f3eb2036ffbb7c5e8cae77ebc1a86e07d31626c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Víc koncových bodů na jedné adrese ListenUri
Tento příklad znázorňuje služby, který je hostitelem víc koncových bodů na jedné `ListenUri`. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Jak je předvedeno v [několik koncových bodů](../../../../docs/framework/wcf/samples/multiple-endpoints.md) ukázku, služba může hostovat několik koncových bodů, každý s různé adresy a případně také různé vazby. Tento příklad ukazuje, že je možné k hostování víc koncových bodů na stejnou adresu. Tento příklad znázorňuje také rozdíly mezi dva druhy adresy, které má koncový bod služby: `EndpointAddress` a `ListenUri`.  
  
 `EndpointAddress` Je adresa logické služby. Je na adresu, která jsou určena protokolu SOAP zprávy. `ListenUri` Je fyzická adresa služby. Obsahuje informace o portu a adresu kde koncový bod služby ve skutečnosti přijímá zprávy do aktuálního počítače. Ve většině případů není třeba pro tyto adresy do liší; Když `ListenUri` není explicitně zadané, nastaví se jako výchozí identifikátor URI `EndpointAddress` koncového bodu. V určitých případech je užitečné k rozlišení, například při konfiguraci směrovač, který může přijmout zprávy adresované do několik různých služeb.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dva kontrakty `ICalculator` a `IEcho`. Kromě obvyklé `IMetadataExchange` koncový bod, existují tři koncových bodů aplikace, jak je znázorněno v následujícím kódu.  
  
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
  
 Všechny tři koncové body jsou hostované ve stejné `ListenUri` a používat stejné `binding` -koncových bodů ve stejné `ListenUri` musí mít stejnou vazbu, protože jejich sdílení jednoho kanálu zásobníku, která přijímá zprávy v této fyzickou adresu na počítač. `address` Každý koncový bod je název URN; když adresy obvykle představují fyzického umístění, ve skutečnosti adresa může být jakýkoli druh identifikátor URI, protože adresa se používá pro porovnávání a filtrování účely, jak je ukázáno v této ukázce.  
  
 Protože všechny tři koncové body sdílet stejný `ListenUri`, při doručení zprávy zde Windows Communication Foundation (WCF) musíte se rozhodnout, kterému koncovému bodu zprávy je určené pro. Každý koncový bod má filtr zpráv, která se skládá ze dvou částí: Filtr adres a filtru smlouvy. Filtr adres odpovídá `To` protokolu SOAP zprávy na adresu koncového bodu služby. Například pouze zprávy adresované `To "Urn:OtherEcho"` jsou kandidáty pro třetí koncový bod této služby. Filtr smlouvy odpovídá akce přidružené těmto operacím konkrétní smlouvou. Příklad zprávy s akcí `IEcho`. `Echo` odpovídá filtry kontrakt druhé a třetí koncových bodů služby, protože obě tyto koncové body hostitele `IEcho` kontrakt.  
  
 Proto kombinace adresu filtr a kontraktů umožňuje směrovat každou zprávu, která dorazí na tuto službu `ListenUri` správný koncový bod. Třetí koncový bod je z další dvě hodnoty, protože přijímá zprávy odeslané na jinou adresu z dalších koncových bodů. První a druhý koncových bodů jsou rozlišené od sebe navzájem na základě jejich smluv (akce příchozí zprávy).  
  
## <a name="client"></a>Klient  
 Podobně jako koncové body na serveru dvě různé adresy, koncové body klienta také mít dvě adresy. Na serveru a klienta, se nazývá logické adresy `EndpointAddress`. Ale vzhledem k tomu, se nazývá fyzickou adresu `ListenUri` na serveru, na straně klienta, se nazývá fyzickou adresu `Via`.  
  
 Tyto dvě adresy jako na serveru, ve výchozím nastavení jsou stejné. Chcete-li určit `Via` v klientovi, který se liší od adresy pro koncový bod `ClientViaBehavior` se používá:  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Adresu jako obvykle pochází z konfiguračního souboru klienta, který byl vygenerován nástrojem Svcutil.exe. `Via` (Která odpovídá `ListenUri` služby) pravděpodobně není v metadatech služby a tak tyto informace se sdělí klienta out-of-band (stejně jako adresu metadata služby).  
  
 Klient v této ukázce odešle zprávy ke každému serveru tři koncových bodů aplikace k předvedení to může komunikovat s (a odlišují jej od) všechny tři koncové body, i když všechny mají stejné `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Cross-počítače je potřeba nahradit localhost v souboru Client.cs název počítače, služby.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Viz také
