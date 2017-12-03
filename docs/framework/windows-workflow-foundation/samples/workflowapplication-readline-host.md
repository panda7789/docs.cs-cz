---
title: WorkflowApplication ReadLine hostitele
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1ba33dff4be8ae3e75ee4d1873feeb4d5e5944b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflowapplication-readline-host"></a>WorkflowApplication ReadLine hostitele
Tato ukázka je obecný ReadLine hostitele. Můžete načíst a spustit žádný pracovní postup pomocí zahrnutou `ReadLine` aktivity (nebo ostatní aktivity, jako je získávající data z záložky pokračuje s řetězce). Výstup z `WriteLine` aktivity nebo nic zápis do <xref:System.Activities.Statements.WriteLine.TextWriter%2A> rozšíření se nasměruje do okna hostitele. Při nečinnosti instance, k dispozici záložky u dané instance se objeví v poli se seznamem. Vyberte záložku, vložení textu, některé a kliknutím na tlačítko Obnovit záložku pokračovat v provádění pracovního postupu. Můžete také zrušit, zrušení nebo ukončení vybrané pracovního postupu. Trvalost je ve výchozím – můžete vypnout hostitele a vrátí ji zpět a naplnění seznamu instanci s instancemi uloženy v databázi. Sledování se používá k výstupu <xref:System.Activities.WorkflowApplication>-úroveň události na hostitele s možností přidat podrobné sledování na úrovni aktivity.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Existují dvě vrstvy pro tohoto hostitele: zobrazení a správce instance. Zobrazení se skládá z `HostView` a `WorkflowApplicationInfo` třídy. Obecné vzor pro tohoto hostitele je pro `HostView` zobrazíte dostupné možnosti pro uživatele na základě `WorkflowApplicationInfo` objekty, které jsou zachovány přiměřeně v synchronizaci se instance představují. Vrstva manager instance se skládá z `WorkflowApplicationManager` třída, která je základní veškerá komunikace hostitele, a `WorkflowDefinitionExtension` několik dalších třídy a třídy, která potrvají vztah mezi instance a definice program byl spuštěn s. `HostView` Volání řízení operací na `WorkflowApplicationManager`. Tyto volání jsou obvykle asynchronní udržovat reagující uživatelské rozhraní. Když asynchronní volání dokončení `WorkflowApplicationManager` provádí volání zpět do zobrazení vrstvy přes dobře definované rozhraní (`IHostView`). `HostView` Třída nejčastěji odešle tyto volání z `WorkflowApplicationManager` třída pro uživatelské rozhraní vlákno. Zápis textu se provádí pro bezpečné pro přístup z více vláken <xref:System.Activities.Statements.WriteLine.TextWriter%2A> objektů poskytované `HostView` třídy. Uživatelské rozhraní není jediné, co generování událostí. <xref:System.Activities.WorkflowApplication> Objekty také signál `WorkflowApplicationManager` když přejde `Idle`, `Complete`, nebo jsou `Aborted`, např. `WorkflowApplicationManager` Třída získá vypnout vlákno událost odeslání vyčistit nebo aktualizaci pracovní na hostitele.  
  
 Nahrávání souboru použitý ke spuštění <xref:System.Activities.WorkflowApplication> usnadňují `WorkflowDefinitionExtension` třídy. Implementuje <xref:System.Activities.Persistence.PersistenceIOParticipant> rozhraní pro účast v trvalosti a zachovat cestu k definice pracovního postupu.  
  
 `WorkflowApplicationManager.Load` Metoda používá k vytvoření instance vyžaduje pro načítání nedokončené programy pracovního postupu uloženou cestu <xref:System.Activities.WorkflowApplication> objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka vyžaduje systém SQL Express k instalaci. SQL Express se dodává s [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Otevřete příkazový řádek sady Visual Studio 2010.  
  
3.  Přejděte do adresáře ukázkové (\WF\Basic\Execution\ControllingWorkflowApplications) a spusťte CreateInstanceStore.cmd.  
  
4.  Skript CreateInstanceStore.cmd se pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete pro instalaci databáze na jinou instanci, upravte skript tak, aby tak.  
  
5.  Kompilace projektu WorkflowApplicationReadLineHost a potom ho spusťte z příkazového řádku.  
  
6.  Po spuštění, můžete volitelně zapnout stálost nebo vypnout. Navíc můžete volitelně zapnout podrobné aktivity sledování zapnout nebo vypnout.  
  
7.  Stiskněte tlačítko se třemi tečkami vedle **spustit** tlačítko procházení pro pracovní postup definované v souboru XAML  
  
     Dvou vzorcích naleznete ve složce SampleWorkflows. Příklad parallel1.xaml přejde nečinnosti.  
  
8.  Po výběru je příklad, stiskněte **spustit** tlačítko.  
  
9. Pokud nebo nečinné, přejde pracovního postupu **záložky** – pole se seznamem se zobrazí v dostupné záložky.  
  
10. V tomto okamžiku jsou možnosti obnovit záložku, zrušení, zrušení nebo ukončení pracovního postupu. Můžete také vypnout hostitele a restartujte ji. Pokud je na stálost, instance jsou uvolněny na vypnutí nebo při spuštění nahoru.  
  
     Chcete-li obnovit záložku, vyberte požadovanou záložku, zadejte hodnotu v textovém poli vedle pole se seznamem a stiskněte klávesu **obnovit záložku**.  
  
#### <a name="to-remove-the-instance-store-database"></a>K odebrání instance úložiště databáze  
  
1.  Otevřete příkazový řádek sady Visual Studio 2010.  
  
2.  Přejděte do adresáře ukázkové (\WF\Basic\Execution\ControllingWorkflowApplications) a spusťte RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`