---
title: Aktivita Policy v rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
ms.openlocfilehash: 9d8983f2f1d3f75beffeacfff4b673f6c23c4204
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508950"
---
# <a name="policy-activity-in-net-framework-45"></a>Aktivita Policy v rozhraní .NET Framework 4.5
Aktivita Policy4 umožňuje Windows Workflow Foundation v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objektů, který se má použít v modelu Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí stroj pravidel, která se dodává v WF 3.5. Pomocí této aktivity může vytvářet a spouštět WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>. Další informace o stroj pravidel 3.5 WF zahrnutý jako součást modelu Windows Workflow Foundation přečtěte si úvod do pravidla modul Windows Workflow Foundation. Další informace o migraci pravidla, která WF v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], přečtěte si prosím [pokyny k migraci](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
  
|Název projektu|Popis|Hlavní soubory|  
|------------------|-----------------|----------------|  
|Policy4|Obsahuje aktivitu Policy4 a jeho [!INCLUDE[wf1](../../../../includes/wf1-md.md)] návrháře.|**Policy4.cs**: Policy4 definici aktivity.<br /><br /> **PolicyDesigner.xaml**: vlastního návrháře aktivity Policy4. Použije pravidla editor ([RuleSetDialog třídy](https://go.microsoft.com/fwlink/?LinkId=150378)) z [!INCLUDE[wf1](../../../../includes/wf1-md.md)] stroj pravidel.|  
|ImperativeCodeClientSample|Ukázková aplikace klienta, který konfiguruje a spustí pracovní postup pomocí Policy4 aplikace pomocí imperativního kódu jazyka C# (žádné [!INCLUDE[wf1](../../../../includes/wf1-md.md)] návrháře použít).|**ApplyDiscount.rules**: soubor s [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pravidlo definice.<br /><br /> **Order.cs**: typ, který představuje zákazníka objednávky. Pravidla se aplikují na objekty tohoto typu.<br /><br /> **Soubor program.cs**: nakonfiguruje a spustí pracovní postup, který obsahuje aktivitu Policy4 použití pravidel definovaných v ApplyDiscount.rules do instance pořadí objektů.<br /><br /> **App.config**: konfigurační soubor s cestou souboru pravidel.|  
|DesignerClientSample|Ukázková klientská aplikace, který konfiguruje a spustí pomocí Policy4 aplikace v pracovním postupu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] návrháře.|**Sequence1.XAML**: sekvenční pracovní postup, který používá aktivitu Policy4 k provedení vyhodnocení pravidla.<br /><br /> `Program.cs`: Spustí instanci pracovního postupu definované v Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>Aktivita Policy4  
 Aktivita Policy4 je třída, která je odvozena z <xref:System.Activities.NativeActivity%601> pracovní postupy pro spuštění, který umožňuje [!INCLUDE[wf1](../../../../includes/wf1-md.md)] sady pravidel. Následující příklad kódu je zjednodušenou definici veřejné OM aktivity.  
  
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
|Sady pravidel|WF [třídy sady pravidel](https://go.microsoft.com/fwlink/?LinkId=150379) pro rozhraní .NET Framework 3.5 k vyhodnocení, když při spuštění této aktivity.|  
|TargetObject|Objekt, proti kterému pravidla v [třídy sady pravidel](https://go.microsoft.com/fwlink/?LinkId=150379) jsou vyhodnocovány.|  
|ValidationError|Seznam chyb ověření vrácené [!INCLUDE[wf1](../../../../includes/wf1-md.md)] stroj pravidel pro rozhraní .NET Framework 3.5 při ověřování [třídy sady pravidel](https://go.microsoft.com/fwlink/?LinkId=150379) proti cílové objektů před spuštěním.|  
  
## <a name="policy4-activity-designer"></a>Návrhář aktivity Policy4  
 Návrhář Policy4 přidává možnost konfigurace aktivity Policy4 bez nutnosti psát kód. Po sestavení řešení, ho najdete v sadě nástrojů v části **Microsoft.Samples.Activities.Rules**.  
  
 WF Návrhář umožňuje nakonfigurovat cílového objektu a sady pravidel. Když **sady pravidel upravit** po kliknutí na tlačítko, WF [RuleSetDialog třídy](https://go.microsoft.com/fwlink/?LinkId=150378) pro [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] se zobrazí. Toto dialogové okno je znovu hostované [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Editor pravidel. Pomocí editoru můžete vytvářet a upravovat pravidla, která se spustí aktivita Policy4.  
  
## <a name="using-this-sample"></a>Pomocí této ukázky  
 Žádné speciální nastavení se vyžaduje pro spuštění této ukázky. Stačí otevřít řešení v sadě Visual Studio a stisknutím klávesy F5 spusťte aplikaci.  
  
 Tato ukázka obsahuje dva klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit Policy40 aktivitu pomocí jazyka C# imperativního kódu. DesignerClientSample ukazuje, jak nakonfigurovat a spustit Policy4 aktivitu pomocí návrháře.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Ke spuštění ImperativeCodeClientSample klientské aplikace  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4Sample.sln.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ImperativeCodeClientSample** projektu a pak vyberte **nastavit jako spouštěný projekt**.  
  
3.  Spusťte projekt, stiskněte CTRL + F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Ke spuštění ImperativeCodeClientSample klientské aplikace  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení Policy4Sample.sln.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **DesignerClientSample** projektu.  
  
    -   Vyberte **nastavit jako spouštěný projekt**.  
  
3.  Ke kompilaci projektu, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
4.  Spusťte projekt, stiskněte CTRL + F5.