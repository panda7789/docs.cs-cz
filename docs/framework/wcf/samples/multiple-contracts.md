---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 39970f9f0aefa46c3d064b39c9b35d195ef22843
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930354"
---
# <a name="multiple-contracts"></a>Víc kontraktů
Ukázka více kontraktů ukazuje, jak implementovat více kontraktů ve službě a jak nakonfigurovat koncové body pro komunikaci se všemi implementovanými kontrakty. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Služba byla změněna tak, aby definovala dvě smlouvy, `ICalculator` kontrakt `ICalculatorSession` a kontrakt.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Třída služby implementuje `ICalculator` `ICalculatorSession` kontrakty i. Vzhledem k tomu, že jedna z kontraktů vyžaduje relaci, služba <xref:System.ServiceModel.InstanceContextMode.PerSession> používá režim instance k udržení stavu po celou dobu životnosti relace.  
  
 Konfigurace služby byla změněna tak, aby definovala dva koncové body, aby bylo možné všechny kontrakty zveřejnit. Koncový bod se zveřejňuje na základní adrese `basicHttpBinding`pomocí. `ICalculator` Koncový bod se zveřejňuje v rámci BaseAddress/Session `wsHttpBinding` pomocí `bindingConfiguration` atributu s atributem nastaveným na `BindingWithSession`, jak je znázorněno v následující ukázkové konfiguraci. `ICalculatorSession`  
  
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
  
 Generovaný kód klienta teď obsahuje třídu klienta pro původní `ICalculator` kontrakt i novou `ICalculatorSession` kontrakt. Konfigurace a kód klienta byly upraveny tak, aby komunikovaly s každou kontraktovou službou příslušného koncového bodu služby.  
  
 Klient je Konzolová aplikace pro Windows (. exe). Služba je hostována službou Internetová informační služba (IIS).  
  
 Okno konzoly klienta zobrazuje operace odesílané do každého koncového bodu, nejprve základní koncový bod následovaný zabezpečeným koncovým bodem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
