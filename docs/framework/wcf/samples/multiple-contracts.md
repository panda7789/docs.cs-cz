---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 5e52c83d69c15ca5c407240a8971248205fef832
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818332"
---
# <a name="multiple-contracts"></a>Víc kontraktů
Více kontraktů Ukázka předvádí, jak implementovat více než jeden kontrakt na služby a jak nakonfigurovat koncové body pro komunikaci s každým implementovaných kontraktů. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Služba byla změněna definovat dva kontrakty `ICalculator` smlouvy a `ICalculatorSession` kontraktu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Implementuje třídu služby i `ICalculator` a `ICalculatorSession` smluv. Vzhledem k tomu, že jeden smlouvách vyžaduje relaci, služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režimu instance k uchování stavu během životního cyklu relace.  
  
 Konfigurace služby byla změněna definovat dvě koncových bodů ke zveřejnění každou smlouvu. `ICalculator` Koncový bod vystavený v základní adresu pomocí `basicHttpBinding`. `ICalculatorSession` Koncový bod je přístupný pomocí baseaddress/relace `wsHttpBinding` s `bindingConfiguration` atribut nastaven na `BindingWithSession`, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 Kód klienta vygenerovaný nyní obsahuje třídu klienta pro původní `ICalculator` kontraktu a nové `ICalculatorSession` kontraktu. Konfigurace klienta a kód se upravila tak komunikaci s každou smlouvu v koncovém bodě příslušnou službu.  
  
 Klient je konzolová aplikace systému windows (.exe). Služba je hostována v Internetové informační služby (IIS).  
  
 V okně konzoly klienta zobrazí operace odeslání na jednotlivé koncové body, nejdřív základní koncového bodu, za nímž následuje zabezpečeného koncového bodu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
