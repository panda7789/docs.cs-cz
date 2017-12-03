---
title: "Výchozí chování služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 57d534a1af16790aa6c3477629f0d4b6e2604179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="default-service-behavior"></a>Výchozí chování služby
Tento příklad znázorňuje, jak lze nakonfigurovat nastavení chování služby. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. Tato ukázka explicitně definuje chování služby a chování operace pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy. Chování můžete nakonfigurovat v konfiguračních souborech nebo imperativní v kódu (jako je tento příklad znázorňuje).  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Třída služby určuje chování s <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> jak znázorňuje následující ukázka kódu. Všechny hodnoty zadané jsou výchozí hodnoty.  
  
```  
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
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automaticky ukončí relace v požadavku klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Určuje režim souběžnosti pro každou instanci služby.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Určuje režim kontextu instance.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Určuje, zda se použít kontext zadaný synchronizace, je-li nastavena. To použijte, pokud chcete řídit, jestli se má použít `WindowsFormsSynchronizationContext` v aplikacích Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Určuje, zda mají být převedeny do jsou obecné provádění neošetřené výjimky `Fault<string>` a odeslán jako zprávu o chybě.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Určuje úroveň izolace transakce.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Určuje, zda záhlaví neočekávaná zpráva způsobit chybový stav.|  
  
 Chování operace jsou určeny pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> atribut. Následující tabulka popisuje některé z těchto projevů.  
  
|Operace chování|Popis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Určuje, jestli dokončení operace služby potvrdí aktuální transakci.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Určuje, zda operace služby využívá v transakci plynoucích klienta.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Určuje, zda operace služby zosobňuje identitu volajícího.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Určuje, zda instance služby recykluje na začátku nebo na konci volání operace služby.|  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Zpoždění mezi volání je výsledkem volání `System.Threading.Thread.Sleep()` provedené v operací služby. Zbývající chování vzorků, které popisují tyto chování podrobněji. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a>Viz také
