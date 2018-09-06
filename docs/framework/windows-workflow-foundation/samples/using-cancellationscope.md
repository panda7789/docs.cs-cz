---
title: Použití CancellationScope
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 82d44fff869f207c09dc7685fc3470630e001a59
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731518"
---
# <a name="using-cancellationscope"></a>Použití CancellationScope
Tato ukázka předvádí, jak používat <xref:System.Activities.Statements.CancellationScope> aktivitu pro práci v aplikaci zrušit.  
  
 Mnoho komponenty střední vrstvy a služby závisí na dobře známé programovací konstrukce transakcí ke zpracování zrušení pro ně.  Ale existuje mnoho situací, ve kterých je nutné zrušit práce, kterou nelze provést v transakci.  Pomocí zrušení je obtížnější než při použití transakcí, protože musí nejprve sledovat práci, která musí být ukončena. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] tím, že poskytuje vám pomůže s tímto <xref:System.Activities.Statements.CancellationScope> aktivity.  
  
 Zrušení může být buď v rámci aktivity nebo z nadřazeného objektu aktivity aktivuje.  Podřízené aktivity se plánují pomocí jejich nadřazené aktivity (například <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, nebo vlastní složených aktivit).  Nadřazená aktivita může zrušit podřízené aktivity z jakéhokoli důvodu.  Například <xref:System.Activities.Statements.Parallel> aktivitu se tři větve zruší zbývající podřízené větve pokaždé, když se dokončí větve a <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> výraz vyhodnocen jako `true`. Pracovní postup lze také zrušit externě hostitelskou aplikací voláním <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Použít <xref:System.Activities.Statements.CancellationScope> aktivity, umístěte práce, kterou je potřeba zrušit do <xref:System.Activities.Statements.CancellationScope.Body%2A> vlastnost a put, která je provedena po zrušení do práce <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> vlastnost.  
  
 V této ukázce zrušení aktivitu z v rámci samotného aktivity.  
  
 Následující příklad používá k předvedení scénář <xref:System.Activities.Statements.CancellationScope> aktivita je chce koupit lístek a Miami co nejdříve klienta. Existují dvě cesty instituce, které mají firmy. Ukázka používá dva <xref:System.Activities.Statements.CancellationScope> v rámci <xref:System.Activities.Statements.Parallel> aktivity pro modelování tato obchodní logiku. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> z <xref:System.Activities.Statements.Parallel> aktivity je nastavený na `true`; od <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> je zaškrtnuto, až se dokončí všechny větve, to způsobí, že zbývající větev zruší po dokončení první větev. Klientská aplikace žádá obou úřady koupit-the-ticket, a když první z nich potvrdí, že byl koupil(a)-the-ticket, aplikace zruší pořadí na daná agentura.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CancelationScopeXAML.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`