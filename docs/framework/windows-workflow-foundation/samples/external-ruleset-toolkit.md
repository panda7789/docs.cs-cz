---
title: Externí Ruleset Toolkit
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: 0c2dec4d28b60fe5caef13ed6bd0e5826713a56f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="external-ruleset-toolkit"></a>Externí Ruleset Toolkit
Za normálních okolností Pokud použijete pravidla v rámci aplikace pracovního postupu, pravidla jsou součástí sestavení. V některých případech můžete udržovat sady pravidel odděleně od sestavení tak, aby bylo možné aktualizovat bez opětovné sestavení a nasazení sestavení pracovního postupu. Tato ukázka vám umožňuje spravovat a upravovat sady pravidel v databázi a přístup k tyto sady pravidel z pracovního postupu za běhu. To umožňuje, aby automaticky začlenit RuleSet změny spuštěných instancí pracovního postupu.  
  
 Ukázka externí RuleSet Toolkit obsahuje nástroj založené na Windows Forms, který můžete použít ke správě a upravit RuleSet verze v databázi. Zahrnuje taky aktivitu a hostitele služby pro provádění těchto pravidel.  
  
> [!NOTE]
>  Tato ukázka vyžaduje [Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=96181).  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] poskytuje editor RuleSet v rámci Windows Workflow Foundation (WF). Můžete spustit tento editor dvojitým kliknutím `Policy` aktivity v pracovním postupu; ho serializuje definovaný objekt RuleSet k souboru .rules přidružený k workflowu ( `Policy` aktivity spouští RuleSet instance pracovního postupu). Při sestavování projektu workflow, je soubor .rules zkompilovat do sestavení jako prostředek.  
  
 Součástí této ukázkové zahrnout:  
  
-   Sada pravidel pro grafické uživatelské rozhraní nástroj, který můžete použít k úpravám a správě verzí RuleSet v databázi.  
  
-   Sada pravidel pro služby, který je nakonfigurován na hostiteli aplikace a přistupuje k sady pravidel z databáze.  
  
-   `ExternalPolicy` Aktivity, která požaduje RuleSet ze služby RuleSet a spouští sada pravidel pro pracovní postup.  
  
 Interakce komponenty je znázorněno na obrázku 1. Následující části popisují jednotlivé komponenty.  
  
 ![Koncepční přehled externí ukázka RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Obrázek 1: Ukázka přehled  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>Sada pravidel pro nástroj  
 Snímek obrazovky nástroje RuleSet je znázorněno na obrázku 2. Z **pravidlo úložiště** nabídky, můžete načíst z databáze k dispozici sady pravidel a uložit upravené sady pravidel zpět do úložiště. Konfigurační soubor aplikace obsahuje připojovací řetězec databáze pro databázi RuleSet. Když spustíte nástroj, automaticky se načte sady pravidel z nakonfigurované databáze.  
  
 ![Externí RuleSet Toolket ukázkový výstup](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Obrázek 2: Sada pravidel pro prohlížeč  
  
 Sada pravidel pro nástroj aplikuje hlavní verze a podverze čísla sady pravidel, který vám umožní současně udržovat a uložit více verzí (poskytuje nástroj žádná konfigurace uzamčení nebo jiné funkce správy kromě schopnosti správy verzí). Pomocí nástroje, můžete vytvořit nové verze RuleSet nebo odstranit existující verze. Když kliknete na tlačítko **nový**, nástroj vytvoří nový název RuleSet a použije verze 1.0. Při kopírování na verzi, nástroj vytvoří kopii vybrané RuleSet verze, včetně obsažená pravidla a přiřadí čísla verzí nové, jedinečné. Tato čísla verze jsou založené na čísla verzí pro existující sady pravidel. Můžete změnit název a verze čísla RuleSet pomocí přidružených polí na formuláři.  
  
 Když kliknete na tlačítko **upravit pravidla**, spustí RuleSet editor, jak je znázorněno na obrázku 3.  
  
 ![Ukázkový výstup externích nástrojů RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Obrázek 3: RuleSet editoru  
  
 Toto je znovu hostování editor dialogového okna, která je součástí doplňku Windows Workflow Foundation Visual Studio. Poskytuje stejné funkce, včetně podporu technologie Intellisense. Pravidla jsou vytvořené pro cílový typ (například pracovního postupu), který je přidružen RuleSet v nástroji; Když kliknete na tlačítko **Procházet** v dialogovém okně hlavní nástroj **typ pracovního postupu nebo selektor** dialogové okno se zobrazí, jak je znázorněno na obrázku 4.  
  
 ![Pracovní postup &#47;zadejte výběr](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Obrázek 4: Výběr pracovního postupu nebo typu  
  
 Můžete použít **typ pracovního postupu nebo selektor** dialogovém okně můžete zadat sestavení a konkrétní typ v této sestavě. Tento typ je typ cíle, proti kterému jsou pravidla vytvořena (a spuštění). V mnoha případech cílový typ je pracovní postup nebo jiný typ aktivity. Můžete však spouštění libovolného typu .NET RuleSet.  
  
 Cesta k souboru sestavení a typu `name are stored with the` RuleSet v databázi, takže pokud sada pravidel pro se načítají z databáze, nástroj pokusí automaticky načíst typ cíle.  
  
 Když kliknete na tlačítko **OK** v **typ pracovního postupu nebo selektor** dialogové okno, ověřuje vybraného typu proti RuleSet, a zajistěte tak, že cílový typ všichni členové odkazuje pravidla. Chyby se zobrazují v **chyby ověření** dialogové okno (viz obrázek 5). Můžete pokračovat ve změně navzdory chyby nebo kliknutím na tlačítko **zrušit**. Z **nástroje** nabídky v dialogovém okně hlavní nástroj, můžete kliknout na **ověřením** znovu ověřit verzi RuleSet proti cílové aktivity.  
  
 ![Chyby ověření od externí RuleSet vzorku](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Obrázek 5: Ověření chyby  
  
 Z **Data** nabídky v nástroji můžete importovat a exportovat sady pravidel. Když kliknete na tlačítko **Import**, zobrazí se dialogové okno výběru souboru, ve kterém můžete vybrat soubor .rules. To se může nebo nemusí být soubor původně vytvořil v sadě Visual Studio. Soubor .rules by měl obsahovat serializovaný seznam `RuleDefinitions` instance, který obsahuje kolekci podmínek a kolekce sady pravidel. Nástroj nepoužívá kolekci podmínky, ale použít `RuleDefinitions` .rules formátu umožňující interakci s prostředí Visual Studio.  
  
 Po výběru soubor .rules **RuleSet selektor** otevře se dialogové okno (viz obrázek 6). Dialogové okno můžete použít k výběru sady pravidel ze souboru, který chcete importovat (výchozí hodnota určuje všechny sady pravidel). Sady pravidel v souboru .rules nemají číslo verze, protože jejich verze v rámci projektu WF je stejná jako verze sestavení. Během procesu importu nástroj automaticky přiřadí další dostupné hlavní číslo verze (které můžete změnit po importu); Zobrazí číslo přiřazené verze v **RuleSet selektor** seznamu.  
  
 Pro každý RuleSet mu nástroj pokusí vyhledat přidružený typ ze složky bin\Debug pod umístění souboru .rules (pokud existuje), založené na členy používány RuleSet. Pokud nástroj najde odpovídající více typů, pokusí se vybrat typ na základě shody mezi .rules název souboru a název typu (například `Workflow1` typ odpovídá Workflow1.rules). Pokud existuje více shod, zobrazí se výzva k výběru typu. Pokud tento mechanismus automaticky identifikace nepodaří najít odpovídající sestavení nebo typ, pak po importu můžete kliknout na **Procházet** v dialogovém okně hlavní nástroj přejděte na typ přidružený.  
  
 ![Sada pravidel pro selektor](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Obrázek 6: Sada pravidel pro selektor  
  
 Když kliknete na tlačítko **Export dat** nabídce hlavní nástroj **RuleSet selektor** dialogové okno se zobrazí znovu, ze kterého můžete určit sady pravidel z databáze, kterou mají být exportovány. Když kliknete na tlačítko **OK**, **uložit soubor** otevře se dialogové okno, ve kterém můžete zadat název a umístění výsledný soubor .rules. Protože .rules soubor neobsahuje informace o verzi, můžete zvolit pouze jedna sada pravidel pro verze se daný název RuleSet.  
  
## <a name="policyfromservice-activity"></a>PolicyFromService aktivity  
 Kód pro `PolicyFromService` aktivity je jednoduché. Funguje podobně jako `Policy` aktivita se poskytuje s WF, ale místo načítání cíl RuleSet ze souboru .rules, zavolá hostitele služby k získání RuleSet instance. Pak spustí RuleSet proti k instanci pracovního postupu aktivity root.  
  
 Chcete-li použít aktivitu v pracovním postupu, přidejte odkaz na `PolicyActivities` a `RuleSetService` sestavení z projektu pracovního postupu. Najdete v postupu na konci tohoto tématu informace o tom, jak přidat aktivity do sady nástrojů.  
  
 Po vložení aktivity do pracovního postupu, je nutné zadat název objektu RuleSet ke spuštění. Můžete zadat název jako literálovou hodnotou, nebo vytvořit vazbu k proměnné pracovního postupu nebo vlastnost jiné aktivity. Volitelně můžete zadat číslo verze pro konkrétní sada pravidel pro, který by měl být spuštěn. Pokud necháte výchozí hodnotu 0 pro hlavní verze a podverze čísla, se automaticky poskytuje nejnovější číslo verze v databázi pro aktivity.  
  
## <a name="ruleset-service"></a>Sada pravidel pro služby  
 Služba je odpovědná za načítání zadaná RuleSet verze z databáze a jeho vrácením volání aktivity. Dřív popsané, pokud hlavní verze a podverze hodnoty předané `GetRuleSet` volání jsou obě 0, služba načte nejnovější verzi. V tomto okamžiku se žádné ukládání do mezipaměti RuleSet definice nebo instance; Podobně neexistují žádné funkce pro označení RuleSet verze jako "nasazení" k jejich odlišení od probíhající sady pravidel.  
  
 Databázi nelze přistupovat pomocí služby musí být nakonfigurovaný na hostiteli pomocí konfiguračního souboru aplikace.  
  
#### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
1.  Soubor Setup.sql obsahuje složky, která nastaví RuleSet tabulky používané nástroje a služby. Můžete spustit Setup.cmd dávkový soubor k vytvoření pravidla databáze na SQL Express a nastavit v tabulce RuleSet.  
  
2.  Pokud upravíte dávkového souboru nebo Setup.sql a určit pomocí SQL Express nebo umístění tabulky v databázi pojmenovali jinak než `Rules`, konfigurační soubory aplikace v nástroji RuleSet a `UsageSample` projekty by měl být upraven se stejným informace.  
  
3.  Po spuštění skriptu Setup.sql, můžete vytvořit `ExternalRuleSetToolkit` řešení a potom spusťte sada pravidel pro nástroj z ExternalRuleSetTool projektu.  
  
4.  `RuleSetToolkitUsageSample` Sekvenčního pracovního postupu konzolové aplikace řešení zahrnuje ukázkového pracovního postupu. Pracovní postup se skládá z `PolicyFromService` aktivity a dvě proměnné, `orderValue` a `discount`, na která se spouští cílový RuleSet.  
  
5.  Ukázku použít sestavení `RuleSetToolkitUsageSample` řešení. Z hlavní nabídky Nástroje RuleSet klikněte **Import dat** a přejděte k souboru DiscountRuleSet.rules ve složce RuleSetToolkitUsageSample. Klikněte na tlačítko **pravidlo úložiště-uložit** nabídky možnost uložení importované RuleSet do databáze.  
  
6.  Protože `PolicyActivities` sestavení se odkazuje z ukázkového projektu pracovního postupu, `PolicyFromService` aktivity se zobrazí v pracovním postupu. Ji, ale nezobrazí v panelu nástrojů ve výchozím nastavení. Přidat do sady nástrojů, postupujte takto:  
  
    -   Klikněte pravým tlačítkem na panelu nástrojů a vyberte **zvolit položky** (to může chvíli trvat).  
  
    -   Při **výběr položek sady nástrojů** otevře se dialogové okno, klikněte na tlačítko **aktivity** kartě.  
  
    -   Vyhledejte `PolicyActivities` sestavení v `ExternalRuleSetToolkit` řešení a klikněte na tlačítko **otevřete**.  
  
    -   Ujistěte se, že `PolicyFromService` aktivity je vybraný v **výběr položek sady nástrojů** dialogové okno a potom klikněte na **OK**.  
  
    -   Aktivity by se měla zobrazit v panelu nástrojů v **RuleSetToolkitUsageSample součásti** kategorie.  
  
7.  Sada pravidel pro služba je již nakonfigurována na hostiteli aplikace konzoly pomocí následujícího příkazu v souboru Program.cs.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Můžete také konfigurovat službu na hostiteli pomocí konfiguračního souboru; najdete v dokumentaci k sadě SDK podrobnosti.  
  
9. Konfigurační soubor aplikace se přidá do projektu workflow zadat připojovací řetězec databáze, která se použije službou. To by měl být stejný připojovací řetězec používaný RuleSet nástroj, který odkazuje na databázi, která obsahuje tabulku RuleSet.  
  
10. Teď můžete spustit `RuleSetToolkitUsageSample` projektu stejně jako všechny ostatní konzolové aplikace pracovního postupu. Stiskněte klávesu F5 nebo Ctrl + F5 ve Visual Studiu nebo soubor RuleSetToolkitUsageSample.exe spustit přímo.  
  
    > [!NOTE]
    >  Protože nástroj načte sestavení ukázkové použití, je třeba nejprve zavřít nástroj RuleSet překompilovat ukázce využití.