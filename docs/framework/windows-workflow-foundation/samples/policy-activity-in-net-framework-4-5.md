---
title: "Zásady aktivity v rozhraní .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d12a3d5a74fa8b0d266fb2ba9494e1a5775f0411
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="policy-activity-in-net-framework-45"></a>Zásady aktivity v rozhraní .NET Framework 4.5
Umožňuje aktivity Policy4 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty, které chcete použít v [!INCLUDE[wf2](../../../../includes/wf2-md.md)] v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí pravidla modulem, který se dodává v WF 3.5. Pomocí této aktivity může vytvářet a spouštět WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WF 3.5 stroj pravidel, které jsou součástí Windows Workflow Foundation, přečtěte si úvod k modulu Windows Workflow Foundation pravidla. Další informace o migraci pravidla, která WF v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], přečtěte si prosím [migrace pokyny](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
  
|Název projektu|Popis|Hlavní soubory|  
|------------------|-----------------|----------------|  
|Policy4|Obsahuje aktivitu Policy4 a jeho [!INCLUDE[wf1](../../../../includes/wf1-md.md)] designer.|**Policy4.cs**: Policy4 definici aktivity.<br /><br /> **PolicyDesigner.xaml**: vlastní Návrhář aktivity Policy4. Použije pravidla editor ([RuleSetDialog třída](http://go.microsoft.com/fwlink/?LinkId=150378)) z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] stroj pravidel.|  
|ImperativeCodeClientSample|Ukázková aplikace klienta, která slouží ke konfiguraci a spustí pracovní postup pomocí Policy4 aplikace pomocí imperativní kód C# (žádné [!INCLUDE[wf1](../../../../includes/wf1-md.md)] návrháře použít).|**ApplyDiscount.rules**: soubor s [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definice pravidla.<br /><br /> **Order.cs**: typ, který reprezentuje pořadí od zákazníků. Pravidla objekty tohoto typu.<br /><br /> **Program.cs**: konfiguruje a spouští pracovní postup, který má aktivita Policy4 použít pravidla definovaná v ApplyDiscount.rules k instancím objektů pořadí.<br /><br /> **App.config**: konfigurační soubor s cestu k souboru pravidla.|  
|DesignerClientSample|Ukázková aplikace klienta, která slouží ke konfiguraci a spustí pracovní postup pomocí aplikace Policy4 v [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer.|**Sequence1.XAML**: sekvenční pracovní postup, který používá aktivitu Policy4 k provedení pravidlo hodnocení.<br /><br /> `Program.cs`: Běží instance pracovního postupu definované v Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>Policy4 aktivity  
 Aktivita Policy4 je třída, která je odvozena z <xref:System.Activities.NativeActivity%601> pracovní postupy pro spuštění, který umožňuje [!INCLUDE[wf1](../../../../includes/wf1-md.md)] sady pravidel. Následující příklad kódu je zjednodušená definice veřejné OM aktivity.  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|Sada pravidel pro|WF [RuleSet třída](http://go.microsoft.com/fwlink/?LinkId=150379) pro rozhraní .NET Framework 3.5, který se má vyhodnotit při provedení aktivity.|  
|TargetObject|Objekt, pro kterou pravidla v [RuleSet třída](http://go.microsoft.com/fwlink/?LinkId=150379) vyhodnocují.|  
|ValidationError|Seznam chyb ověření vrácené [!INCLUDE[wf1](../../../../includes/wf1-md.md)] stroj pravidel pro rozhraní .NET Framework 3.5 při ověření [RuleSet třída](http://go.microsoft.com/fwlink/?LinkId=150379) proti cílový objekt před spuštěním.|  
  
## <a name="policy4-activity-designer"></a>Návrhář aktivity Policy4  
 Návrhář Policy4 přidá možnosti konfigurace aktivity Policy4 bez nutnosti psaní kódu. Po sestavení řešení, se nachází v panelu nástrojů v části **Microsoft.Samples.Activities.Rules**.  
  
 Návrhář WF můžete konfigurovat cílový objekt a sada pravidel pro. Když **upravit RuleSet** po kliknutí na tlačítko, WF [RuleSetDialog třída](http://go.microsoft.com/fwlink/?LinkId=150378) pro [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] se zobrazí. Toto dialogové okno je znovu hostované [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] editoru pravidel. Pomocí editoru vytvořte a upravte pravidla, která provede Policy4 aktivity.  
  
## <a name="using-this-sample"></a>Pomocí této ukázky  
 Ke spuštění této ukázce je vyžadováno žádné speciální nastavení. Stačí otevřít řešení v sadě Visual Studio a stisknutím klávesy F5 spusťte aplikaci.  
  
 Tato ukázka obsahuje dva klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit aktivitu Policy40 pomocí imperativní kód C#. DesignerClientSample ukazuje, jak nakonfigurovat a spustit aktivitu Policy4 pomocí návrháře.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Ke spuštění klienta aplikace ImperativeCodeClientSample  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4Sample.sln.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ImperativeCodeClientSample** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
3.  Chcete-li spustit projekt, stiskněte CTRL + F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Ke spuštění klienta aplikace ImperativeCodeClientSample  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4Sample.sln.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DesignerClientSample** projektu.  
  
    -   Vyberte **nastavit jako spouštěný projekt**.  
  
3.  Kompilace projektu, stiskněte CTRL + SHIFT + B.  
  
4.  Chcete-li spustit projekt, stiskněte CTRL + F5.