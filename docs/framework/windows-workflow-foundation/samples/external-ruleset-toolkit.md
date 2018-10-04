---
title: Externí Toolkit sady pravidel
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: f545d083bb6caf9daca3ce553d0a1ee6711b0062
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584257"
---
# <a name="external-ruleset-toolkit"></a>Externí Toolkit sady pravidel
Obvykle při použití pravidla v rámci aplikace pracovního postupu pravidla jsou součástí sestavení. V některých případech můžete chtít spravovat sady pravidel odděleně od sestavení tak, aby bylo možné aktualizovat bez nutnosti opětovného sestavování a nasazování sestavení pracovního postupu. Tato ukázka umožňuje spravovat a upravovat sady pravidel v databázi a zpřístupnit tyto sady pravidel z pracovního postupu za běhu. To umožňuje spuštěné instance pracovního postupu, jak automaticky začlenit změny sady pravidel.

 Ukázka externích nástrojů sady pravidel obsahuje nástroj formulářů Windows, který vám pomůže spravovat a upravovat sady pravidel verze v databázi. Zahrnuje také aktivitu a hostitelská služba pro provádění těchto pravidel.

> [!NOTE]
>  Tato ukázka vyžaduje [Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=96181).  
  
 Visual Studio poskytuje v editoru sady pravidel v rámci Windows Workflow Foundation (WF). Můžete spustit tento editor dvojitým kliknutím `Policy` aktivity v pracovním postupu; serializuje definovaný objekt RuleSet .rules souboru spojené s pracovním postupem ( `Policy` aktivity spouští instanci sady pravidel pro pracovní postup). Při sestavování projektu pracovního postupu je .rules soubor zkompilovaný do sestavení jako prostředek.  
  
 Součástí této ukázky zahrnout:  
  
-   Sada pravidel pro grafické uživatelské rozhraní nástroj, který můžete použít k úpravám a správě verzí sady pravidel v databázi.  
  
-   Služba sady pravidel, která je nakonfigurovaná na hostitelskou aplikaci a budou k dispozici sady pravidel z databáze.  
  
-   `ExternalPolicy` Aktivitu, která požádá službu sady pravidel pravidel a spouští sada pravidel pro pracovní postup.  
  
 Na obrázku 1 je zobrazena interakce součástí. Následující části popisují jednotlivé komponenty.  
  
 ![Koncepční přehled externí ukázková RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Obrázek 1: Přehled ukázky  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>Nástroje sady pravidel  
 Snímek obrazovky nástroje sady pravidel je znázorněno na obrázku 2. Z **pravidlo Store** nabídku, můžete načíst dostupné sady pravidel z databáze a uložit změny pravidel zpět do úložiště. Konfigurační soubor aplikace obsahuje připojovací řetězec databáze pro databázi sady pravidel. Při spuštění nástroje, automaticky se načte sady pravidel z nakonfigurované databáze.  
  
 ![Externí sady pravidel Toolket ukázkový výstup](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Obrázek 2: Sada pravidel pro prohlížeč  
  
 Nástroje sady pravidel se týká čísla hlavní verze a podverze sady pravidel, což vám umožní současně udržovat a uložit více verzí (nástroj poskytuje žádná konfigurace uzamčení nebo jiné funkce správy kromě funkce správy verzí). Pomocí nástroje, můžete vytvořit nové verze sady pravidel nebo odstranit existující verze. Po kliknutí na **nový**, nástroj vytvoří nový název sady pravidel a použije verze 1.0. Při kopírování s verzí, nástroj vytvoří kopii vybrané verze sady pravidel, včetně obsažených pravidel a přiřadí čísla verzí nové, jedinečné. Tato čísla verze jsou založeny na čísla verzí pro existující sady pravidel. Můžete změnit název a verzi čísla sady pravidel pomocí přidružené pole ve formuláři.  
  
 Po kliknutí na **upravit pravidla**, spustí editor sady pravidel, jak je znázorněno na obrázku 3.  
  
 ![Ukázkový výstup externích nástrojů sady pravidel](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Obrázek 3: RuleSet editoru  
  
 Toto je opětovné hostování editor dialogového okna, která je součástí doplňku sady Visual Studio Windows Workflow Foundation. Nabízí stejné funkce, včetně podporu technologie Intellisense. Pravidla pro čtení zleva doprava vůči cílový typ (například pracovní postup), který je spojen s sady pravidel v nástroji; Po kliknutí na **Procházet** v dialogovém okně hlavní nástroj **selektor pracovního postupu a typu** dialogového okna se zobrazí, jak je znázorněno na obrázku 4.  
  
 ![Pracovní postup &#47;výběru typu](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Obrázek 4: Typ pracovního postupu/selektor  
  
 Můžete použít **selektor pracovního postupu a typu** dialogové okno k zadání sestavení a určitého typu v rámci tohoto sestavení. Tento typ je cílový typ, proti kterému se pravidla vytvářejí (a spustit). V mnoha případech je cílový typ pracovního postupu nebo jiný typ aktivity. Však můžete spustit sady pravidel pro libovolný typ rozhraní .NET.  
  
 Cesta k souboru sestavení a typu `name are stored with the` sady pravidel v databázi tak, že pokud sada pravidel je načtena z databáze, nástroj se pokusí automaticky načíst typ cíle.  
  
 Po kliknutí na **OK** v **selektor pracovního postupu a typu** dialogového okna, ověřuje vybraného typu proti sady pravidel, zajistit, že všechny členy, které odkazují pravidla cílového typu. Zobrazují se chyby v **chyby ověření** dialogového okna (viz obrázek 5). Můžete pokračovat ve změně bez ohledu na chyby, nebo klikněte na **zrušit**. Z **nástroje** nabídky v dialogovém okně hlavní nástroj, můžete kliknout na **ověřit** znovu ověřit verzi sady pravidel na cílovou aktivitu.  
  
 ![Chyby ověření z externí ukázková RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Obrázek 5: Ověření chyby  
  
 Z **Data** nabídky v nástroji, můžete importovat a exportovat sady pravidel. Po kliknutí na **Import**, zobrazí se dialogové okno Výběr souboru, ve kterém můžete vybrat soubor .rules. To může nebo nemusí být soubor původně vytvořil v sadě Visual Studio. Soubor .rules by měl obsahovat serializovaného `RuleDefinitions` instance, která obsahuje kolekci podmínek a kolekce pravidel. Nástroj nevyužívá kolekci podmínek, ale nepoužívá `RuleDefinitions` .rules formátu umožňující interakci s prostředím Visual Studio.  
  
 Po výběru souboru .rules **selektor sady pravidel** se zobrazí dialogové okno (viz obrázek 6). Použijete dialogové okno pro výběr sady pravidel ze souboru, který chcete importovat (výchozí hodnota určuje všechny sady pravidel). Sady pravidel v souboru .rules nemají číslo verze, protože jejich správy verzí v rámci projektu pracovního postupu je stejná jako verze sestavení. Během procesu importu nástroj automaticky přiřadí další k dispozici hlavní číslo verze (které můžete změnit po importu); můžete zobrazit čísla verzí přiřazené v **selektor sady pravidel** seznamu.  
  
 U každé sady pravidel, který importuje nástroj pokusí vyhledat přidruženého typu ve složce bin\Debug podle umístění souboru .rules (pokud existuje), závisí na členy používané sady pravidel. Pokud nástroj zjistí, několik odpovídajících typů, pokusí se zvolte typ na základě shody mezi .rules název souboru a název typu (například `Workflow1` typu odpovídá Workflow1.rules). Pokud existuje více shod, zobrazí se výzva k výběru typu. Pokud tento mechanismus automatického identifikace nepodaří najít odpovídající sestavení nebo typ, pak po dokončení importu můžete kliknout na **Procházet** v dialogovém okně hlavní nástroj přejděte do přidruženého typu.  
  
 ![Selektor sady pravidel](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Obrázek 6: Výběr sady pravidel  
  
 Po kliknutí na **Export dat** nabídce hlavní nástroj **selektor sady pravidel** se zobrazí dialogové okno znovu, ze kterého můžete určit sady pravidel z databáze, která mají být exportovány. Po kliknutí na **OK**, **uložit soubor** se zobrazí dialogové okno, ve kterém můžete zadat název a umístění souboru pro výslednou .rules. Protože .rules soubor neobsahuje informace o verzi, můžete vybrat pouze jedna verze sady pravidel se daný název sady pravidel.  
  
## <a name="policyfromservice-activity"></a>Aktivita PolicyFromService  
 Kód `PolicyFromService` aktivity je jednoduché. Funguje to stejně jako `Policy` aktivity, které jsou součástí pracovního postupu, ale místo cílové sady pravidel se načítají ze souboru .rules, volá hostitelská služba pro získání instance sady pravidel. Pak spustí sady pravidel pro instanci kořenové aktivity pracovního postupu.  
  
 Chcete-li použít aktivitu v pracovním postupu, přidejte odkaz na `PolicyActivities` a `RuleSetService` sestavení z projektu pracovního postupu. Najdete v postupu na konci tohoto tématu informace o tom, jak přidat aktivity do panelu nástrojů.  
  
 Po zahájení aktivity v pracovním postupu, musíte zadat název sady pravidel ke spuštění. Můžete zadat název jako hodnotu literálu nebo připojení k proměnné pracovního postupu nebo vlastnosti druhé aktivity. Volitelně můžete zadat čísla verzí pro konkrétní sady pravidel, která by se měl spustit. Pokud necháte výchozí hodnotu 0 pro čísla hlavní verze a podverze, nejnovější číslo verze v databázi je poskytována automaticky pro aktivity.  
  
## <a name="ruleset-service"></a>Služba sady pravidel  
 Služba je zodpovědná za načítání zadaná verze sady pravidel z databáze a vrátilo se volání aktivity. Jak jsme uvedli, pokud hlavní verze a podverze hodnoty předané `GetRuleSet` volání jsou obě 0, služba načte nejnovější verzi. V tomto okamžiku není žádné ukládání do mezipaměti definice sady pravidel nebo instance; Podobně neexistují žádné funkce pro označení "nasazení" je odlišili od sady pravidel v průběhu s verzemi sady pravidel.  
  
 Databáze, kterou chcete mít přístup služby musí být nakonfigurovaný na hostiteli pomocí konfiguračního souboru aplikace.  
  
#### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
1.  Složka, který nastaví kolekci pravidel tabulky používané nástroje a služby obsahuje Setup.sql souboru. Můžete spustit Setup.cmd dávkový soubor k vytvoření pravidla databáze na SQL Express a nastavení v tabulce sady pravidel.  
  
2.  Pokud upravíte dávkového souboru nebo Setup.sql a zadejte použít systém SQL Express nebo umístění tabulky v databázi pojmenovali jinak než `Rules`, konfigurační soubory aplikace v nástroji sady pravidel a `UsageSample` projekty by měl být upraven se stejným informace.  
  
3.  Po spuštění skriptu Setup.sql můžete sestavit `ExternalRuleSetToolkit` řešení a pak spustit sady pravidel nástroje z ExternalRuleSetTool projektu.  
  
4.  `RuleSetToolkitUsageSample` Konzolová aplikace sekvenčního pracovního postupu řešení zahrnuje ukázkového pracovního postupu. Pracovní postup se skládá z `PolicyFromService` aktivity a dvě proměnné, `orderValue` a `discount`, na která se spouští cílový sady pravidel.  
  
5.  Použitím této ukázky sestavení `RuleSetToolkitUsageSample` řešení. Sady pravidel nástroje hlavní nabídky, klikněte na tlačítko **Import dat** a odkazování na soubor DiscountRuleSet.rules ve složce RuleSetToolkitUsageSample. Klikněte na tlačítko **Store ukládání pravidlo** nabídky uložte do databáze importované sady pravidel.  
  
6.  Vzhledem k tomu, `PolicyActivities` sestavení se odkazuje z ukázkového projektu pracovního postupu a `PolicyFromService` aktivity se zobrazí v pracovním postupu. Ne, ale nezobrazí v sadě nástrojů ve výchozím nastavení. Chcete-li přidat ho do panelu nástrojů, postupujte takto:  
  
    -   Klikněte pravým tlačítkem na panelu nástrojů a vyberte **zvolit položky** (to může chvíli trvat).  
  
    -   Při **zvolit položky nástrojů** se zobrazí dialogové okno, klikněte na tlačítko **aktivity** kartu.  
  
    -   Přejděte `PolicyActivities` sestavení v `ExternalRuleSetToolkit` řešení a klikněte na tlačítko **otevřít**.  
  
    -   Ujistěte se, že `PolicyFromService` aktivity je vybrán v **zvolit položky nástrojů** dialogového okna a pak klikněte na tlačítko **OK**.  
  
    -   Aktivita by se měla objevit na panelu nástrojů v **RuleSetToolkitUsageSample součásti** kategorie.  
  
7.  Služba sady pravidel je už nakonfigurovaná na hostiteli aplikace konzoly pomocí následujícího příkazu v souboru Program.cs.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Můžete také nakonfigurovat službu na hostiteli pomocí konfiguračního souboru; Viz podrobnosti naleznete v dokumentaci sady SDK.  
  
9. Konfigurační soubor aplikace se přidá do projektu pracovního postupu zadat připojovací řetězec pro databáze, kterou chcete používat službu. To by měl být stejný připojovací řetězec používaný projektem nástroj sady pravidel, která odkazuje na databázi, která obsahuje tabulku sady pravidel.  
  
10. Teď můžete spustit `RuleSetToolkitUsageSample` projektu stejně jako jakékoli jiné Konzolová aplikace pracovního postupu. Stiskněte klávesu F5 nebo Ctrl + F5 v sadě Visual Studio nebo spusťte soubor RuleSetToolkitUsageSample.exe přímo.  
  
    > [!NOTE]
    >  Sada pravidel nástroj znovu zkompilovat ukázkový používání musí ukončit, protože se nástroj načte sestavení ukázkový používání.