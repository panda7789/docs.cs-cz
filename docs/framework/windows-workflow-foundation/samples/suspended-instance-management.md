---
title: Správa pozastavené instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 3f1f4f8edcbe0e05067d3ca739ef3d5f4fe4d798
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715947"
---
# <a name="suspended-instance-management"></a>Správa pozastavené instance
Tato ukázka předvádí, jak spravovat instance pracovních postupů, které byly pozastaveny.  Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`. To znamená, že ve výchozím nastavení se neošetřené výjimky vyvolané z instance pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost> způsobí odstranění instance z paměti (opuštěno) a trvalá/trvalá verze instance, která bude označena jako pozastavená. Instanci pozastaveného pracovního postupu nebude možné spustit, dokud nebude pozastavena.

 Ukázka ukazuje, jak lze nástroj příkazového řádku implementovat pro dotaz na pozastavené instance a jak dát uživateli možnost obnovit nebo ukončit instanci. V této ukázce služba pracovního postupu záměrně vyvolá výjimku, což způsobí, že by se pozastavila. Nástroj příkazového řádku se pak dá použít k dotazování na instanci a následnému obnovení nebo ukončení instance.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.ServiceModel.WorkflowServiceHost> s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> v programovací model Windows Workflow Foundation (WF).

## <a name="discussion"></a>Účely
 Nástroj příkazového řádku implementovaný v této ukázce je specifický pro implementaci úložiště instance SQL, která je dodávána v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Máte-li vlastní implementaci úložiště instance, můžete tento nástroj přizpůsobit nahrazením `WorkflowInstanceCommand`ch implementací v ukázce s implementacemi, které jsou specifické pro vaše úložiště instancí.

 Zadaná implementace spouští příkazy SQL pro úložiště instance SQL přímo v seznamu pozastavených instancí a spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidáno do <xref:System.ServiceModel.WorkflowServiceHost>, aby bylo možné obnovit nebo ukončit instance.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Tato ukázka vyžaduje, aby byly povoleny následující součásti systému Windows:

    1. Server služby MSMQ (Microsoft Message Queue)

    2. SQL Server Express

2. Nastavte databázi SQL Server.

    1. Z příkazového řádku sady Visual Studio 2010 spusťte "Setup. cmd" z ukázkového adresáře SuspendedInstanceManagement, který provede následující akce:

        1. Vytvoří databázi trvalosti pomocí SQL Server Express. Pokud databáze trvalosti už existuje, pak se vynechá a znovu vytvoří.

        2. Nastaví databázi pro trvalost.

        3. Přidá službu IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service do role InstanceStoreUsers, která byla definována při nastavování databáze pro trvalost.

3. Nastavte frontu služby.

    1. V sadě Visual Studio 2010 klikněte pravým tlačítkem na projekt **SampleWorkflowApp** a klikněte na **nastavit jako spouštěný projekt**.

    2. Zkompilujte a spusťte SampleWorkflowApp stisknutím klávesy **F5**. Tím se vytvoří požadovaná fronta.

    3. Stisknutím klávesy **ENTER** zastavte SampleWorkflowApp.

    4. Spusťte compmgmt. msc z příkazového řádku a otevřete tak konzolu pro správu počítače.

    5. Rozbalte **službu a aplikace**, **Služba Řízení front zpráv**a **soukromé fronty**.

    6. Klikněte pravým tlačítkem na frontu **ReceiveTx** a vyberte **vlastnosti**.

    7. Vyberte kartu **zabezpečení** a umožněte **všem** , aby měli oprávnění **přijímat zprávy**, **prohlížet zprávy**a **odesílat zprávy**.

4. Nyní spusťte ukázku.

    1. V aplikaci Visual Studio 2010 znovu spusťte projekt SampleWorkflowApp bez ladění stisknutím **kombinace kláves CTRL + F5**. V okně konzoly budou vytištěny dvě adresy koncových bodů: jeden pro koncový bod aplikace a další z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Instance pracovního postupu je pak vytvořena a sledování záznamů pro tuto instanci se zobrazí v okně konzoly. Instance pracovního postupu vyvolá výjimku způsobující pozastavení a přerušení instance.

    2. Nástroj příkazového řádku je pak možné použít k provedení dalších akcí na kterékoli z těchto instancí. Syntaxe pro argumenty příkazového řádku je následující::

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Podporovány jsou následující příkazy: `Query`, `Resume`a `Terminate`.  Přepínač InstanceId je vyžadován pouze pro operace `Resume` a `Terminate`.

#### <a name="to-cleanup-optional"></a>K vyčištění (volitelné)

1. Spusťte příkaz compmgmt. msc v `vs2010` příkazovém řádku a otevřete konzolu pro správu počítače.

2. Rozbalte **službu a aplikace**, **Služba Řízení front zpráv**a **soukromé fronty**.

3. Odstraňte frontu **ReceiveTx** .

4. Chcete-li odebrat databázi trvalosti, spusťte příkaz Cleanup. cmd.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
