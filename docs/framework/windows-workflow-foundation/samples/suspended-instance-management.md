---
title: Správa pozastavené instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182793"
---
# <a name="suspended-instance-management"></a>Správa pozastavené instance
Tato ukázka ukazuje, jak spravovat instance pracovního postupu, které byly pozastaveny.  Výchozí akce <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> pro `AbandonAndSuspend`je . To znamená, že ve výchozím nastavení neošetřené výjimky <xref:System.ServiceModel.WorkflowServiceHost> vyzývané z instance pracovního postupu hostované v způsobí, že instance, která má být uvolněna z paměti (opuštěné) a trvalé/trvalé verze instance, které mají být označeny jako pozastavena. Pozastavená instance pracovního postupu nebude možné spustit, dokud nebude nepozastavena.

 Ukázka ukazuje, jak nástroj příkazového řádku může být implementována pro dotaz na pozastavené instance a jak dát uživateli možnost obnovit nebo ukončit instanci. V této ukázce služba pracovního postupu záměrně vyvolá výjimku, což způsobí, že se pozastaví. Nástroj příkazového řádku pak lze použít k dotazování na instanci a následně obnovit nebo ukončit instanci.

## <a name="demonstrates"></a>Demonstruje
 <xref:System.ServiceModel.WorkflowServiceHost>s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> a v základu pracovního postupu systému Windows (WF).

## <a name="discussion"></a>Diskuse
 Nástroj příkazového řádku implementovaný v této ukázce je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]specifický pro implementaci úložiště instancí SQL, která je dodávána v aplikaci . Pokud máte vlastní implementaci úložiště instancí, můžete tento nástroj `WorkflowInstanceCommand` upravit nahrazením implementací v ukázce implementacemi, které jsou specifické pro úložiště instancí.

 Zapředpokladuovaná implementace spouští příkazy SQL proti úložišti instancí SQL přímo <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> seznamu pozastavených instancí a spoléhá na přidání do instance, aby bylo možné instance obnovit nebo ukončit.

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Tato ukázka vyžaduje, aby byly povoleny následující součásti systému Windows:

    1. Server front zpráv (MSMQ) společnosti Microsoft

    2. SQL Server Express

2. Nastavte databázi serveru SQL Server.

    1. Z příkazového řádku sady Visual Studio 2010 spusťte soubor setup.cmd z ukázkového adresáře SuspendedInstanceManagement, který provádí následující akce:

        1. Vytvoří databázi trvalosti pomocí sql server express. Pokud databáze trvalosti již existuje, je vynechána a znovu vytvořena.

        2. Nastaví databázi pro trvalost.

        3. Přidá iis APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service do role InstanceStoreUsers, která byla definována při nastavování databáze pro trvalost.

3. Nastavte frontu služeb.

    1. V sadě Visual Studio 2010 klikněte pravým tlačítkem myši na projekt **SampleWorkflowApp** a klikněte na **příkaz Nastavit jako spouštěcí projekt**.

    2. Zkompilujte a spusťte SampleWorkflowApp stisknutím **klávesy F5**. Tím se vytvoří požadovaná fronta.

    3. Stisknutím **klávesy Enter** ukončete aplikaci SampleWorkflowApp.

    4. Otevřete konzolu správa počítače spuštěním souboru Compmgmt.msc z příkazového řádku.

    5. Rozbalte **položku Služby a aplikace**, **Služba řízení front zpráv**, Soukromé **fronty**.

    6. Klepněte pravým tlačítkem myši na frontu **ReceiveTx** a vyberte příkaz **Vlastnosti**.

    7. Vyberte kartu **Zabezpečení** a povolte **všem** oprávnění k **přijímání zpráv**, **náhledu zprávy**a **odeslat zprávu**.

4. Teď spusťte ukázku.

    1. V sadě Visual Studio 2010 spusťte projekt SampleWorkflowApp znovu bez ladění stisknutím **kombinace kláves Ctrl+F5**. V okně konzoly budou vytištěny dvě adresy koncového bodu: jedna pro <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>koncový bod aplikace a pak druhá z . Poté se vytvoří instance pracovního postupu a v okně konzoly se zobrazí záznamy sledování pro tuto instanci. Instance pracovního postupu vyvolá výjimku, která způsobí, že instance bude pozastavena a přerušena.

    2. Nástroj příkazového řádku lze potom použít k další akci v některé z těchto instancí. Syntaxe argumentů příkazového řádku je následující::

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Podporované příkazy `Query`jsou: `Resume`, `Terminate`a .  Přepínač InstanceId je vyžadován `Resume` `Terminate` pouze pro a operace.

#### <a name="to-cleanup-optional"></a>Vyčištění (volitelné)

1. Otevřete konzolu správa počítače spuštěním souboru `vs2010` Compmgmt.msc z příkazového řádku.

2. Rozbalte **položku Služby a aplikace**, **Služba řízení front zpráv**, Soukromé **fronty**.

3. Odstraňte frontu **ReceiveTx.**

4. Chcete-li odebrat databázi trvalosti, spusťte cleanup.cmd.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
