---
title: "Předdefinované konfigurace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7dc11c19025393ffb1ce8e10cbfa637f38a867fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="built-in-configuration"></a>Předdefinované konfigurace
Tento příklad znázorňuje použití a konfigurace úložiště SQL instance pracovního postupu. Ukládání instance pracovního postupu SQL je na základě SQL implementace instance úložiště. Umožňuje instanci pro uložení a načtení stavu do a z databáze systému SQL Server nebo SQL Server Express.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka se skládá z pracovního postupu, který implementuje počítání služby. Jakmile je volána metoda spuštění služby, služby počty od 0 do 59. Hodnota čítače se zvýší každé 2 sekundy. Po každé počet pracovního postupu trvá.  
  
 Počítání pracovního postupu je samoobslužně hostovaná hostitel služby pracovního postupu. Program `Main` metoda vytvoří instanci hostitele služby pracovního postupu, který je hostitelem počítání pracovního postupu. Definuje koncové body, za kterých bude možné spojit počítání pracovního postupu. Potom definuje SQL pracovního postupu instance úložiště chování, které slouží ke konfiguraci úložiště instance SQL pracovního postupu. V dalším kroku program vytvoří klienta, který volá metodu start počítání pracovního postupu.  
  
 Po spuštění programu, čítač, automaticky spustí, počítání. Všimněte si, že může trvat několik sekund, načítání instance a konfiguraci úložiště instance pracovního postupu SQL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]úložiště instance pracovního postupu, najdete v části [úložiště Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Ukázka se skládá ze dvou částí:  
  
1.  Zobrazuje InstanceStore1 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> je konfigurován pomocí kódu jazyka C# (viz Program.cs).  
  
2.  Zobrazuje InstanceStore2 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> je nakonfigurovat pomocí XML (viz App.config).  
  
 Umožňuje nakonfigurovat chování ukládání Instance pracovního postupu SQL k dispozici jsou následující nastavení:  
  
-   Nastavte `HostLockRenewalPeriod`. Tentokrát definuje interval, pomocí kterého hostitele obnovuje zámek vlastnictví instancí, které běží. Zámek informace jsou uloženy v úložišti Instance. Pokud se vlastnictví neobnovíte pro dvě z intervalech definovaných v `HostLockRenewalPeriod`, instance je považován za opuštění. Pokud jiný <xref:System.ServiceModel.Activities.WorkflowServiceHost> běží témže pracovním postupu a připojené ke stejné instanci úložiště (buď na stejném počítači nebo do jiného počítače), obnoví tuto instanci. (Instance obnovení je mimo rozsah pro tuto ukázku.)  
  
-   Nastavte `RunnableInstancesDetectionPeriod`. Toto období definuje interval, ve kterém hostitele se dotazuje na instance, které se staly spustitelného. Instance se může stát spustitelného, pokud dojde k některé z následujících událostí:  
  
    -   Trvanlivý časovač (<xref:System.Activities.Statements.Delay>) vyprší platnost.  
  
    -   Jiného hostitele neúspěchy jeho `HostLockRenewal` prezenčního signálu (například z důvodu selhání počítače) a instance je obnovena.  
  
-   Nastavte `InstanceCompletionAction`. Tato vlastnost, pokud nastavena na `DeleteNothing`, udržuje dokončit instancí v úložišti Instance; je-li nastavena na `DeleteAll`, instancí jsou odstranit z úložiště po dokončení. Všimněte si, že  
  
    > [!NOTE]
    >  Stisknutím klávesy ENTER před počítání dokončil ukončení hostitele nedokončí k instanci pracovního postupu.  
  
-   Nastavte `InstanceLockedExceptionAction`. Toto nastavení určuje, jak hostitel postupovat, pokud chcete načíst instanci, která je uzamčený jiného hostitele. Existují tyto možnosti:  
  
    -   Pokud nastavena na `NoRetry`: nemáte opakujte zatížení a vrátit `InstanceLockedException` k hostiteli.  
  
    -   Pokud nastavena na `BasicRetry`: i nadále pokoušet o načtení instance. Opakované pokusy jsou naplánovány podle jednoduchého lineární algoritmus (například zkusit každých 5 sekund).  
  
    -   Pokud nastavena na `AggressiveRetry`: i nadále pokoušet o načtení instance. Opakované pokusy jsou naplánovány podle agresivní exponenciální back vypnout algoritmu.  
  
-   Nastavte možnost kódování. Toto nastavení určuje, jak je stav instance uložen v úložišti Instance pracovního postupu SQL. Existují tyto možnosti:  
  
    -   Stav instance se komprimují pomocí algoritmu kompresi GZip.  
  
    -   Stav instance není komprimována.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek jako správce, pokud jsou k dispozici oprávnění.  
  
2.  Přejděte do adresáře ukázkové (\WF\Basic\Persistence\BuiltInConfiguration\CS) a spusťte CreateInstanceStore.cmd.  
  
3.  Pokud není k dispozici, oprávnění správce přihlášení vytvořit systému SQL Server. Přejděte na `Security`, **přihlášení**. Klikněte pravým tlačítkem na **přihlášení** a vytvořte nové přihlašovací údaje.  
  
4.  Přidání vašeho seznamu ACL uživatele do role systému SQL. Otevřete **databáze**, **InstanceStore**, **zabezpečení**. Klikněte pravým tlačítkem na **uživatelé** a vyberte **noví uživatelé**. Nastavte **přihlašovací jméno** uživateli vytvořili v předchozím kroku. Přidejte uživatele do členství role databáze **System.Activities.DurableInstancing.InstanceStoreUsers** (a dalších). Všimněte si, že tento uživatel může existovat již (například dbo uživatele).  
  
5.  Otevřete soubor InstanceStore.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
6.  V [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do adresáře odpovídající bin\debug tohoto příkladu (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), klikněte pravým tlačítkem na InstanceStore.exe a vyberte **spustit jako správce**. Tato ukázka musí spustit s oprávněními správce, protože ho otevře naslouchací proces kanálu.  
  
7.  Pokud jste vytvořili instanci úložiště do jiné databáze než místní instalace systému SQL Server Express je nutné aktualizovat připojovací řetězec databáze (`const string ConnectionString` v souboru Program.cs projektu InstanceStore1 a `connectionString` atribut v souboru App.config z InstanceStore2 projekt) v ukázkové a pak ji znovu zkompilovat vzorku.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Ověření ukázku běží správně  
  
1.  Je spuštěn ukázku, spustíte SQL Server Management Studio.  
  
2.  V **Průzkumník objektů**, vyberte **databáze**, **InstanceStore**, **tabulky**a potom  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Klikněte pravým tlačítkem na **InstanceTable** a vyberte **vyberte Top 1000 řádky**.  
  
4.  Sledovat je nový záznam a, **vypršení platnosti zámku** změny každých 5 sekund (klikněte na hlavním panelu **Execute** tlačítko pro aktualizaci dotazu). Toto je v důsledku nastavení **interval obnovování hostitele zámku** 5.  
  
5.  Sledujte po inventuru dokončení, že záznam v tabulce instance odebrána. Toto je v důsledku nastavení **Instance dokončení akce** k **DeleteAll**.  
  
6.  Stisknutím klávesy ENTER ukončení pracovního postupu hostitelskou aplikaci a že **LockOwnersTable** se odstraní.  
  
#### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Spusťte RemoveInstanceStore.cmd v adresáři ukázkové (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
