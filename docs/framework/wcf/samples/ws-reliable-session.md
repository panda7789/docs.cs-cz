---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143496"
---
# <a name="ws-reliable-session"></a>Spolehlivá relace WS
Tato ukázka ukazuje použití spolehlivé relace. Spolehlivé relace poskytují podporu pro spolehlivé zasílání zpráv a relací. Spolehlivé zasílání zpráv opakuje komunikaci o selhání a umožňuje zajištění doručení, které mají být zadány, jako je například doručení zpráv v pořadí. Relace udržovat stav pro klienty mezi voláními. Ukázka implementuje relace pro udržování stavu klienta a určuje záruky doručení v pořadí.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. Spolehlivé funkce relace jsou povoleny a konfigurovány v konfiguračních souborech aplikace pro klienta a službu.  
  
 V této ukázce je služba hostována v Internetové informační službě (IIS) a klient je konzolová aplikace (.exe).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ukázka používá `wsHttpBinding`. Vazba je určena v konfiguračních souborech pro klienta i službu. Typ vazby je určen v atributu prvku koncového `binding` bodu, jak je znázorněno v následující konfiguraci ukázky.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Koncový bod obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem "Binding1.". Konfigurace vazby umožňuje spolehlivé `enabled` relace nastavením atributu `true` [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) na . Záruky doručení pro objednané relace jsou `true` řízeny nastavením objednaného atributu nebo `false`. Výchozí formát je `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Třída implementace služby <xref:System.ServiceModel.InstanceContextMode.PerSession> implementuje instance udržovat samostatnou instanci třídy pro každého klienta, jak je znázorněno v následujícím ukázkovém kódu.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
