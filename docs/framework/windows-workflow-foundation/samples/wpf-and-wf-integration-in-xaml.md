---
title: WPF a integrace WF v jazyce XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 327efb0b829e2628328d2e324c0736f8cb423b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-and-wf-integration-in-xaml"></a>WPF a integrace WF v jazyce XAML
Tento příklad ukazuje, jak vytvořit aplikaci, která používá [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] a [!INCLUDE[wf](../../../../includes/wf-md.md)] funkce do jednoho dokumentu XAML. K tomu Ukázka používá [!INCLUDE[wf](../../../../includes/wf-md.md)] a rozšiřitelnost XAML.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Soubor ShowWindow.xaml deserializuje do <xref:System.Activities.Statements.Sequence> aktivitu se dvěma řetězec proměnné, které jsou s nimi manipulovat aktivitami pořadí: `ShowWindow` a `WriteLine`. <xref:System.Activities.Statements.WriteLine> Výstupem aktivity v okně konzoly výraz, který se přiřadí <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost. `ShowWindow` Zobrazí aktivity [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okno jako součást logiky provádění pravidla. <xref:System.Activities.ActivityContext.DataContext%2A> Okna zahrnuje proměnných deklarovaných v sekvenci. Ovládací prvky okna deklarované v `ShowWindow` aktivity použít datovou vazbu pro zpracování těchto proměnných. Nakonec okno obsahuje ovládací prvek tlačítko. `Click` Události pro tlačítko se zpracovává souborem <xref:System.Activities.ActivityDelegate> s názvem `MarkupExtension` obsahující `CloseWindow` aktivity. `MarkUpExtension`Vyvolá obsažené aktivity, která obsahuje všechny objekty identifikovaný jako kontext, `x:Name`, a taky <xref:System.Activities.ActivityContext.DataContext%2A> obsahující okna. Proto `CloseWindow.InArgument<Window>` může být svázán pomocí výraz, který odkazuje na název okna.  
  
 `ShowWindow` Aktivity je odvozena z <xref:System.Activities.AsyncCodeActivity%601> třída zobrazíte [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] okno a dokončení při zavření okna. `Window` Vlastnost je typu `Func<Window>` umožňuje okno vytvořit na vyžádání pro každé spuštění aktivity. `Window` Vlastnost používá <xref:System.Xaml.XamlDeferringLoader> povolit tento model odložené hodnocení. `FuncFactoryDeferringLoader` Umožňuje `XamlReader` zaznamenána během serializace a přečtěte si při provádění aktivity.  
  
 Aktivitu kvalitně nikdy blokuje podprocesu plánovače. Ale `ShowWindow` aktivity nelze dokončit, dokud nezavřete okno je zobrazení. `ShowWindow` Aktivity dosahuje toto chování odvozování z <xref:System.Activities.AsyncCodeActivity>, volání <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> metoda v <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metoda a modálně zobrazující okna. Delegát volání prostřednictvím WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Přiřadí aktivity <xref:System.Activities.ActivityContext.DataContext%2A> vlastnost, která má `Window.DataContext` vlastnost zajistit žádná data vázána řídí přístup k proměnné v oboru.  
  
 Je poslední bod týkající se v této ukázce <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> názvem `DelegateActivityExtension`. `ProvideValue` Metoda tohoto rozšíření značek vrátí delegáta, který vyvolá aktivitu embedded. Tato aktivita běží v prostředí, které obsahuje [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kontextu dat a všechny `x:Name` hodnoty v oboru. V `GenericInvoke` metoda, toto prostředí je zadán pro aktivity prostřednictvím <xref:System.Activities.Hosting.SymbolResolver> rozšíření. Toto rozšíření je přidán do <xref:System.Activities.WorkflowInvoker> , se pak použije k vyvolání embedded aktivity vždy, když je vyvolán delegát rozšíření značek.  
  
> [!NOTE]
>  Výchozí designer nepodporuje ShowWindow aktivity; jako takový soubor ShowWindow.Xaml nezobrazuje správně v návrháři.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WPFWFIntegration.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
4.  Zadejte název vaší první a poslední do dialogu.  
  
5.  Zavřete dialogové okno a vrátí konzole je vaše jméno.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`