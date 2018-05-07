---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: e755c99f83cc7fdc02f3d8ff74b5a34fc6d57869
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ws-reliable-session"></a>Spolehlivá relace WS
Tento příklad znázorňuje použití spolehlivé relace. Spolehlivé relace poskytuje podporu pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv opakování komunikace při selhání a umožňuje záruky doručení zadat, jako je například doručení zpráv v daném pořadí. Relace uchování stavu pro klienty mezi volání. Ukázka implementuje relace pro zachování stavu klienta a určuje záruky doručení v daném pořadí.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. Spolehlivá relace funkcí jsou povolené a nakonfigurované v konfiguračních souborech aplikace pro klienta a služby.  
  
 V této ukázce služba je hostovaná v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázce se používá `wsHttpBinding`. Vazba je zadána v konfiguračních souborech pro klienta a služby. Typ vazby je zadaný v elementu koncový bod `binding` atributu, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Obsahuje koncový bod `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem "Binding1." Konfigurace vazeb umožňuje spolehlivé relace nastavením `enabled` atribut [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) k `true`. Záruky doručení pro seřazené relace jsou řízeny nastavením seřazené atribut `true` nebo `false`. Výchozí hodnota je `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Třída implementuje implementace služby <xref:System.ServiceModel.InstanceContextMode.PerSession> zřizování instancí udržovat samostatné třídy instance pro jednotlivé klienty, jak je znázorněno v následujícím ukázkovém kódu.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
