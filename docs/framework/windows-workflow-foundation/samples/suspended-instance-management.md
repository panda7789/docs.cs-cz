---
title: Správa pozastavené Instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: f614770121185644c3395f923cf7835141653f55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394597"
---
# <a name="suspended-instance-management"></a>Správa pozastavené Instance
Tento příklad ukazuje, jak spravovat instancí pracovních postupů, které byly pozastaveny.  Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`. To znamená, že ve výchozím nastavení, neošetřené výjimky vyvolané z instance pracovního postupu hostitelem <xref:System.ServiceModel.WorkflowServiceHost> způsobí, že instance, která má být uvolněn z paměti (opuštěných) a verze durable/trvalé instance, kterou chcete označit, jak je pozastavena. Instance pracovního postupu pozastavené nebude možné spustit až po jejím nezruší.  
  
 Vzorek ukazuje, jak nástroj příkazového řádku lze provést dotaz pro pozastavené instance a poskytnout uživateli možnost obnovit nebo ukončení instance. V této ukázce Služba pracovního postupu záměrně vyvolá výjimku, vyvolá zablokuje. Nástroj příkazového řádku pak umožňuje zadat dotaz pro instanci a následně obnovit nebo ukončení instance.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.ServiceModel.WorkflowServiceHost> s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> ve Windows Workflow Foundation (WF).  
  
## <a name="discussion"></a>Diskuse  
 Nástroj příkazového řádku, které jsou implementovány v této ukázce je specifické pro implementaci úložiště instance SQL, který se dodává v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Pokud máte vlastní implementaci v úložišti instancí, pak tento nástroj můžete přizpůsobit tak, že nahradíte `WorkflowInstanceCommand` implementace v ukázce s implementací, které jsou specifické pro vaše úložiště instancí.  
  
 Poskytnutou implementační spouští příkazy SQL pro ukládání instance SQL přímo na seznamu pozastavené instance, a spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidán do <xref:System.ServiceModel.WorkflowServiceHost> za účelem obnovení nebo ukončení instance.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Tato ukázka vyžaduje, že jsou povoleny následující součásti Windows:  
  
    1.  Server Microsoft zpráv fronty (MSMQ)  
  
    2.  SQL Server Express  
  
2.  Nastavení databáze SQL serveru.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazovém řádku spusťte "setup.cmd" adresáře ukázka SuspendedInstanceManagement, který provede následující akce:  
  
        1.  Vytvoří databáze trvalosti pomocí SQL Server Express. Pokud už existuje databáze trvalosti, pak je vyřadit a znovu vytvořit  
  
        2.  Nastaví databáze trvalosti.  
  
        3.  Přidá IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service InstanceStoreUsers roli, která byla definována při nastavení databáze trvalosti.  
  
3.  Nastavení služby queue.  
  
    1.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], klikněte pravým tlačítkem myši **SampleWorkflowApp** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
    2.  Kompilace a spuštění SampleWorkflowApp stisknutím kombinace kláves **F5**. Tím se vytvoří požadované frontě.  
  
    3.  Stisknutím klávesy **Enter** zastavit SampleWorkflowApp.  
  
    4.  Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z příkazového řádku.  
  
    5.  Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
    6.  Klikněte pravým tlačítkem myši **ReceiveTx** zařadit do fronty a vyberte **vlastnosti**.  
  
    7.  Vyberte **zabezpečení** kartu a povolit **Everyone** oprávnění pro **přijímat zprávy**, **prohlížet zprávy**, a  **Odeslat zprávu**.  
  
4.  Nyní spusťte ukázku.  
  
    1.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], znovu spusťte SampleWorkflowApp projektu bez ladění stisknutím kombinace kláves **Ctrl + F5**. Dvě adresy koncových bodů budou zobrazeny v okně konzoly: jeden pro koncový bod aplikace a pak ostatní z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Instance pracovního postupu se pak vytvoří a sledování záznamů pro tuto instanci se zobrazí v okně konzoly. Instance pracovního postupu vyvolá výjimku, způsobující instance, kterou chcete pozastavit a byla přerušena.  
  
    2.  Nástroj příkazového řádku je pak možné provádět další akce na kteroukoli z těchto instancí. Syntaxe pro argumenty příkazového řádku je následující:  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         Podporované příkazy: `Query`, `Resume`, a `Terminate`.  InstanceId přepínač je potřeba jenom pro `Resume` a `Terminate` operace.  
  
#### <a name="to-cleanup-optional"></a>Vyčistit (volitelné)  
  
1.  Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z `vs2010` příkazového řádku.  
  
2.  Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
3.  Odstranit **ReceiveTx** fronty.  
  
4.  Pokud chcete odebrat databáze stálost, spusťte cleanup.cmd.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
