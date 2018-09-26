---
title: Integrace WPF a WF v XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 619f3b7ce2b854e27fe9229fd08727627ce37f1a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210055"
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
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WPFWFIntegration.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
4.  Do dialogového okna zadejte své jméno a příjmení.  
  
5.  Zavřete dialogové okno a konzole vypisuje své jméno.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`