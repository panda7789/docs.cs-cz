---
title: Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
ms.openlocfilehash: 8fd08c9c29f7a268170aaa101a9bdb85250157dc
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094628"
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5

Tato ukázka předvádí, jak aktivita ExternalizedPolicy4 umožňuje spouštět existující .NET Framework 3,5 programovací model Windows Workflow Foundation (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objektů v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] programovací model Windows Workflow Foundation (WF 4,5) přímo pomocí modulu pravidel, který je dodán v WF 3,5. Pomocí této aktivity můžete otevřít a spustit všechny existující <xref:System.Workflow.Activities.Rules.RuleSet>WF 3,5. Další informace o modulu pravidel WF 3,5, který je součástí programovací model Windows Workflow Foundation, najdete v tématu [Úvod do modulu programovací model Windows Workflow Foundation Rules](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480193(v=msdn.10)). Další informace o migraci pravidel [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]najdete v tématu pokyny k [migraci](../migration-guidance.md).

## <a name="projects-in-this-sample"></a>Projekty v této ukázce

|Název projektu|Popis|Hlavní soubory|
|-|-|-|
|ExternalizedPolicy4|Obsahuje aktivitu ExternalizedPolicy4 a její modul WF 4,5 Designer.|**ExternalizedPolicy4.cs**: definice aktivity.<br /><br /> **ExternalizedPolicy4Designer. XAML**: vlastní Návrhář pro aktivitu ExternalizedPolicy4. Používá editor pravidel (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) z stroje WF 3,5 Rules.|
|ImperativeCodeClientSample|Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup pomocí aplikace ExternalizedPolicy4 C# s použitím imperativního kódu (bez použití návrháře).|**ApplyDiscount. Rules**: soubor s definicemi [!INCLUDE[wf1](../../../../includes/wf1-md.md)]ch pravidel.<br /><br /> **Order.cs**: typ, který reprezentuje objednávku zákazníka. Pravidla se aplikují na objekty tohoto typu.<br /><br /> **Program.cs**: konfiguruje a spustí pracovní postup, který má aktivitu Policy4 pro použití pravidel definovaných v ApplyDiscount. pravidla pro instance objektů Order.<br /><br /> App. config: konfigurační soubor s cestou k souboru pravidel.|
|DesignerClientSample|Ukázková klientská aplikace, která konfiguruje a spustí pracovní postup pomocí aplikace ExternalPolicy4 v Návrháři [!INCLUDE[wf1](../../../../includes/wf1-md.md)].|**Sequence1. XAML**: sekvenční pracovní postup, který používá aktivitu Policy4 k provádění hodnocení pravidel.<br /><br /> **Program.cs**: spustí instanci pracovního postupu definovaného v souboru Sequence1. XAML.|

## <a name="the-externalizedpolicy4-activity"></a>Aktivita ExternalizedPolicy4

Aktivita ExternalizedPolicy4 je <xref:System.Activities.NativeActivity>, která umožňuje spouštění objektů <xref:System.Workflow.Activities.Rules.RuleSet> WF 3,5 v rámci pracovních postupů WF 4,5. Následující příklad je zjednodušenou definicí modelu veřejného objektu aktivity.

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
|RuleSetFilePath|Cesta k souboru <xref:System.Workflow.Activities.Rules.RuleSet> .NET Framework 3,5, který se má vyhodnotit při spuštění aktivity.|
|RuleSetName|Název <xref:System.Workflow.Activities.Rules.RuleSet>, který se má použít v souboru. Rules.|
|TargetObject|Objekt, na kterém jsou <xref:System.Workflow.Activities.Rules.Rule> objekty v <xref:System.Workflow.Activities.Rules.RuleSet> vyhodnocovány proti.|
|ResultObject|Výsledný objekt po použití pravidel (například pravidla jsou použita proti vstupnímu argumentu a výsledek je uložen v argumentu výsledek.|
|ValidationError|Seznam chyb ověřování vrácených modulem pravidel WF 3,5 při ověřování <xref:System.Workflow.Activities.Rules.RuleSet> proti cílovému objektu před spuštěním.|

## <a name="externalizedpolicy4-activity-designer"></a>Návrhář aktivity ExternalizedPolicy4

Návrhář ExternalizedPolicy4 umožňuje konfigurovat aktivitu pro použití existující RuleSet bez psaní kódu. Stačí nastavit cestu, kde se nachází soubor. Rules, a zadat název <xref:System.Workflow.Activities.Rules.RuleSet>, který chcete použít. Umožňuje také upravit <xref:System.Workflow.Activities.Rules.RuleSet>. Po sestavení řešení je možné ho najít v sadě nástrojů v části Microsoft. Samples. Activities. Rules. Návrhář umožňuje vybrat soubor. Rules a <xref:System.Workflow.Activities.Rules.RuleSet>. Po kliknutí na tlačítko **Upravit RuleSet** se zobrazí <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> WF 3,5. Toto dialogové okno je znovu hostovaný Editor pravidel WF 3,5 a používá se k zobrazení a úpravám pravidel, která aktivita ExternalizedPolicy4 spouští.

## <a name="policy4-and-externalpolicy4"></a>Policy4 a ExternalPolicy4

Aktivita zásad umožňuje vytvořit a spustit .NET Framework 3,5 RuleSet v pracovním postupu WF 4,5. <xref:System.Workflow.Activities.Rules.RuleSet> je serializovaně vložen do definice XAML aktivity Policy4. Ukázka ExternalizedPolicy4 ukazuje, jak použít existující externí <xref:System.Workflow.Activities.Rules.RuleSet> (obsažená v souboru. Rules).

## <a name="use-this-sample"></a>Použít tuto ukázku

Ke spuštění této ukázky není nutné žádné speciální nastavení. Otevřete řešení v aplikaci Visual Studio a potom stisknutím klávesy **F5** spusťte aplikaci.

Tato ukázka obsahuje dvě klientské aplikace: ImperativeCodeClientSample a DesignerClientSample. Klient ImperativeCodeClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí C# imperativního kódu. DesignerClientSample ukazuje, jak nakonfigurovat a spustit aktivitu ExternalizedPolicy4 pomocí návrháře.

### <a name="run-the-imperativecodeclientsample-application"></a>Spuštění aplikace ImperativeCodeClientSample

1. Pomocí sady Visual Studio otevřete soubor řešení *Policy4Sample. sln* .

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **ImperativeCodeClientSample** a vyberte **nastavit jako spouštěný projekt**.

3. Chcete-li spustit projekt, stiskněte klávesu **Ctrl**+**F5**.

### <a name="run-the-designerclientsample-application"></a>Spuštění aplikace DesignerClientSample

1. Pomocí sady Visual Studio otevřete soubor řešení *Policy4Sample. sln* .

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **DesignerClientSample** a vyberte **nastavit jako spouštěný projekt**.

3. Pro zkompilování projektu stiskněte **kombinaci kláves Ctrl**+**SHIFT**+**B** .

4. Stisknutím **kombinace kláves Ctrl**+**F5** spusťte projekt.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.
>
> Tato ukázka se nachází v následujícím adresáři:
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
