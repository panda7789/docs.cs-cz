---
title: Omezování
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: 1337b5d1c4c18700f0722bbb6912e934b2170b01
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202052"
---
# <a name="throttling"></a>Omezování
Ukázka omezování demonstruje použití omezení ovládacích prvků. Omezení ovládacích prvků umístit omezení na počtu souběžných volání, instance nebo relace, aby se zabránilo typu over-pass-the spotřebu prostředků. Chování při omezování chování je zadán v nastavení konfiguračního souboru služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Konfigurační soubor služby definuje omezení ovládacích prvků [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Podle konfigurace, služba omezuje maximální souběžných volání 2 a maximální počet souběžných instancí 10.  
  
 Aby bylo možné předvést, omezování definujeme doba režimu spánku u metod služby následujícím způsobem:  
  
```csharp
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Metody přidat a rozdílové jsou současně spouštěny a Multiply a dělení metody jsou spouštěny souběžně prokázání, že není více než 2 metody mohou být provedeny souběžně tedy ukázka omezování.  
  
```console  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
  
## <a name="see-also"></a>Viz také
