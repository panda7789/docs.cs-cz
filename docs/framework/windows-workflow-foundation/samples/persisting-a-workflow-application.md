---
title: "Setrvání pracovního postupu aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16251bcf5ceb9660fc4854c8e46bc376de9f01ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="persisting-a-workflow-application"></a>Setrvání pracovního postupu aplikace
Tento příklad ukazuje, jak spustit <xref:System.Activities.WorkflowApplication>ji uvolnit, kdy přestane nečinnosti a potom ho znovu načtěte mohla pokračovat v jeho zpracování.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 <xref:System.Activities.WorkflowApplication>je hostitel pro instanci jednoho pracovního postupu, který poskytuje jednoduché rozhraní a některé z běžnějších scénáře hostingu umožňuje. Jeden z těchto důvodů je dlouhá spouštění pracovních postupů, které usnadňují trvalost. Řízení hostitele trvalost provádí, buď pomocí volání operace trvalost na <xref:System.Activities.WorkflowApplication>, nebo zpracování <xref:System.Activities.WorkflowApplication> a událost označující, že <xref:System.Activities.WorkflowApplication> musí zachovat.  
  
 Ukázkový pracovní postup je <xref:System.Activities.Statements.WriteLine> výzvy pro uživatele pro jejich název aktivity `ReadLine` aktivity pro příjem názvu jako vstup prostřednictvím obnovení <xref:System.Activities.Bookmark>a jiné <xref:System.Activities.Statements.WriteLine> pro zobrazování pohlednice zpět na uživatele. Při čekání na vstup je pracovní postup, to umožňuje bod přirozené trvalost. To se často označuje jako <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> bodu. <xref:System.Activities.WorkflowApplication>Vyvolá <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> událost vždy, když program pracovního postupu můžete nastavit jako trvalý, čeká na záložku obnovení a je prováděna žádné další kroky. V pracovním postupu Tato ukázka, která se dodává bod okamžitě po `ReadLine` aktivity zahájí provádění.  
  
 A <xref:System.Activities.WorkflowApplication> jsou nastaveny na provedení trvalost s <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. V tomto příkladu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Musí být přiřazená k <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost před <xref:System.Activities.WorkflowApplication> běží.  
  
 Ukázka přidá obslužné rutiny na <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> událostí. Obslužná rutina pro tuto událost označuje, co <xref:System.Activities.WorkflowApplication> udělat vrácením <xref:System.Activities.PersistableIdleAction>. Když <xref:System.Activities.PersistableIdleAction.Unload> se vrátí, <xref:System.Activities.WorkflowApplication> je odpojen.  
  
 Ukázka pak přijímá vstup od uživatele a načte trvalou pracovního postupu do nové <xref:System.Activities.WorkflowApplication>. Dělá to tak, tak, že vytvoříte novou <xref:System.Activities.WorkflowApplication>, opakované vytvoření <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`a přidružení dokončené a odpojen události, které instance a pak volání <xref:System.Activities.WorkflowApplication.Load%2A> s identifikátorem cílové instance pracovního postupu. Jakmile je získali instanci, `ReadLine` je obnoveno záložku aktivity. Pracovního postupu vykonává provádění uvnitř `ReadLine` aktivity a používá pro dokončení. Po dokončení pracovního postupu a zrušeno jeho zavedení, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` nazývá ještě jednou odstranit pracovní postup.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
     Tato ukázka vyžaduje SQL Server Express, která je nainstalována ve výchozím nastavení s [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Přejděte do adresáře ukázkové (\WF\Basic\Persistence\InstancePersistence\CS) a spusťte CreateInstanceStore.cmd.  
  
    > [!CAUTION]
    >  Skript CreateInstanceStore.cmd se pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete pro instalaci databáze na jinou instanci, upravte skript tak, aby tak.  
  
3.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Persistence.sln a stiskněte klávesu CTRL + SHIFT + B ji od sestavit.  
  
    > [!CAUTION]
    >  Pokud jste nainstalovali databázi na jiné než výchozí instanci systému SQL Server, aktualizujte připojovací řetězec v kódu než začnete vytvářet řešení.  
  
4.  Spustit ukázku s oprávněními správce tak, že přejdete do adresáře bin projektu (\WF\Basic\Persistence\InstancePersistence\bin\Debug) v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], pravým tlačítkem myši na Workflow.exe a výběr **spustit jako správce**.  
  
#### <a name="to-remove-the-instance-store-database"></a>K odebrání instance úložiště databáze  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
2.  Přejděte do adresáře ukázka a spusťte RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
