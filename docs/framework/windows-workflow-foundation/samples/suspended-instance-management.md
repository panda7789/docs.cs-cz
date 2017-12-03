---
title: "Správa pozastavenou instancí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24c94f93524f6b31b622c527da068379ce7e724d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="suspended-instance-management"></a>Správa pozastavenou instancí
Tento příklad ukazuje, jak spravovat instancí pracovních postupů, které byly pozastaveny.  Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`. To znamená, že ve výchozím nastavení, neošetřených výjimek vyvolaných z instance pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost> způsobí, že instance má-li být uvolněn z paměti (opuštění) a trvale nebo trvalé verze instance označeno jako pozastaveno. Instanci pracovního postupu pozastavenou nebude možné spustit až po jejím pozastavení.  
  
 Ukázka ukazuje, jak můžete implementovat nástroj příkazového řádku dotazu pro pozastavenou instance a poskytnout možnost obnovit nebo ukončení instance uživatele. V této ukázce služby pracovního postupu záměrně vyvolá výjimku, způsobuje mohla stát pozastaveno. Nástroj příkazového řádku pak slouží k dotazování pro instanci a následně obnovit nebo ukončení instance.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.WorkflowServiceHost>s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> v [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## <a name="discussion"></a>Diskusní  
 Nástroj příkazového řádku, které jsou implementované v této ukázce je specifická pro implementace úložiště instance SQL, který se dodává v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Pokud máte vlastní implementaci instance úložiště, pak tento nástroj můžete přizpůsobit tak, že nahradíte `WorkflowInstanceCommand` implementace v ukázce s implementací, které jsou specifické pro instance úložiště.  
  
 Zadaná implementace spouští příkazy SQL úložiště instance SQL přímo do seznamu pozastavenou instance, a přitom spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidán do <xref:System.ServiceModel.WorkflowServiceHost> Chcete-li obnovit nebo ukončení instance.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka vyžaduje, že jsou povoleny následující součásti systému Windows:  
  
    1.  Server Microsoft zpráv fronty (MSMQ)  
  
    2.  SQL Server Express  
  
2.  Nastavení databáze systému SQL Server.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazovém řádku spusťte "setup.cmd" z adresáře ukázka SuspendedInstanceManagement, který provede následující akce:  
  
        1.  Vytvoří databázi trvalost pomocí SQL Server Express. Pokud už existuje databáze trvalost, pak je vyřadit a znovu vytvořit  
  
        2.  Nastaví databázi trvalosti.  
  
        3.  Přidá IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service InstanceStoreUsers roli, která byla definována při nastavení databáze pro trvalost.  
  
3.  Nastavte fronta služby.  
  
    1.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], klikněte pravým tlačítkem myši **SampleWorkflowApp** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
    2.  Zkompilování a spuštění SampleWorkflowApp stisknutím **F5**. Tím se vytvoří požadované fronty.  
  
    3.  Stiskněte klávesu **Enter** zastavit SampleWorkflowApp.  
  
    4.  Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z příkazového řádku.  
  
    5.  Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
    6.  Klikněte pravým tlačítkem **ReceiveTx** fronty a vyberte **vlastnosti**.  
  
    7.  Vyberte **zabezpečení** kartě a povolit **Everyone** tak, aby měl oprávnění k **přijímat zprávy**, **prohlížet zprávy**, a  **Odeslat zprávu**.  
  
4.  Nyní spusťte ukázku.  
  
    1.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], znovu spusťte projekt SampleWorkflowApp bez ladění stisknutím **Ctrl + F5**. V okně konzoly budou vytištěny dvě adresy koncových bodů: jeden pro koncový bod aplikace a pak další z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Instance pracovního postupu je poté jste vytvořili, a sledování záznamů u dané instance se zobrazí v okně konzoly. Instance pracovního postupu vyvolá výjimku způsobuje instanci systému na jde je pozastavit a byl zrušen.  
  
    2.  Nástroj příkazového řádku pak lze provádět další akce na všech těchto instancí. Tady je syntax argumenty pro příkazový řádek::  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         Jsou podporované příkazy: `Query`, `Resume`, a `Terminate`.  Identifikátor InstanceId přepínač je potřeba jenom pro `Resume` a `Terminate` operace.  
  
#### <a name="to-cleanup-optional"></a>Pro čištění (volitelné)  
  
1.  Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z `vs2010` příkazového řádku.  
  
2.  Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
3.  Odstranit **ReceiveTx** fronty.  
  
4.  Chcete-li odebrat databázi trvalost, spusťte cleanup.cmd.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
