---
title: Uchování aplikace pracovního postupu
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: 0c225a9ed56a742fce0aaff3704bab31dabb0b9a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500001"
---
# <a name="persisting-a-workflow-application"></a>Uchování aplikace pracovního postupu
Tato ukázka předvádí, jak spustit <xref:System.Activities.WorkflowApplication>uvolněn, když dostane nečinnosti a pak znovu načtěte ji chcete-li pokračovat v jeho provádění.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 <xref:System.Activities.WorkflowApplication> je hostitel pro instanci jednoho pracovního postupu, která poskytuje jednoduché rozhraní a některé z běžnějších scénáře hostingu umožňuje. Jeden takový scénář je dlouhý spouštění pracovních postupů, zjednodušuje tím trvalosti. Hostitelský ovládací prvek trvalého se provádí buď pomocí volání operace trvalosti u <xref:System.Activities.WorkflowApplication>, nebo pomocí manipulace <xref:System.Activities.WorkflowApplication> událostí a označující, že <xref:System.Activities.WorkflowApplication> byste neměli zachovat.  
  
 Ukázkový pracovní postup je <xref:System.Activities.Statements.WriteLine> aktivity výzvy k zadání názvu, `ReadLine` aktivity pro příjem názvu jako vstup prostřednictvím opětovné <xref:System.Activities.Bookmark>a další <xref:System.Activities.Statements.WriteLine> pro zobrazování pozdrav uživateli. Při čekání na vstup je pracovní postup, nabízí bod přirozené pro trvalost. To se často označuje jako <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> bodu. <xref:System.Activities.WorkflowApplication> Vyvolá <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> událost pokaždé, když se program pracovního postupu můžete nastavit jako trvalý, čeká na obnovení záložku a žádná další práce je prováděna. V pracovním postupu této ukázce, který bod je okamžitě po `ReadLine` aktivity začne spouštět.  
  
 A <xref:System.Activities.WorkflowApplication> nastaven na provedení trvalé uložení <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. Tento příklad používá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Se musí přiřadit <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost před <xref:System.Activities.WorkflowApplication> běží.  
  
 Ukázka přidá obslužná rutina <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> událostí. Označuje obslužnou rutinu pro tuto událost, co <xref:System.Activities.WorkflowApplication> by měl provádět tak, že vrací <xref:System.Activities.PersistableIdleAction>. Když <xref:System.Activities.PersistableIdleAction.Unload> se vrátí <xref:System.Activities.WorkflowApplication> je uvolněna.  
  
 Ukázka pak přijímá vstup od uživatele a načte trvalá pracovního postupu do nového <xref:System.Activities.WorkflowApplication>. Dělá to tak, že vytvoříte nový <xref:System.Activities.WorkflowApplication>, opakované vytvoření <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`a přidružení dokončené a uvolněné události k instanci a následným voláním <xref:System.Activities.WorkflowApplication.Load%2A> s identifikátorem instance cílového pracovního postupu. Jakmile je získat instanci, `ReadLine` obnovení aktivity záložku. Pracovního postupu vykonává spuštění v rámci `ReadLine` aktivity a běží na dokončení. Po dokončení pracovního postupu a uvolní, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` je volána jednou odstranit pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
     Tato ukázka vyžaduje SQL Server Express, který je nainstalovaný ve výchozím nastavení se [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Přejděte do adresáře vzorku (\WF\Basic\Persistence\InstancePersistence\CS) a spusťte CreateInstanceStore.cmd.  
  
    > [!CAUTION]
    >  Skript CreateInstanceStore.cmd pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete nainstalovat databázi na jinou instanci, upravte skript tak učinit.  
  
3.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Persistence.sln a stiskněte klávesu CTRL + SHIFT + B na jejich vytváření.  
  
    > [!CAUTION]
    >  Pokud jste nainstalovali databázi na jinou než výchozí instanci systému SQL Server, aktualizujte připojovací řetězec v kódu před sestavením řešení.  
  
4.  Spusťte ukázku s oprávněními správce tak, že přejdete do adresáře bin projektu (\WF\Basic\Persistence\InstancePersistence\bin\Debug) v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], Workflow.exe pravým tlačítkem myši a vyberete **spustit jako správce**.  
  
#### <a name="to-remove-the-instance-store-database"></a>K odebrání instance databáze úložiště  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do adresáře vzorku a spuštění RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
