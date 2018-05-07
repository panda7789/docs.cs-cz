---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 8e96d1ac27eb69d8e7e4da76aa8679aa35bf8ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="multiple-contracts"></a>Víc kontraktů
Ukázka víc kontraktů ukazuje, jak implementovat více než jeden kontrakt na služby a konfiguraci koncových bodů pro komunikaci s jednotlivými implementovaná kontrakty. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Služba byla změněna definovat dvě kontrakty `ICalculator` kontraktu a `ICalculatorSession` kontrakt.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Třída služby implementuje i `ICalculator` a `ICalculatorSession` smluv. Protože jeden z smluv vyžaduje relaci, služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režim instancí Udržovat stav po dobu životnosti relace.  
  
 Konfigurace služby se změnilo definovat dva koncové body vystavit každé smlouvě. `ICalculator` Koncový bod vystavený v základní adresa pomocí `basicHttpBinding`. `ICalculatorSession` Koncový bod vystavený v baseaddress/relace pomocí `wsHttpBinding` s `bindingConfiguration` atribut nastaven na `BindingWithSession`, jak ukazuje následující ukázka konfigurace.  
  
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
  
 Kód klienta vygenerovaný teď obsahuje třídu klienta pro obě původní `ICalculator` kontraktu a nové `ICalculatorSession` kontrakt. Konfigurace klienta a kód bylo upraveno, aby komunikovat s každou smlouvu na koncový bod příslušné služby.  
  
 Klient je konzolovou aplikaci systému windows (.exe). Služba je hostovaná Internetové informační služby (IIS).  
  
 V okně konzoly klienta zobrazí operace Odeslat všechny koncové body, nejdřív základní koncový bod, za nímž následuje zabezpečený koncový bod.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>Viz také
