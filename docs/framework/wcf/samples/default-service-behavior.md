---
title: Výchozí chování služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 6c144bddff4e485673dbdc7e218e82808c20aa61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305231"
---
# <a name="default-service-behavior"></a>Výchozí chování služby
Tato ukázka předvádí, jak lze konfigurovat nastavení chování služby. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování služby a operace chování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy. Chování můžete nakonfigurovat v konfiguračních souborech nebo imperativně v kódu (jako v této ukázce).  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Určuje chování s třídu služby <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím příkladu kódu. Všechny zadané hodnoty jsou výchozí hodnoty.  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 Chování služby se zadaným <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut. Následující tabulka popisuje některé z těchto projevů.  
  
|Chování služby|Popis|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automaticky ukončí relaci v požadavku klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Určuje režim pro každou repliku služby.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Určuje režim kontextu instance.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Určuje, zda použít kontext synchronizace zadaná, je-li nastavena. Použijte ho, když chcete řídit, jestli se má použít `WindowsFormsSynchronizationContext` v aplikacích Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Určuje, zda mají být převedeny do jsou obecné zpracování neošetřené výjimky `Fault<string>` a odeslána jako zprávu o chybě.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Určuje úroveň izolace transakce.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Určuje, zda záhlaví neočekávaná zpráva způsobí chybovou podmínku.|  
  
 Operace chování je určené vlastností <xref:System.ServiceModel.OperationBehaviorAttribute> atribut. Následující tabulka popisuje některé z těchto projevů.  
  
|Chování operace|Popis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Určuje, zda služba dokončení operace potvrzení aktuální transakce.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Určuje, zda operace služby využívá v rámci klienta plynoucí transakce.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Určuje, zda operace služby zosobňuje identitu volajícího.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Určuje, zda instance služby recyklován na začátku nebo konci volání operace služby.|  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Zpoždění mezi volání je výsledkem volání `System.Threading.Thread.Sleep()` provedených operací služby. Zbývající část ukázky chování vysvětlit těchto projevů podrobněji. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
