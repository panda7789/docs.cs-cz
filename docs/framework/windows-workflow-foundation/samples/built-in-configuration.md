---
title: Integrovaná konfigurace
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867839"
---
# <a name="built-in-configuration"></a>Integrovaná konfigurace
Tato ukázka demonstruje používání a konfiguraci úložiště instancí pracovních postupů SQL. Úložiště instancí pracovních postupů SQL je založený na SQL implementace úložiště instancí. To umožňuje instance pro uložení a načtení stavu do a z databáze systému SQL Server nebo SQL Server Express.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na stránku (stahování) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tento příklad se skládá z pracovní postup, který implementuje počítání služby. Po zavolání metody start služby služba se počítá od 0 do 59. Hodnota čítače se zvýší každé 2 sekundy. Po každé počet pracovního postupu trvá.  
  
 Počítání pracovního postupu je samoobslužně hostovaná od hostitele služby pracovního postupu. Programu `Main` metoda vytvoří instanci hostitele služby pracovního postupu, který je hostitelem počítání pracovního postupu. Definuje koncové body, za kterých se dá kontaktovat počítání pracovního postupu. Potom definuje SQL pracovního postupu instance úložiště chování, které slouží ke konfiguraci úložiště instancí pracovních postupů SQL. V dalším kroku program vytvoří klienta, který volá metodu start počítání pracovního postupu.  
  
 Po spuštění programu čítač automaticky spustí, počítací. Všimněte si, že může trvat několik sekund na načtení instance a nakonfigurovat úložiště instancí pracovních postupů SQL. Další informace o úložiště instancí pracovních postupů najdete v tématu [Store Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Ukázka se skládá ze dvou částí:  
  
1.  InstanceStore1 ukazuje jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> je konfigurovat pomocí kódu jazyka C# (viz Program.cs).  
  
2.  InstanceStore2 ukazuje jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> konfigurován s použitím XML (viz App.config).  
  
 Konfigurace chování Store Instance pracovního postupu SQL k dispozici jsou následující nastavení:  
  
-   Nastavte `HostLockRenewalPeriod`. Tentokrát definuje interval, pomocí kterého hostitele obnoví uzamčení vlastnictví instancí, které poběží. Zámek informace jsou uloženy v instanci Store. Pokud se pro dva intervalech definovaných v neobnoví vlastnictví `HostLockRenewalPeriod`, instance se považuje za opuštěna. Pokud jiný <xref:System.ServiceModel.Activities.WorkflowServiceHost> běží stejného pracovního postupu a připojení k úložišti stejné instance, (buď na stejném počítači nebo jiném počítači), obnoví instanci. (Obnovení instance je mimo rozsah pro tuto ukázku.)  
  
-   Nastavte `RunnableInstancesDetectionPeriod`. Toto období definuje interval, ve kterém se dotazuje hostiteli instance, které mají stane spustitelným. Instance může spustitelnost Pokud kterákoli z následujících událostí:  
  
    -   Trvalý časovače (<xref:System.Activities.Statements.Delay>) vyprší platnost.  
  
    -   Další Neúspěšné přístupy do hostitele jeho `HostLockRenewal` zjišťování prezenčního signálu (například z důvodu selhání počítače) a instance se obnoví.  
  
-   Nastavte `InstanceCompletionAction`. Tuto vlastnost, pokud nastavena na `DeleteNothing`, zachová dokončení instance ve Store Instance; Pokud `DeleteAll`, instance budou odstraněny z úložiště po dokončení. Všimněte si, že  
  
    > [!NOTE]
    >  Ukončování hostitele stisknutím klávesy ENTER před dokončením počítání nedokončí instance pracovního postupu.  
  
-   Nastavte `InstanceLockedExceptionAction`. Toto nastavení definuje, co hostitel dělat, když ji chce, aby se vyžadovalo načtení instance, která je uzamčen jiného hostitele. Existují tyto možnosti:  
  
    -   Pokud nastavena na `NoRetry`: nemáte opakujte zatížení a vrátit `InstanceLockedException` k hostiteli.  
  
    -   Pokud nastavit `BasicRetry`: i nadále pokoušet o načtení instance. Opakované pokusy jsou naplánovány podle jednoduchých lineárního algoritmu (například opakovat každých 5 sekund).  
  
    -   Pokud nastavit `AggressiveRetry`: i nadále pokoušet o načtení instance. Opakované pokusy jsou naplánovány podle agresivní exponenciální regresní algoritmus.  
  
-   Nastavte možnost kódování. Toto nastavení definuje, jak je uložen stav instance v Store Instance pracovního postupu SQL. Existují tyto možnosti:  
  
    -   Stav instance je komprimován pomocí algoritmu GZip komprese.  
  
    -   Stav instance není komprimovaná.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek jako správce, pokud oprávnění jsou k dispozici.  
  
2.  Přejděte do adresáře vzorku (\WF\Basic\Persistence\BuiltInConfiguration\CS) a spusťte CreateInstanceStore.cmd.  
  
3.  Pokud není k dispozici, oprávnění správce přihlášení vytvoření SQL serveru. Přejděte na `Security`, **přihlášení**. Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje.  
  
4.  Přidáte uživatele seznamu ACL pro role systému SQL. Otevřít **databází**, **třídy InstanceStore**, **zabezpečení**. Klikněte pravým tlačítkem na **uživatelé** a vyberte **noví uživatelé**. Nastavte **přihlašovací jméno** uživateli, vytvořený v předchozím kroku. Přidat uživatele do členství role databáze **System.Activities.DurableInstancing.InstanceStoreUsers** (a ostatní). Všimněte si, že uživatel může existovat už (například objekt dbo uživatele).  
  
5.  Otevřete soubor InstanceStore.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
6.  V [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do adresáře příslušné bin\debug vzorku (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), InstanceStore.exe klikněte pravým tlačítkem myši a vyberte **spustit jako správce**. Tato ukázka musí spustit s oprávněními správce, protože otevře naslouchacího procesu kanálu.  
  
7.  Pokud jste vytvořili v úložišti instancí v jiné databáze než místní instalace systému SQL Server Express je nutné aktualizovat připojovací řetězec databáze (`const string ConnectionString` v souboru Program.cs InstanceStore1 projektu a `connectionString` atributu v souboru App.config aplikace Projekt InstanceStore2) ve vzorku a překompilujte vzorku.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Chcete-li ověřit ukázku běží správně  
  
1.  Je spuštěn ukázku spusťte SQL Server Management Studio.  
  
2.  V **Průzkumník objektů**vyberte **databází**, **třídy InstanceStore**, **tabulky**a potom  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Klikněte pravým tlačítkem myši **InstanceTable** a vyberte **vybrat prvních 1000 řádků**.  
  
4.  Podívejte se, že je nový záznam a, který **platnost zámku** změní každých 5 sekund (klikněte na hlavním panelu **Execute** tlačítko pro aktualizaci dotazu). Toto je v důsledku nastavení **interval obnovování zámku hostitele** na 5.  
  
5.  Sledujte po dokončení počítání, že položka v tabulce instance je odebrána. Toto je v důsledku nastavení **akce dokončení Instance** k **DeleteAll**.  
  
6.  Stisknutím klávesy ENTER ukončete nástroj aplikace hostitele pracovního postupu a zda se zobrazila zpráva **LockOwnersTable** se odstraní.  
  
#### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
