---
title: Integrace WPF a WF v XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 188702cfc13d7e353238e108066cc3d5f1c8bda9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298640"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Integrace WPF a WF v XAML
Tento příklad ukazuje, jak vytvořit aplikaci, která využívá funkce Windows Presentation Foundation (WPF) a Windows Workflow Foundation (WF) v jednom dokumentu XAML. K tomu Ukázka používá rozšíření Windows Workflow Foundation (WF) a XAML.

## <a name="sample-details"></a>Ukázka podrobnosti
 Soubor ShowWindow.xaml deserializuje do <xref:System.Activities.Statements.Sequence> aktivity se dvěma proměnnými řetězce, které jsou manipulovat aktivity pořadí: `ShowWindow` a `WriteLine`. <xref:System.Activities.Statements.WriteLine> Výstupem aktivity do okna konzoly výraz, který přiřazuje <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost. `ShowWindow` Zobrazí aktivity [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okno jako součást logiky jeho spuštění. <xref:System.Activities.ActivityContext.DataContext%2A> Okna obsahuje proměnné deklarované v sekvenci. Ovládací prvky okna deklarované v `ShowWindow` aktivity použít datovou vazbu pro manipulaci s těchto proměnných. Nakonec v okně obsahuje ovládací prvek tlačítko. `Click` Zpracovává události pro tlačítko <xref:System.Activities.ActivityDelegate> s názvem `MarkupExtension` , který obsahuje `CloseWindow` aktivity. `MarkUpExtension` Spustí obsaženou aktivitu, která poskytuje všechny objekty identifikován jako kontext, `x:Name`, jakož i <xref:System.Activities.ActivityContext.DataContext%2A> nadřazeného okna. Proto `CloseWindow.InArgument<Window>` lze vázat vlastnosti autorefresh pomocí výrazu, který odkazuje na název v okně.

 `ShowWindow` Aktivity je odvozen od <xref:System.Activities.AsyncCodeActivity%601> třídy k zobrazení [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okno a ten se dokončí při zavření okna. `Window` Vlastnost je typu `Func<Window>` , který umožňuje v okně vytvořit na vyžádání pro každé spuštění aktivity. `Window` Používá vlastnost <xref:System.Xaml.XamlDeferringLoader> povolit tento model odložené hodnocení. `FuncFactoryDeferringLoader` Umožňuje `XamlReader` zaznamenána během serializace a pak si můžete přečíst během provádění aktivity.

 Kvalitně napsané aktivity nikdy blokuje vlákno plánovače. Ale `ShowWindow` aktivity nelze dokončit, dokud není zavřena oken se zobrazuje. `ShowWindow` Odvozený z tohoto chování dosahuje aktivity <xref:System.Activities.AsyncCodeActivity>, volání <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> metoda ve <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metoda a modálně zobrazení okna. Je delegát vyvolán pomocí WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Přiřadí aktivity <xref:System.Activities.ActivityContext.DataContext%2A> vlastnost `Window.DataContext` vlastnost poskytnout všechna data vázána řídí přístup k proměnným v oboru.

 Poslední bod zájmu v této ukázce je <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> volá `DelegateActivityExtension`. `ProvideValue` Delegáta, který vyvolá vložený aktivita vrátí metoda tohoto rozšíření značek. Tato aktivita spouští v prostředí, které zahrnuje [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kontext dat a všechny `x:Name` hodnoty v rozsahu. V `GenericInvoke` metoda, toto prostředí je k dispozici na aktivitu prostřednictvím <xref:System.Activities.Hosting.SymbolResolver> rozšíření. Tato přípona přidána <xref:System.Activities.WorkflowInvoker> , která se pak použije k vyvolání vloženého aktivity pokaždé, když je vyvolán delegát rozšíření značek.

> [!NOTE]
>  Výchozí návrhář nepodporuje ShowWindow aktivity; v důsledku toho soubor ShowWindow.Xaml nezobrazuje správně v návrháři.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor řešení WPFWFIntegration.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Abyste mohli spustit řešení, stiskněte klávesu F5.

4. Do dialogového okna zadejte své jméno a příjmení.

5. Zavřete dialogové okno a konzole vypisuje své jméno.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`