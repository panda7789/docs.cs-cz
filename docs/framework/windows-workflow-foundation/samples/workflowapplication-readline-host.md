---
title: Hostitel metody ReadLine pro WorkflowApplication
ms.date: 03/30/2017
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
ms.openlocfilehash: 4388ff0285de58b0dc6f86af93aad84b2894373f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502932"
---
# <a name="workflowapplication-readline-host"></a>Hostitel metody ReadLine pro WorkflowApplication
Tato ukázka je obecný hostitel metody ReadLine. Můžete načíst a spustit jakýkoli pracovní postup pomocí zahrnutou `ReadLine` aktivity (nebo jiné aktivity jako, které získávají data z záložky pokračuje s řetězce). Výstup `WriteLine` aktivity nebo cokoli zápisu do <xref:System.Activities.Statements.WriteLine.TextWriter%2A> rozšíření se přesměruje do okna hostitele. Při nečinnosti instance, k dispozici záložky pro tuto instanci se zobrazují v poli se seznamem. Vyberete záložku, zadejte nějaký text a stisknutím tlačítka záložku obnovení pokračovat v provádění pracovního postupu. Můžete také zrušit, přerušení nebo vybraný pracovní postup bude ukončen. Trvalost je ve výchozím – můžete vypnout hostitele a znovu a naplnění seznamu instanci s instancí uložených v databázi. Sledování se používá k výstupu <xref:System.Activities.WorkflowApplication>– úroveň události na hostitele s možností přidat podrobné sledování na úrovni aktivity.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Existují dvě vrstvy k tomuto hostiteli: zobrazení a vedoucí instanci. Zobrazení se skládá z `HostView` a `WorkflowApplicationInfo` třídy. Je obecný vzor pro tohoto hostitele `HostView` třídy a zobrazte dostupné možnosti pro uživatele na základě `WorkflowApplicationInfo` objekty, které jsou přiměřeně zachovány v synchronizaci se sadou instancí, které představují. Správce vrstvy instance se skládá z `WorkflowApplicationManager` třídu, která je jádrem veškerá komunikace hostitele, a `WorkflowDefinitionExtension` třídu, která přetrvává vztah mezi instance a definici program byl spuštěn s a několik jiných tříd. `HostView` Volání řízení operací na `WorkflowApplicationManager`. Tato volání jsou obvykle asynchronní udržovat responzivní uživatelské rozhraní. Pokud asynchronní volání dokončení `WorkflowApplicationManager` zavolá zpět do zobrazení vrstvy prostřednictvím dobře definovaných rozhraní (`IHostView`). `HostView` Třída nejčastěji odešle tato volání z `WorkflowApplicationManager` třídy na vlákně uživatelského rozhraní. Psaní textu slouží k bezpečné pro vlákna <xref:System.Activities.Statements.WriteLine.TextWriter%2A> objekty poskytované `HostView` třídy. Uživatelské rozhraní není jediné, co generujících události. <xref:System.Activities.WorkflowApplication> Objekty také signalizuje, že `WorkflowApplicationManager` při otevření `Idle`, `Complete`, nebo jsou `Aborted`, např. `WorkflowApplicationManager` Třídy získá mimo vlákno události čištění rozesílání nebo aktualizuje pracovní k hostiteli.  
  
 Nahrávání souboru použitý ke spuštění <xref:System.Activities.WorkflowApplication> usnadňují `WorkflowDefinitionExtension` třídy. Implementuje <xref:System.Activities.Persistence.PersistenceIOParticipant> rozhraní k účasti v trvalosti a zachovat cestu k definici pracovního postupu.  
  
 `WorkflowApplicationManager.Load` Metoda používá k vytvoření instance vyžaduje pro načítání nedokončené programy pracovního postupu uložená cesta <xref:System.Activities.WorkflowApplication> objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Tato ukázka vyžaduje systém SQL Express k instalaci. Systém SQL Express se dodává s [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Otevřete příkazový řádek sady Visual Studio 2010.  
  
3.  Přejděte do adresáře vzorku (\WF\Basic\Execution\ControllingWorkflowApplications) a spusťte CreateInstanceStore.cmd.  
  
4.  Skript CreateInstanceStore.cmd pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete nainstalovat databázi na jinou instanci, upravte skript tak učinit.  
  
5.  Kompilace projektu WorkflowApplicationReadLineHost a spuštění z příkazového řádku.  
  
6.  Po spuštění, můžete volitelně zapnout stálost nebo vypnutí. Dále můžete volitelně zapnout podrobné aktivit nebo vypnout sledování.  
  
7.  Stiskněte tlačítko se třemi tečkami vedle **spustit** tlačítko Procházet pro pracovní postup definovaný v souboru XAML  
  
     Dvě ukázkové najdete ve složce SampleWorkflows. Příklad parallel1.xaml přejde nečinnosti.  
  
8.  Po výběru je příklad, stiskněte **spustit** tlačítko.  
  
9. Pokud nebo přechodu pracovního postupu nečinnosti, **záložky** – pole se seznamem se vyplní dostupné záložky.  
  
10. V tomto okamžiku jsou možnosti obnovení záložku, zrušení, přerušení nebo ukončení pracovního postupu. Můžete také vypnout hostitele a restartujte ji. Pokud je na stálost, instance jsou při ukončení a projekt znovu nenačtete v nabídce start nahoru.  
  
     Pokud chcete obnovit záložku, vyberte požadovaný záložku, zadejte hodnotu v textovém poli vedle pole se seznamem a stiskněte klávesu **obnovit záložku**.  
  
#### <a name="to-remove-the-instance-store-database"></a>K odebrání instance databáze úložiště  
  
1.  Otevřete příkazový řádek sady Visual Studio 2010.  
  
2.  Přejděte do adresáře vzorku (\WF\Basic\Execution\ControllingWorkflowApplications) a spusťte RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`