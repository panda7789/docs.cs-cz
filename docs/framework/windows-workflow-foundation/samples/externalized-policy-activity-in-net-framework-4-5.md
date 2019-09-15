---
title: Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 7d3c9b2bd9da7e3793479c002094504a4a556aa0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989571"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5

Tato ukázka předvádí, jak aktivita ExternalizedPolicy4 umožňuje spouštět [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] stávající objekty programovací model Windows Workflow Foundation (WF <xref:System.Workflow.Activities.Rules.RuleSet> 3,5) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] v programovací model Windows Workflow Foundation (WF 4,5) přímo pomocí modulu pravidel. který je dodán na WF 3,5. Pomocí této aktivity můžete otevřít a spustit všechny existující WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet>. Další informace o modulu pravidel WF 3,5, který je součástí programovací model Windows Workflow Foundation, najdete v tématu [Úvod do modulu programovací model Windows Workflow Foundation Rules](https://go.microsoft.com/fwlink/?LinkId=166079). Další informace o migraci pravidel do nástroje [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]produktu najdete v pokynech k migraci v článku [pokyny](../migration-guidance.md)k migraci.

## <a name="projects-in-this-sample"></a>Projekty v této ukázce

|Název projektu|Popis|Hlavní soubory|
|-|-|-|
|ExternalizedPolicy4|Obsahuje aktivitu ExternalizedPolicy4 a její modul WF 4,5 Designer.|**ExternalizedPolicy4.cs**: definice aktivity.<br /><br /> **ExternalizedPolicy4Designer. XAML**: Vlastní Návrhář pro aktivitu ExternalizedPolicy4 Používá editor pravidel (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z stroje WF 3,5 Rules.|
|ImperativeCodeClientSample|Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup pomocí aplikace ExternalizedPolicy4 C# s použitím imperativního kódu (bez použití návrháře).|**ApplyDiscount. Rules**: Soubor s [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definicemi pravidla<br /><br /> **Order.cs**: Typ, který představuje objednávku zákazníka. Pravidla se aplikují na objekty tohoto typu.<br /><br /> **Program.cs**: Konfiguruje a spustí pracovní postup, který má aktivitu Policy4 pro použití pravidel definovaných v ApplyDiscount. pravidla pro instance objektů Order.<br /><br /> App.config: Konfigurační soubor s cestou k souboru pravidel.|
|DesignerClientSample|Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup pomocí aplikace ExternalPolicy4 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v návrháři.|**Sequence1. XAML**: Sekvenční pracovní postup, který používá aktivitu Policy4 k provádění hodnocení pravidel.<br /><br /> **Program.cs**: Spustí instanci pracovního postupu, která je definována v souboru Sequence1. XAML.|

## <a name="the-externalizedpolicy4-activity"></a>Aktivita ExternalizedPolicy4

Aktivita ExternalizedPolicy4 je <xref:System.Activities.NativeActivity> , která umožňuje spouštění objektů WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> v rámci pracovních postupů WF 4,5. Následující příklad je zjednodušenou definicí modelu veřejného objektu aktivity.

```csharp
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
|RuleSetFilePath|Cesta k souboru .NET Framework 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> , který se má vyhodnotit při spuštění aktivity.|
|RuleSetName|Název, <xref:System.Workflow.Activities.Rules.RuleSet> který se má použít v souboru. Rules.|
|TargetObject|Objekt, na kterém <xref:System.Workflow.Activities.Rules.Rule> <xref:System.Workflow.Activities.Rules.RuleSet> jsou vyhodnocovány objekty v objektu.|
|ResultObject|Výsledný objekt po použití pravidel (například pravidla jsou použita proti vstupnímu argumentu a výsledek je uložen v argumentu výsledek.|
|ValidationError|Seznam chyb ověřování vrácených modulem pravidel WF 3,5 při ověřování <xref:System.Workflow.Activities.Rules.RuleSet> proti cílovému objektu před spuštěním.|

## <a name="externalizedpolicy4-activity-designer"></a>Návrhář aktivity ExternalizedPolicy4

Návrhář ExternalizedPolicy4 umožňuje konfigurovat aktivitu pro použití existující RuleSet bez psaní kódu. Stačí nastavit cestu, kde se nachází soubor. Rules, a zadat <xref:System.Workflow.Activities.Rules.RuleSet> název, který chcete použít. Umožňuje také upravit <xref:System.Workflow.Activities.Rules.RuleSet>. Po sestavení řešení je možné ho najít v sadě nástrojů v části Microsoft. Samples. Activities. Rules. Návrhář umožňuje vybrat soubor. Rules a <xref:System.Workflow.Activities.Rules.RuleSet>. Když kliknete na tlačítko **Upravit RuleSet** , zobrazí se WF <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> 3,5. Toto dialogové okno je znovu hostovaný Editor pravidel WF 3,5 a používá se k zobrazení a úpravám pravidel, která aktivita ExternalizedPolicy4 spouští.

## <a name="policy4-and-externalpolicy4"></a>Policy4 a ExternalPolicy4

Aktivita zásad umožňuje vytvořit a spustit .NET Framework 3,5 RuleSet v pracovním postupu WF 4,5. <xref:System.Workflow.Activities.Rules.RuleSet> Je serializovaný vložený v definici XAML aktivity Policy4. Ukázka ExternalizedPolicy4 ukazuje, jak použít existující externí <xref:System.Workflow.Activities.Rules.RuleSet> (obsažený v souboru. Rules).

## <a name="use-this-sample"></a>Použít tuto ukázku

Ke spuštění této ukázky není nutné žádné speciální nastavení. Otevřete řešení v aplikaci Visual Studio a potom stisknutím klávesy **F5** spusťte aplikaci.

Tato ukázka obsahuje dvě klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí C# imperativního kódu. DesignerClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí návrháře.

### <a name="run-the-imperativecodeclientsample-application"></a>Spuštění aplikace ImperativeCodeClientSample

1. Pomocí sady Visual Studio otevřete soubor řešení *Policy4Sample. sln* .

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **ImperativeCodeClientSample** a vyberte **nastavit jako spouštěný projekt**.

3. Chcete-li spustit projekt, stiskněte klávesu **CTRL**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Spuštění aplikace DesignerClientSample

1. Pomocí sady Visual Studio otevřete soubor řešení *Policy4Sample. sln* .

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **DesignerClientSample** a vyberte **nastavit jako spouštěný projekt**.

3. Pro zkompilování projektu stiskněte **kombinaci kláves CTRL**+**SHIFT**+**B** .

4. Stisknutím klávesy **CTRL**+**F5** spusťte projekt.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.
>
> Tato ukázka se nachází v následujícím adresáři:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
