---
title: Výchozí chování služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 4da3deff69930dba7249e0651f820b448b837862
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592447"
---
# <a name="default-service-behavior"></a>Výchozí chování služby
Tato ukázka předvádí, jak lze nakonfigurovat nastavení chování služby. Ukázka je založena na [Začínáme](getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování služby a chování operace pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atributů a <xref:System.ServiceModel.OperationBehaviorAttribute> . Chování můžete nakonfigurovat v konfiguračních souborech nebo imperativně v kódu (jak ukazuje tento příklad).  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Třída služby určuje chování pomocí a, <xref:System.ServiceModel.ServiceBehaviorAttribute> jak je <xref:System.ServiceModel.OperationBehaviorAttribute> znázorněno v následujícím příkladu kódu. Všechny zadané hodnoty jsou výchozí hodnoty.  
  
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
  
 Chování služby je určeno <xref:System.ServiceModel.ServiceBehaviorAttribute> atributem. Některé z těchto chování jsou popsány v následující tabulce.  
  
|Chování služby|Popis|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automaticky vypne relaci v žádosti klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Určuje režim souběžnosti pro každou instanci služby.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Určuje kontextový režim instance.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Určuje, zda se má použít poskytnutý kontext synchronizace, pokud je nastaven. Tuto možnost použijte, pokud chcete určit, jestli se má používat `WindowsFormsSynchronizationContext` v model Windows Formsch aplikacích.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Určuje, zda mají být obecné neošetřené výjimky provádění převedeny do `Fault<string>` a odeslány jako chybová zpráva.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Určuje úroveň izolace pro transakce.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Určuje, zda neočekávaná záhlaví zprávy způsobují chybový stav.|  
  
 Chování operace jsou určena pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> atributu. Některé z těchto chování jsou popsány v následující tabulce.  
  
|Chování operace|Popis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Určuje, zda dokončení operace služby potvrdí aktuální transakci.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Určuje, zda operace služby zařadí transakce v transakci toku klienta.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Určuje, zda operace služby zosobňuje identitu volajícího.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Určuje, zda se instance služby recyklují na začátku nebo konci volání operace služby.|  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Zpoždění mezi voláními je výsledkem volání, která se mají `System.Threading.Thread.Sleep()` provést v operacích služby. Zbytek ukázek chování Vysvětlete toto chování podrobněji. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
