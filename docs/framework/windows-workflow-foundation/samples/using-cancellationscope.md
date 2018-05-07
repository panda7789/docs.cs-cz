---
title: Pomocí CancellationScope
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 62b798b29149e30a2fae680b507f62ef0a2e23d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-cancellationscope"></a>Pomocí CancellationScope
Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.CancellationScope> aktivity zrušit práci v aplikaci.  
  
 Mnoho střední vrstvy součástmi a službami spoléhají na známý programovací konstrukce transakcí pro zrušení pro jejich zpracování.  Existují však mnoha situacích, ve kterých je nutné zrušit práce, kterou nelze provést v transakci.  Pomocí zrušení je obtížnější než použití transakcí, protože nejprve musí být sledována práci, kterou je nutné zrušit. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] vám pomůže to tím, že poskytuje <xref:System.Activities.Statements.CancellationScope> aktivity.  
  
 Zrušení může být aktivována buď z aktivity nebo z nadřazené aktivity.  Podřízené aktivity jsou naplánovány podle jejich nadřazené aktivity (například <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, nebo vlastní aktivity složený).  Nadřazená aktivita, můžete zrušit podřízené aktivity z jakéhokoli důvodu.  Například <xref:System.Activities.Statements.Parallel> aktivitu tři větve zruší zbývající větve vždy, když dokončí větve a <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> výraz vyhodnocen jako `true`. Pracovní postup lze také zrušit externě hostitelskou aplikaci voláním <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Použít <xref:System.Activities.Statements.CancellationScope> aktivity, put, musí být zrušena do práce <xref:System.Activities.Statements.CancellationScope.Body%2A> vlastnost a put práci, kterou provádí po zrušení do <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> vlastnost.  
  
 Tento příklad znázorňuje zrušení aktivita z v rámci aktivity sám sebe.  
  
 Scénář, který ukázce se používá k předvedení <xref:System.Activities.Statements.CancellationScope> aktivity je klient chtějí koupit lístek do Opole co nejdříve. Existují dvě cestovní kanceláře, které mají firmy. Příklad používá dva <xref:System.Activities.Statements.CancellationScope> v rámci <xref:System.Activities.Statements.Parallel> aktivity pro modelování tento obchodní logiku. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> z <xref:System.Activities.Statements.Parallel> aktivity je nastavený na `true`; od <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> je zaškrtnuto, po dokončení všech větve, z tohoto důvodu zbývající větev, která má být zrušen po dokončení první větev. Klientská aplikace vás obě úřady koupit the-ticket a když první potvrdí, že má byly v rámci the-ticket, aplikace zruší pořadí v jiných agenturou.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CancelationScopeXAML.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`