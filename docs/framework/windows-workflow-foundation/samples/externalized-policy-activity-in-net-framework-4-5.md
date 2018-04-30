---
title: Činnost externalized zásad v rozhraní .NET Framework 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f131d644d58359cec305b83c136e6fe7f68a1b93
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Činnost externalized zásad v rozhraní .NET Framework 4.5
Tento příklad ukazuje, jak aktivity ExternalizedPolicy4 umožňuje provádění stávající [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] modelu Windows Workflow Foundation (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] modelu Windows Workflow Foundation (WF 4.5) přímo pomocí stroj pravidel která se dodává v WF 3.5. Pomocí této aktivity můžete otevřít a provést jakékoli existující 3.5 WF <xref:System.Workflow.Activities.Rules.RuleSet>. Další informace o stroj pravidel 3.5 WF jako součást modelu Windows Workflow Foundation, přečtěte si prosím [Úvod k modulu Windows Workflow Foundation pravidla](http://go.microsoft.com/fwlink/?LinkId=166079). Další informace o migraci pravidla [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], přečtěte si pokyny migrace na [migrace pokyny](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
  
|Název projektu|Popis|Hlavní soubory|  
|-|-|-|  
|ExternalizedPolicy4|Obsahuje ExternalizedPolicy4 aktivita a její návrháře WF 4.5.|**ExternalizedPolicy4.cs**: definici aktivity.<br /><br /> **ExternalizedPolicy4Designer.xaml**: vlastní Návrhář aktivity ExternalizedPolicy4. Použije pravidla editor (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z stroj pravidel WF 3.5.|  
|ImperativeCodeClientSample|Ukázkovou aplikaci klienta, která slouží ke konfiguraci a spustí pracovní postup pomocí ExternalizedPolicy4 aplikace pomocí imperativní kód C# (žádný návrhář použít).|**ApplyDiscount.rules**: soubor s [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definice pravidla.<br /><br /> **Order.cs**: typ, který reprezentuje pořadí od zákazníků. Pravidla objekty tohoto typu.<br /><br /> **Program.cs**: konfiguruje a spouští pracovní postup, který má aktivita Policy4 použít pravidla definovaná v ApplyDiscount.rules k instancím objektů pořadí.<br /><br /> App.config: Konfigurační soubor s cestu k souboru pravidla.|  
|DesignerClientSample|Ukázková aplikace klienta, která slouží ke konfiguraci a spustí pracovní postup pomocí aplikace ExternalPolicy4 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer.|**Sequence1.XAML**: sekvenční pracovní postup, který používá aktivitu Policy4 k provedení pravidlo hodnocení.<br /><br /> **Program.cs**: běží instance pracovního postupu definované v Sequence1.xaml.|  
  
## <a name="the-externalizedpolicy4-activity"></a>ExternalizedPolicy4 aktivity  
 Aktivita ExternalizedPolicy4 <xref:System.Activities.NativeActivity> umožňuje provádění WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> objektů v rámci pracovních postupů WF 4.5. Následující příklad je zjednodušený definice veřejné objektový model aktivity.  
  
```  
public class ExternalizedPolicy4Activity<TResult>: CodeActivity  
{  
    public string RulesFilePath   
  
    public string RuleSetName           
  
    [RequiredArgument]  
    public InArgument<T> TargetObject   
  
    [RequiredArgument]  
    public OutArgument<T> ResultObject   
  
    public OutArgument<ValidationErrorCollection> ValidationErrors   
}  
```  
  
|Vlastnost|Popis|  
|-|-|  
|RuleSetFilePath|Cesta k rozhraní .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> soubor vyhodnoceno, když se spustí aktivity.|  
|RuleSetName|Název <xref:System.Workflow.Activities.Rules.RuleSet> má být použit v rámci tohoto souboru .rules.|  
|TargetObject|Objekt, u kterého <xref:System.Workflow.Activities.Rules.Rule> objekty v <xref:System.Workflow.Activities.Rules.RuleSet> je porovnán s.|  
|ResultObject|Výsledný objekt po použití pravidel (například pravidla se používají s argumentem vstup a výsledek je uložen v argumentu výsledek.|  
|ValidationError|Seznam chyb ověřování vrácená strojem pravidel 3.5 WF při ověřování <xref:System.Workflow.Activities.Rules.RuleSet> proti cílový objekt před spuštěním.|  
  
## <a name="externalizedpolicy4-activity-designer"></a>Návrhář aktivity ExternalizedPolicy4  
 Návrhář ExternalizedPolicy4 umožňuje nakonfigurovat aktivitu používat existující RuleSet bez nutnosti psaní kódu. Stačí nastavit cestu, kde je umístěn soubor .rules a zadejte <xref:System.Workflow.Activities.Rules.RuleSet> název, kterou chcete použít. Můžete taky změnit <xref:System.Workflow.Activities.Rules.RuleSet>. Po sestavení řešení, můžete najít v panelu nástrojů v části Microsoft.Samples.Activities.Rules. Návrhář vám umožní vybrat soubor .rules a <xref:System.Workflow.Activities.Rules.RuleSet>. Když **upravit RuleSet** po kliknutí na tlačítko, WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> se zobrazí. Toto dialogové okno je znovu hostované editoru pravidel WF 3.5 a slouží k zobrazení a úprava pravidla, která provede ExternalizedPolicy4 aktivity.  
  
## <a name="policy4-and-externalpolicy4"></a>Policy4 a ExternalPolicy4  
 [Činnost zásad v rozhraní .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) aktivity umožňuje vytvářet a spouštět rozhraní .NET Framework 3.5 RuleSet v pracovním postupu WF 4.5. <xref:System.Workflow.Activities.Rules.RuleSet> Je serializovaná vložené v aktivitě Policy4 definici XAML. Ukázka ExternalizedPolicy4 ukazuje způsob použití existující externí <xref:System.Workflow.Activities.Rules.RuleSet> (obsažené v souboru .rules).  
  
## <a name="using-this-sample"></a>Pomocí této ukázky  
 Ke spuštění této ukázce je vyžadováno žádné speciální nastavení. Otevřete řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], a stiskněte klávesu F5 a spusťte aplikaci.  
  
 Tato ukázka obsahuje dva klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí imperativní kód C#. DesignerClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí návrháře.  
  
#### <a name="to-run-the-imperativecodeclientsample-application"></a>Ke spuštění aplikace ImperativeCodeClientSample  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4sample.sln.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ImperativeCodeClientSample** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
3.  Chcete-li spustit projekt, stiskněte CTRL + F5.  
  
#### <a name="to-run-the-designerclientsample-application"></a>Ke spuštění aplikace DesignerClientSample  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4sample.sln.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DesignerClientSample** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
3.  Stisknutím kombinace kláves CTRL + SHIFT + B kompilace projektu.  
  
4.  Stisknutím kombinace kláves CTRL + F5 a spusťte projekt.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
