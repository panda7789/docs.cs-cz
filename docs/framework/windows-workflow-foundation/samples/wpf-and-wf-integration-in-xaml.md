---
title: Integrace WPF a WF v XAML
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 547049488a1bf97d5f5ef03a71278b8f653293a2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045328"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>Integrace WPF a WF v XAML
Tento příklad ukazuje, jak vytvořit aplikaci, která používá funkce Windows Presentation Foundation (WPF) a programovací model Windows Workflow Foundation (WF) v jednom dokumentu XAML. K tomu ukázka používá programovací model Windows Workflow Foundation (WF) a rozšiřitelnost XAML.

## <a name="sample-details"></a>Podrobnosti ukázky
 Soubor: ShowWindow. XAML se deserializace do <xref:System.Activities.Statements.Sequence> aktivity se dvěma řetězcovými proměnnými, které jsou zpracovávány aktivitami sekvence: `ShowWindow` a. `WriteLine` Výstup aktivity do okna konzoly, který výraz přiřadí <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnosti. <xref:System.Activities.Statements.WriteLine> `ShowWindow` Aktivita zobrazí okno WPF jako součást logiky provádění. <xref:System.Activities.ActivityContext.DataContext%2A> Okno obsahuje proměnné deklarované v sekvenci. Ovládací prvky okna deklarované v `ShowWindow` aktivitě používají datovou vazbu k manipulaci s těmito proměnnými. Nakonec okno obsahuje ovládací prvek tlačítko. Událost pro tlačítko je zpracována <xref:System.Activities.ActivityDelegate> s názvem `MarkupExtension` , který obsahuje `CloseWindow` aktivitu. `Click` `MarkUpExtension`vyvolá obsaženou aktivitu, která poskytuje jako kontext všechny objekty, které jsou označeny objektem `x:Name`, a také v <xref:System.Activities.ActivityContext.DataContext%2A> obsahujícím okně. Proto je `CloseWindow.InArgument<Window>` možné svázat pomocí výrazu, který odkazuje na název okna.

 Aktivita je odvozena <xref:System.Activities.AsyncCodeActivity%601> z třídy pro zobrazení okna WPF a dokončení při zavření okna. `ShowWindow` Vlastnost je typu `Func<Window>` , který umožňuje, aby bylo okno vytvořeno na vyžádání pro každé spuštění aktivity. `Window` `Window` Vlastnost<xref:System.Xaml.XamlDeferringLoader> používá k povolení tohoto odloženého zkušebního modelu. `FuncFactoryDeferringLoader` Umožňujezachytitačístběhemserializaceapak`XamlReader` číst během provádění aktivity.

 Dobře zapsaná aktivita nikdy neblokuje vlákno Scheduleru. `ShowWindow` Aktivitu však nelze dokončit, dokud nebude zavřeno okno, které zobrazuje. Tato aktivita dosahuje tohoto chování odvozením z <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> voláním <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> metody v metodě a zobrazením okna v modálním okně. `ShowWindow` Delegát je vyvolán prostřednictvím WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Aktivita přiřazujevlastnost`Window.DataContext`vlastnosti , aby poskytovala libovolné datové vazby ovládací prvky pro přístup k proměnným v oboru. <xref:System.Activities.ActivityContext.DataContext%2A>

 Poslední bod zájmu v této ukázce je <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> volaný. `DelegateActivityExtension` `ProvideValue` Metoda tohoto rozšíření značek vrací delegáta, který vyvolá vloženou aktivitu. Tato aktivita běží v prostředí, které zahrnuje kontext dat WPF a všechny `x:Name` hodnoty v oboru. V metodě je toto prostředí poskytováno aktivitě <xref:System.Activities.Hosting.SymbolResolver> prostřednictvím rozšíření. `GenericInvoke` Toto rozšíření se přidá do <xref:System.Activities.WorkflowInvoker> , které se pak použije k vyvolání vložené aktivity při vyvolání delegáta rozšíření značek.

> [!NOTE]
> Výchozí Návrhář nepodporuje aktivitu: ShowWindow; v takovém případě se soubor: ShowWindow. XAML nezobrazuje správně v návrháři.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení WPFWFIntegration. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

4. Do dialogového okna zadejte jméno a příjmení.

5. Zavřete dialogové okno a v konzole se budou zobrazovat vaše jméno.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
