---
title: SQLStoreExtensibility
ms.date: 03/30/2017
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
ms.openlocfilehash: f49d05244cf9f65a8e06f39c7e40391aaebd9f77
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090159"
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Tato ukázka demonstruje používání a konfiguraci propagované vlastnosti úložiště instancí pracovních postupů SQL. Úložiště instancí pracovních postupů SQL je založený na SQL implementace úložiště instancí. To umožňuje instance pro uložení stavu a načtení stavu do a z databáze systému SQL Server nebo SQL Server Express. Funkce rozšiřitelnost úložiště umožňuje uživateli definovat vlastnosti, které jsou uloženy v úložišti instancí. Tyto vlastnosti jsou zobrazeny v zobrazení propagované vlastnosti, které mu umožní dotazu pro ně.  
  
 Tento příklad se skládá z pracovní postup, který implementuje počítání služby. Po zavolání metody start služby služba se počítá od 0 do 29. Hodnota čítače se zvýší každé 2 sekundy. Po každé počet pracovního postupu trvá. Aktuální hodnota čítače je uložen v úložišti instancí jako propagovanou vlastnost.  
  
 Počítání pracovního postupu je samoobslužně hostovaná od hostitele služby pracovního postupu. Programu `Main` metoda provede následující akce:  
  
-   Vytvoří instanci hostitele služby pracovního postupu, který je hostitelem počítání pracovního postupu a definuje koncové body, za kterých se dá kontaktovat počítání pracovního postupu.  
  
-   Definuje SQL pracovního postupu instance úložiště chování, které slouží ke konfiguraci úložiště instancí pracovních postupů SQL. Úložiště je nastaven na považovat `CountStatus` jako propagovanou vlastnost.  
  
-   Vytvoří klienta, která volá metodu start počítání pracovního postupu.  
  
 Po spuštění programu čítač automaticky spustí, počítací. Všimněte si, že může trvat několik sekund na načtení instance a nakonfigurovat úložiště instancí pracovních postupů SQL.  
  
 Ke zvýšení úrovně hodnota čítače jako vlastní vlastnost, musí provést následující kroky:  
  
1.  Třída `CounterStatus` definuje instanci rozšíření typu <xref:System.Activities.Persistence.PersistenceParticipant>, které používají aktivity slouží k poskytování proměnné stavu. `Count` je definován jako hodnotu pouze pro zápis. Při instance pracovního postupu se dodává s bodem trvalost, rozšíření instance uloží `Count` vlastností do kolekce dat trvalosti.  
  
2.  Při vytváření v úložišti instancí, novou vlastnost `CountStatus`, je definován pomocí `store.Promote()` metody.  
  
3.  Pro pracovní postupy `SaveCounter` aktivity přiřadí aktuální hodnotu do proměnné čítače `Count` pole Stav.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Vytvoření instance databáze úložiště.  
  
    1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do adresáře vzorku (\WF\Basic\Persistence\SqlStoreExtensibility\CS) a spusťte CreateInstanceStore.cmd [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
        > [!WARNING]
        >  Skript CreateInstanceStore.cmd pokusí vytvořit databázi na výchozí instanci systému SQL Server 2008 Express. Pokud chcete nainstalovat databázi na jinou instanci, upravte skript tak učinit.  
  
2.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a načtení řešení SqlStoreExtensibility.sln a sestavte ho stisknutím kombinace kláves CTRL + SHIFT + B.  
  
    > [!WARNING]
    >  Pokud jste nainstalovali databázi na jinou než výchozí instanci systému SQL Server, aktualizujte připojovací řetězec v kódu před sestavením řešení.  
  
3.  Spusťte ukázku s oprávněními správce tak, že přejdete do adresáře bin projektu (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) v [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], SqlStoreExtensibility.exe pravým tlačítkem myši a vyberete **spustit jako Správce**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Chcete-li ověřit ukázku pracuje správně  
  
1.  Pomocí SQL Server Management Studio zobrazíte obsah tabulky instance tak, že vyberete **databází**, **třídy InstanceStore**a potom  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** v Průzkumníku objektů klikněte pravým tlačítkem na **System.ServiceModel.Activities.DurableInstancing.InstanceTable** a vyberte  **Vybrat prvních 1 000 řádků**. Další informace o nástroji SQL Server Management Studio najdete v tématu [Představujeme SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Sledujte instancí pracovních postupů, které jsou uvedeny.  
  
3.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku, spusťte skript QueryInstanceStore.cmd nachází v adresáři ukázkové (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
4.  Podívejte se hodnota čítače se zobrazí v části **CountStatus**.  
  
5.  Spusťte skript několikrát zobrazíte **CountStats** hodnotu změnit.  
  
6.  Stiskněte klávesu ENTER k ukončení aplikace pracovního postupu.  
  
### <a name="to-uninstall-the-sample"></a>Chcete-li odinstalovat vzorku  
  
1.  Odeberte instanci databáze úložiště spuštěním skriptu RemoveInstanceStore.cmd nachází v adresáři ukázkové (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Viz také  
 [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
