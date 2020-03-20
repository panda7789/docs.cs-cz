---
title: Víc kontraktů
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144341"
---
# <a name="multiple-contracts"></a>Víc kontraktů
Ukázka více smluv ukazuje, jak implementovat více než jednu smlouvu na službu a jak nakonfigurovat koncové body pro komunikaci s každou z implementovaných smluv. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Služba byla upravena tak, aby `ICalculator` definovala `ICalculatorSession` dvě smlouvy, smlouvu a smlouvu.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Třída služeb implementuje `ICalculator` `ICalculatorSession` a smlouvy. Vzhledem k tomu, že jedna ze <xref:System.ServiceModel.InstanceContextMode.PerSession> smluv vyžaduje relaci, služba používá režim instance k udržení stavu po celou dobu trvání relace.  
  
 Konfigurace služby byla upravena tak, aby definovala dva koncové body pro vystavení každé smlouvy. Koncový `ICalculator` bod je vystaven na základní `basicHttpBinding`adrese pomocí . Koncový `ICalculatorSession` bod je vystaven na baseaddress/session pomocí `wsHttpBinding` `bindingConfiguration` atribut `BindingWithSession`nastavit na , jak je znázorněno v následující konfiguraci vzorku.  
  
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
  
 Generovaný kód klienta nyní zahrnuje třídu klienta pro původní `ICalculator` smlouvu i novou `ICalculatorSession` smlouvu. Konfigurace klienta a kód byly upraveny tak, aby komunikovaly s každou smlouvou v příslušném koncovém bodu služby.  
  
 Klient je aplikace systému Windows konzoly (.exe). Služba je hostována internetovou informační službou (IIS).  
  
 Okno klientské konzole zobrazí operace odeslané do každého koncového bodu, nejprve základní koncový bod následovaný zabezpečeným koncovým bodem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
