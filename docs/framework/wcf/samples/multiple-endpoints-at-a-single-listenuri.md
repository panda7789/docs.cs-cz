---
title: Víc koncových bodů na jedné adrese ListenUri
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 6249690b7fdc95affd21eee13e0c6e2af1c4f8a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312355"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Víc koncových bodů na jedné adrese ListenUri
Tato ukázka předvádí, služby, který je hostitelem více koncových bodů na jedné `ListenUri`. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Jak je ukázáno v [několik koncových bodů](../../../../docs/framework/wcf/samples/multiple-endpoints.md) ukázku, služba může hostovat více koncových bodů, každá má různé adresy a případně také různé vazby. Tento příklad ukazuje, že je možné k hostování více koncových bodů na stejné adrese. Tento příklad také znázorňuje rozdíly mezi těmito dvěma typy adres, které má koncový bod služby: `EndpointAddress` a `ListenUri`.  
  
 `EndpointAddress` Logické adresu služby. Je to adresa, že zprávy protokolu SOAP. `ListenUri` Je na fyzickou adresu služby. Obsahuje informace o portu a adresu kde koncový bod služby ve skutečnosti přijímají zprávy na aktuálním počítači. Ve většině případů není nutné pro tyto adresy, které se liší; Když `ListenUri` nebyl explicitně zadán, použije se výchozí identifikátor URI `EndpointAddress` koncového bodu. V několika případech je užitečné k rozlišení, jako je například při konfiguraci směrovač, který může přijímat zprávy adresované celou řadou různých služeb.  
  
## <a name="service"></a>Služba  
 Služby v této ukázce má dva kontrakty `ICalculator` a `IEcho`. Kromě obvyklý `IMetadataExchange` koncový bod, existují tři aplikačními koncovými body, jak je znázorněno v následujícím kódu.  
  
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
  
 Všechny tři koncové body jsou hostované na stejné `ListenUri` a použít stejné `binding` -koncových bodů na stejné `ListenUri` musí mít stejnou vazbu, protože sdílí jeden kanál zásobníku, které přijímají zprávy na tuto fyzickou adresu na počítač. `address` Každého koncového bodu je název URN, i když obvykle představují adresy fyzických umístění, ve skutečnosti adresa může být libovolný typ identifikátoru URI, protože adresa se používá pro porovnávání a účely filtrování, jak je uvedeno v této ukázce.  
  
 Protože všechny tři koncové body sdílet stejný `ListenUri`, při přijetí e-mailu, Windows Communication Foundation (WCF) musíte se rozhodnout, který koncový bod zprávy je určený pro. Každý koncový bod má filtru zpráv, která se skládá ze dvou částí: filtr adresy a filtru smlouvy. Filtr adresy odpovídá `To` zprávy protokolu SOAP, která se adresa koncového bodu služby. Například pouze zprávy adresované `To "Urn:OtherEcho"` jsou kandidáty na třetí koncového bodu této služby. Akce přidružené těmto operacím kontrakt konkrétní bod odpovídá filtru kontraktu. Příklad zprávy s akcí `IEcho`. `Echo` odpovídá kontraktu filtry druhého a třetího koncové body služby, protože obě tyto koncové body hostitele `IEcho` kontraktu.  
  
 Proto kombinace adresy filtr a kontrakt díky tomu je možné směrovat každá zpráva, která dorazí na tuto službu `ListenUri` na správný koncový bod. Třetí koncový bod je z další dvě jako liší, protože přijímá zprávy odeslané na adresu odlišnou z ostatních koncových bodů. Koncové body prvního a druhého se liší od sebe navzájem podle jejich kontrakty (akce příchozí zprávy).  
  
## <a name="client"></a>Klient  
 Stejně jako koncových bodů na serveru máte dvě různé adresy, koncové body klienta také mít dvě adresy. Na serveru a klienta, se nazývá logického adresního `EndpointAddress`. Ale vzhledem k tomu je volána na fyzickou adresu `ListenUri` na serveru, na straně klienta, se nazývá fyzickou adresu `Via`.  
  
 Tyto dvě adresy jako na serveru, ve výchozím nastavení jsou stejné. K určení `Via` na klientovi, který se liší od koncového bodu adresy `ClientViaBehavior` se používá:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Adresu jako obvykle pocházejí z klienta konfigurační soubor, který byl vygenerován pomocí Svcutil.exe. `Via` (Který odpovídá `ListenUri` služby) se nezobrazují v metadat služby a proto musí být tyto informace předávají klienta out-of-band (stejně jako adresu metadat služby).  
  
 Klient v této ukázce odešle zprávy u každého serveru tři koncových bodů aplikace prokázat, že se může komunikovat s (a odlišení) všechny tři koncové body, i když všechny mají stejnou `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Pro mezi počítači musíte místního hostitele v souboru Client.cs nahraďte název počítače, služby.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
