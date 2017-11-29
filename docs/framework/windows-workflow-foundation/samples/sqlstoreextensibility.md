---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 111e7aa4164d9fc811ebe3f5efb196df77d1ded0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Tento příklad znázorňuje použití a konfiguraci propagovaných vlastností v úložišti instance SQL pracovního postupu. Ukládání instance pracovního postupu SQL je na základě SQL implementace instance úložiště. Umožňuje instanci pro uložení stavu a načtení stavu do a z databáze systému SQL Server nebo SQL Server Express. Funkce rozšiřitelnost úložiště umožňuje uživateli definovat vlastnosti, které jsou uložené v úložišti instance. Tyto vlastnosti jsou zobrazeny v zobrazení propagovaných vlastnosti, která umožňuje uživatelům dotazu pro ně.  
  
 Tato ukázka se skládá z pracovního postupu, který implementuje počítání služby. Po zavolání metody spuštění služby, služby počty od 0 do 29. Hodnota čítače se zvýší každé 2 sekundy. Po každé počet pracovního postupu trvá. Aktuální hodnota čítače je uložen v úložišti instance jako propagovaných vlastnost.  
  
 Počítání pracovního postupu je samoobslužně hostovaná hostitel služby pracovního postupu. Program `Main` metoda provede následující akce:  
  
-   Vytvoří instanci hostitele služby pracovního postupu, který je hostitelem počítání pracovního postupu a definuje koncové body, za kterých bude možné spojit počítání pracovního postupu.  
  
-   Definuje SQL pracovního postupu instance úložiště chování, které slouží ke konfiguraci úložiště instance SQL pracovního postupu. Windows store je odeslán pokyn přistupovat ke `CountStatus` jako propagovaných vlastnost.  
  
-   Vytvoří klienta, který volá metodu start počítání pracovního postupu.  
  
 Po spuštění programu, čítač, automaticky spustí, počítání. Všimněte si, že může trvat několik sekund, načítání instance a konfiguraci úložiště instance pracovního postupu SQL.  
  
 Ke zvýšení úrovně hodnota čítače jako vlastní vlastnost, musí být přijata následující kroky:  
  
1.  Třída `CounterStatus` definuje rozšíření instance typu <xref:System.Activities.Persistence.PersistenceParticipant>, který je využíván jiným aktivity k poskytování proměnné stavu. `Count`je definován jako hodnotu pouze pro zápis. Instance pracovního postupu vycházejí trvalost bodu, uloží rozšíření instance `Count` vlastnost do kolekce dat trvalost.  
  
2.  Při vytváření úložiště instance, novou vlastnost `CountStatus`, je definována pomocí `store.Promote()` metoda.  
  
3.  Pracovního postupu `SaveCounter` aktivity přiřadí aktuální hodnota čítače `Count` pole stavu.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Vytvoření instance úložiště databáze.  
  
    1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do adresáře ukázkové (\WF\Basic\Persistence\SqlStoreExtensibility\CS) a spusťte CreateInstanceStore.cmd [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
        > [!WARNING]
        >  Skript CreateInstanceStore.cmd se pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete pro instalaci databáze na jinou instanci, upravte skript tak, aby tak.  
  
2.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] načíst SqlStoreExtensibility.sln řešení a sestavení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
    > [!WARNING]
    >  Pokud jste nainstalovali databázi na jiné než výchozí instanci systému SQL Server, aktualizujte připojovací řetězec v kódu než začnete vytvářet řešení.  
  
3.  Spustit ukázku s oprávněními správce tak, že přejdete do adresáře bin projektu (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], pravým tlačítkem myši na SqlStoreExtensibility.exe a výběr **spustit jako Správce**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Ověření ukázku pracuje správně.  
  
1.  Použít SQL Server Management Studio k zobrazení obsahu tabulky instance výběrem **databáze**, **InstanceStore**a potom  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** v Průzkumníku objektů, klikněte pravým tlačítkem na **System.ServiceModel.Activities.DurableInstancing.InstanceTable** a vyberte  **Vybrat prvních 1 000 řádků**. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio, najdete v části [představení SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Sledujte instancí pracovních postupů, které jsou uvedené.  
  
3.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku, spusťte skript QueryInstanceStore.cmd umístěný v adresáři ukázkové (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
4.  Sledovat hodnota čítače se zobrazí v části **CountStatus**.  
  
5.  Spusťte skript několikrát zobrazíte **CountStats** hodnotu změnit.  
  
6.  Stisknutím klávesy ENTER ukončení aplikace pracovního postupu.  
  
### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Odeberte databázi úložiště instance spuštěním skriptu RemoveInstanceStore.cmd umístěný v adresáři ukázkové (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Viz také  
 [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
