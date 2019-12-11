---
title: Integrace WPF a WF v XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: b8015e5c526f58875beb58ab48a21c050bdc8a06
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960084"
---
# <a name="wpf-and-windows-workflow-foundation-integration-in-xaml"></a>Integrace WPF a programovací model Windows Workflow Foundation v jazyce XAML

Tento příklad ukazuje, jak vytvořit aplikaci, která používá funkce Windows Presentation Foundation (WPF) a programovací model Windows Workflow Foundation (WF) v jednom dokumentu XAML. K tomu ukázka používá rozšíření programovací model Windows Workflow Foundation a XAML.

## <a name="sample-details"></a>Podrobnosti ukázky

 Soubor: ShowWindow. XAML se deserializace do aktivity <xref:System.Activities.Statements.Sequence> se dvěma řetězcovými proměnnými, které jsou manipulovány aktivitami sekvence: `ShowWindow` a `WriteLine`. Výstup aktivity <xref:System.Activities.Statements.WriteLine> do okna konzoly, který výraz přiřadí vlastnosti <xref:System.Activities.Statements.WriteLine.Text%2A>. Aktivita `ShowWindow` zobrazuje okno WPF jako součást logiky provádění. <xref:System.Activities.ActivityContext.DataContext%2A> okna obsahuje proměnné deklarované v sekvenci. Ovládací prvky okna deklarované v aktivitě `ShowWindow` používají datovou vazbu k manipulaci s těmito proměnnými. Nakonec okno obsahuje ovládací prvek tlačítko. Událost `Click` pro tlačítko je zpracována <xref:System.Activities.ActivityDelegate> s názvem `MarkupExtension`, který obsahuje aktivitu `CloseWindow`. `MarkUpExtension` vyvolá obsaženou aktivitu, která poskytuje jako kontext všechny objekty identifikované `x:Name`a také <xref:System.Activities.ActivityContext.DataContext%2A> obsahujícího okna. Proto je možné `CloseWindow.InArgument<Window>` svázat pomocí výrazu, který odkazuje na název okna.

 Aktivita `ShowWindow` odvozena z <xref:System.Activities.AsyncCodeActivity%601> třídy pro zobrazení okna WPF a dokončení při zavření okna. Vlastnost `Window` je typu `Func<Window>`, který umožňuje vytvořit okno na vyžádání pro každé spuštění aktivity. Vlastnost `Window` používá <xref:System.Xaml.XamlDeferringLoader> k povolení tohoto odloženého zkušebního modelu. `FuncFactoryDeferringLoader` umožňuje zachytit `XamlReader` během serializace a pak číst během provádění aktivity.

 Dobře zapsaná aktivita nikdy neblokuje vlákno Scheduleru. Aktivitu `ShowWindow` však nelze dokončit, dokud nebude zavřeno okno, které zobrazuje. Aktivita `ShowWindow` dosahuje tohoto chování odvozením od <xref:System.Activities.AsyncCodeActivity>, voláním metody <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> v metodě <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a zobrazením okna v modálním případě. Delegát je vyvolán prostřednictvím <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>WPF. Aktivita `ShowWindow` přiřadí vlastnosti `Window.DataContext` vlastnost <xref:System.Activities.ActivityContext.DataContext%2A>, která poskytne přístup k proměnným v oboru dat ovládacími prvky.

 Poslední bod zájmu v této ukázce je <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> s názvem `DelegateActivityExtension`. Metoda `ProvideValue` tohoto rozšíření značek vrací delegáta, který vyvolá vloženou aktivitu. Tato aktivita běží v prostředí, které zahrnuje kontext dat WPF a všechny `x:Name` hodnoty v oboru. V metodě `GenericInvoke` se toto prostředí poskytuje aktivitě prostřednictvím rozšíření <xref:System.Activities.Hosting.SymbolResolver>. Toto rozšíření je přidáno do <xref:System.Activities.WorkflowInvoker>, který je poté použit k vyvolání vložené aktivity při vyvolání delegáta rozšíření značek.

> [!NOTE]
> Výchozí Návrhář nepodporuje aktivitu: ShowWindow; v takovém případě se soubor: ShowWindow. XAML nezobrazuje správně v návrháři.

## <a name="run-the-sample"></a>Spuštění ukázky

1. Pomocí sady Visual Studio otevřete soubor řešení WPFWFIntegration. sln.

2. Chcete-li vytvořit řešení, stiskněte klávesu **Ctrl**+**SHIFT**+**B**.

3. Pokud chcete řešení spustit, stiskněte klávesu **F5**.

4. Do dialogového okna zadejte jméno a příjmení.

5. Zavřete dialogové okno a v konzole se budou zobrazovat vaše jméno.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
