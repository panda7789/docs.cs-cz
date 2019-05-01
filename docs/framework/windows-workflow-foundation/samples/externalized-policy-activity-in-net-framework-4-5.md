---
title: Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 622b0f14281d5b068700d9e4fe03485aa1a60fcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005027"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5

Tato ukázka předvádí, jak aktivity ExternalizedPolicy4 umožňuje provádění existujících [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Windows Workflow Foundation (WF 4.5) přímo s použitím stroje pravidel která je dodávána s prostředím v WF 3.5. Pomocí této aktivity můžete otevřít a spustit všechny existující 3.5 WF <xref:System.Workflow.Activities.Rules.RuleSet>. Další informace o stroj pravidel 3.5 WF zahrnutý jako součást modelu Windows Workflow Foundation, přečtěte si prosím [Úvod do modul Windows Workflow Foundation pravidla](https://go.microsoft.com/fwlink/?LinkId=166079). Další informace o migraci pravidla pro [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], přečtěte si pokyny k migraci na [pokyny k migraci](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projekty v této ukázce

|Název projektu|Popis|Hlavní soubory|
|-|-|-|
|ExternalizedPolicy4|Obsahuje aktivitu ExternalizedPolicy4 a návrhář WF 4.5.|**ExternalizedPolicy4.cs**: definici aktivity.<br /><br /> **ExternalizedPolicy4Designer.xaml**: Vlastní návrháři ExternalizedPolicy4 aktivity. Použije pravidla editor (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z stroj pravidel 3.5 WF.|
|ImperativeCodeClientSample|Ukázková klientská aplikace, která konfiguruje a používá pracovního postupu pomocí ExternalizedPolicy4 aplikace pomocí imperativního kódu C# (žádný návrhář použít).|**ApplyDiscount.rules**: Soubor s [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pravidlo definice.<br /><br /> **Order.cs**: Typ, který představuje zákazníka objednávky. Pravidla se aplikují na objekty tohoto typu.<br /><br /> **Program.cs**: Konfiguruje a spustí pracovní postup, který obsahuje aktivitu Policy4 použití pravidel definovaných v ApplyDiscount.rules do instance pořadí objektů.<br /><br /> App.config: Konfigurační soubor s cestou souboru pravidel.|
|DesignerClientSample|Ukázková klientská aplikace, který konfiguruje a spustí pomocí ExternalPolicy4 aplikace v pracovním postupu [!INCLUDE[wf1](../../../../includes/wf1-md.md)] návrháře.|**Sequence1.XAML**: Sekvenční pracovní postup, který používá aktivitu Policy4 k provedení vyhodnocení pravidla.<br /><br /> **Program.cs**: Spuštění instance pracovního postupu definované v Sequence1.xaml.|

## <a name="the-externalizedpolicy4-activity"></a>Aktivita ExternalizedPolicy4

Aktivita ExternalizedPolicy4 <xref:System.Activities.NativeActivity> , která umožňuje provádění pracovního postupu 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> objektů v rámci pracovních postupů WF 4.5. Následující příklad je zjednodušený definice veřejných objektový model aktivity.

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
|RuleSetFilePath|Cesta k rozhraní .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> souboru má být vyhodnocen při spuštění aktivity.|
|RuleSetName|Název <xref:System.Workflow.Activities.Rules.RuleSet> pro použití v rámci souboru .rules.|
|TargetObject|Objekt, kterému <xref:System.Workflow.Activities.Rules.Rule> objekty v <xref:System.Workflow.Activities.Rules.RuleSet> je porovnán s.|
|ResultObject|Výsledný objekt po použití pravidla (třeba pravidla se použijí pro vstupní argument a výsledek je uložen v Result argument.|
|ValidationError|Seznam chyb ověřování vrácená strojem pravidel 3.5 WF při ověřování <xref:System.Workflow.Activities.Rules.RuleSet> proti cílové objektů před spuštěním.|

## <a name="externalizedpolicy4-activity-designer"></a>Návrhář aktivity ExternalizedPolicy4

Návrhář ExternalizedPolicy4 umožňuje konfigurování aktivity pro použití existující sady pravidel bez psaní kódu. Stačí nastavit cestu, kde je umístěn soubor .rules a zadejte <xref:System.Workflow.Activities.Rules.RuleSet> název, který chcete použít. Také umožňuje upravovat <xref:System.Workflow.Activities.Rules.RuleSet>. Po sestavení řešení, můžete najít na panelu nástrojů v části Microsoft.Samples.Activities.Rules. Návrhář umožňuje výběr souboru .rules a <xref:System.Workflow.Activities.Rules.RuleSet>. Když **sady pravidel upravit** po kliknutí na tlačítko, WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> se zobrazí. Toto dialogové okno je znovu hostované editor pravidel WF 3.5 a slouží k zobrazení a úprava pravidla, která se spustí aktivita ExternalizedPolicy4.

## <a name="policy4-and-externalpolicy4"></a>Policy4 a ExternalPolicy4

Zásady aktivit umožňuje vytvořit a spustit sady pravidel rozhraní .NET Framework 3.5 v pracovním postupu WF 4.5. <xref:System.Workflow.Activities.Rules.RuleSet> Je serializovaná vložená v aktivitě Policy4 definice XAML. Ukázka ExternalizedPolicy4 ukazuje způsob použití stávající externí <xref:System.Workflow.Activities.Rules.RuleSet> (obsažené v souboru .rules).

## <a name="use-this-sample"></a>Pomocí této ukázky

Žádné speciální nastavení se vyžaduje pro spuštění této ukázky. Otevřete řešení v sadě Visual Studio a potom stiskněte klávesu **F5** ke spuštění aplikace.

Tato ukázka obsahuje dva klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit ExternalizedPolicy4 aktivitu pomocí jazyka C# imperativního kódu. DesignerClientSample ukazuje, jak nakonfigurovat a spustit ExternalizedPolicy4 aktivitu pomocí návrháře.

### <a name="run-the-imperativecodeclientsample-application"></a>Spusťte aplikaci ImperativeCodeClientSample

1. Pomocí sady Visual Studio, otevřete *Policy4sample.sln* soubor řešení.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ImperativeCodeClientSample** projektu a pak vyberte **nastavit jako spouštěný projekt**.

3. Chcete-li spustit projekt, stiskněte **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Spusťte aplikaci DesignerClientSample

1. Pomocí sady Visual Studio, otevřete *Policy4sample.sln* soubor řešení.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **DesignerClientSample** projektu a pak vyberte **nastavit jako spouštěný projekt**.

3. Stisknutím klávesy **Ctrl**+**Shift**+**B** ke kompilaci projektu.

4. Stisknutím klávesy **Ctrl**+**F5** spusťte projekt.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.
>
> Tato ukázka se nachází v následujícím adresáři:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
