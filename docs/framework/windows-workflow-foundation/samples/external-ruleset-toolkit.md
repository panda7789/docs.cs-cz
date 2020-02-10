---
title: Sada nástrojů pro externí sadu pravidel
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: eb59b02d469788b23126f4e02c5b7ae5a63081f0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094667"
---
# <a name="external-ruleset-toolkit"></a>Sada nástrojů pro externí sadu pravidel

Normálně při použití pravidel v rámci aplikace pracovního postupu jsou tato pravidla součástí sestavení. V některých scénářích můžete chtít udržovat RuleSets odděleně od sestavení, aby bylo možné je aktualizovat bez opětovného sestavení a nasazení sestavení pracovního postupu. Tato ukázka vám umožní spravovat a upravovat RuleSets v databázi a přistupovat k nim z pracovního postupu za běhu. To umožňuje spuštěným instancím pracovních postupů automaticky začlenit RuleSet změny.

Ukázka externí sady nástrojů RuleSet obsahuje nástroj založený na model Windows Forms, který můžete použít ke správě a úpravám RuleSet verzí v databázi. Zahrnuje také aktivitu a hostitelskou službu pro spouštění těchto pravidel.

> [!NOTE]
> Tato ukázka vyžaduje [Microsoft SQL Server](/sql).

Visual Studio poskytuje editor RuleSet jako součást programovací model Windows Workflow Foundation (WF). Tento editor můžete spustit dvojitým kliknutím na aktivitu `Policy` v pracovním postupu. serializace definovaného objektu RuleSet do souboru. Rules přidruženého k pracovnímu postupu (aktivita `Policy` spouští instanci RuleSet v rámci pracovního postupu). Soubor. Rules je zkompilován do sestavení jako prostředek při sestavování projektu pracovního postupu.

Mezi součásti této ukázky patří:

- Nástroj grafického uživatelského rozhraní RuleSet, pomocí kterého můžete upravovat a spravovat verze RuleSet v databázi.

- Služba RuleSet, která je nakonfigurovaná na hostitelské aplikaci a přistupuje k RuleSets z databáze.

- Aktivita `ExternalPolicy`, která žádá o RuleSet ze služby RuleSet a spustí RuleSet v rámci pracovního postupu.

Interakce komponent je znázorněna na následujícím obrázku. Následující části popisují jednotlivé součásti.

![Diagram znázorňující přehled ukázek externích RuleSet Toolkit.](./media/external-ruleset-toolkit/ruleset-toolkit-overview.gif)

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`

## <a name="ruleset-tool"></a>Nástroj RuleSet

Následující obrázek je snímek obrazovky nástroje RuleSet. V nabídce **úložiště pravidla** můžete načíst dostupné RuleSets z databáze a uložit upravené RuleSets zpátky do úložiště. Konfigurační soubor aplikace poskytuje připojovací řetězec databáze pro databázi RuleSet. Když nástroj spustíte, automaticky načte RuleSets z nakonfigurované databáze.

![Snímek obrazovky zobrazující prohlížeč RuleSet](./media/external-ruleset-toolkit/ruleset-browser-dialog.gif)

Nástroj RuleSet používá pro RuleSets hlavní a podverze čísla a umožňuje tak souběžně udržovat a ukládat více verzí (nástroj kromě možnosti správy verzí neposkytuje žádné uzamykání ani jiné funkce správy konfigurace). Pomocí tohoto nástroje můžete vytvořit nové verze RuleSet nebo odstranit existující verze. Když kliknete na **Nový**, nástroj vytvoří nový název RuleSet a použije verzi 1,0. Při kopírování verze nástroj vytvoří kopii vybrané verze RuleSet, včetně obsažených pravidel, a přiřadí nová a jedinečná čísla verzí. Tato čísla verzí jsou založená na číslech verzí stávajícího RuleSets. Můžete změnit název a číslo verze RuleSet pomocí přidružených polí ve formuláři.

Po kliknutí na **upravit pravidla**se spustí editor RuleSet, jak je znázorněno na následujícím obrázku:

![Snímek obrazovky znázorňující Editor RuleSet](./media/external-ruleset-toolkit/ruleset-editor-dialog.gif)

Toto je opětovné hostování dialogového okna editoru, které je součástí programovací model Windows Workflow Foundationho doplňku sady Visual Studio. Nabízí stejné funkce, včetně podpory technologie IntelliSense. Pravidla jsou vytvořena proti cílovému typu (například pracovní postup), který je přidružen k RuleSet v nástroji. Když kliknete na **Procházet** v hlavním dialogovém okně nástroje, zobrazí se dialogové okno pro **Výběr pracovního postupu nebo typu** , jak je znázorněno na obrázku 4.

![Výběr &#47;typu pracovního postupu](./media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")

Obrázek 4: selektor pracovního postupu/typu

Můžete použít dialog pro **Výběr pracovního postupu nebo typu** k určení sestavení a konkrétního typu v rámci tohoto sestavení. Tento typ je cílový typ, proti kterému jsou pravidla vytvořená (a jsou spuštěná). V mnoha případech je cílovým typem pracovní postup nebo nějaký jiný typ aktivity. Můžete však spustit RuleSet proti libovolnému typu rozhraní .NET.

Cesta k souboru sestavení a typ `name are stored with the` RuleSet v databázi, takže když je RuleSet načten z databáze, nástroj se pokusí automaticky načíst cílový typ.

Po kliknutí na tlačítko **OK** v dialogovém okně pro **Výběr pracovního postupu nebo typu** ověří vybraný typ proti RuleSet, aby se zajistilo, že cílový typ obsahuje všechny členy, na které odkazují pravidla. Chyby se zobrazují v dialogovém okně **chyby ověřování** . Můžete se rozhodnout, že budete pokračovat v změně bez ohledu na chyby, nebo klikněte na **Zrušit**. V nabídce **nástroje** v hlavním dialogovém okně nástroje můžete kliknout na **ověřit** a znovu ověřit verzi RuleSet proti cílové aktivitě.

![Snímek obrazovky zobrazující dialog chyby ověřování](./media/external-ruleset-toolkit/validation-errors-dialog.png)

Z nabídky **data** v nástroji můžete importovat a exportovat RuleSets. Po kliknutí na **importovat**se zobrazí dialogové okno Výběr souboru, ve kterém můžete vybrat soubor. Rules. To může nebo nemusí být soubor, který byl původně vytvořen v aplikaci Visual Studio. Soubor. Rules by měl obsahovat serializovanou instanci `RuleDefinitions`, která obsahuje kolekci podmínek a kolekci RuleSets. Nástroj nepoužívá kolekci podmínek, ale používá formát `RuleDefinitions`. Rules k umožnění interakce s prostředím sady Visual Studio.

Po výběru souboru. Rules se zobrazí dialogové okno **RuleSet Selector** . Pomocí dialogového okna můžete vybrat RuleSets ze souboru, který chcete importovat (výchozí nastavení určuje všechny RuleSets). RuleSets v souboru. Rules nemají čísla verzí, protože jejich správa verzí v rámci projektu WF je stejná jako verze sestavení. Během procesu importu nástroj automaticky přiřadí další dostupné hlavní číslo verze (které můžete po importu změnit). v seznamu **selektoru RuleSet** můžete zobrazit čísla přiřazených verzí.

Pro každý RuleSet, který importuje, se nástroj pokusí najít přidružený typ ze složky bin\Debug v umístění souboru. Rules (pokud existuje) na základě členů použitých ve RuleSet. Pokud nástroj najde více odpovídajících typů, pokusí se zvolit typ založený na shodě mezi názvem souboru. Rules a názvem typu (například `Workflow1` typ odpovídá Workflow1. Rules). Pokud existuje více shod, budete vyzváni k výběru typu. Pokud tento mechanismus automatického identifikace nenajde odpovídající sestavení nebo typ, potom po importu můžete kliknout na **Procházet** v hlavním dialogovém okně nástroje a přejít tak k přidruženému typu. RuleSet selektor znázorňuje následující obrázek:

![Snímek obrazovky s dialogovým oknem pro výběr RuleSet](./media/external-ruleset-toolkit/ruleset-selector-dialog.gif)

Když kliknete na **exportovat data** z hlavní nabídky nástroje, zobrazí se znovu dialog pro **Výběr RuleSet** , ze kterého můžete určit RuleSets z databáze, která se má exportovat. Po kliknutí na tlačítko **OK**se zobrazí dialogové okno **Uložit soubor** , ve kterém můžete zadat název a umístění výsledného souboru. Rules. Vzhledem k tomu, že soubor. Rules neobsahuje informace o verzi, můžete vybrat pouze jednu verzi RuleSet s daným RuleSet názvem.

## <a name="policyfromservice-activity"></a>Aktivita PolicyFromService

Kód aktivity `PolicyFromService` je jednoduchý. Funguje podobně jako aktivita `Policy` poskytovaná pomocí WF, ale místo načítání cílového RuleSet ze souboru. Rules volá hostitelskou službu, aby získala instanci RuleSet. Pak spustí RuleSet proti instanci aktivity kořenového pracovního postupu.

Chcete-li použít aktivitu v pracovním postupu, přidejte odkaz na `PolicyActivities` a `RuleSetService` sestavení z projektu pracovního postupu. Diskuzi o tom, jak přidat aktivitu do sady nástrojů, najdete v postupu na konci tohoto tématu.

Po umístění aktivity do pracovního postupu musíte zadat název RuleSet, který se má spustit. Název můžete zadat jako hodnotu literálu nebo vytvořit vazby na proměnnou pracovního postupu nebo vlastnost jiné aktivity. Volitelně můžete zadat čísla verzí pro konkrétní RuleSet, která se mají spustit. Pokud necháte výchozí hodnotu 0 pro čísla hlavní verze a podverze, bude se pro aktivitu automaticky poskytovat číslo nejnovější verze v databázi.

## <a name="ruleset-service"></a>Služba RuleSet

Služba zodpovídá za načtení zadané verze RuleSet z databáze a její vrácení do volající aktivity. Jak je popsáno výše, pokud hodnoty hlavní a dílčí verze předané ve `GetRuleSet` volání jsou obě 0, služba načte nejnovější verzi. V tomto okamžiku není ukládání definic nebo instancí RuleSet do mezipaměti; Podobně nejsou k dispozici žádné funkce pro označení verzí RuleSet jako "nasazené", aby je bylo možné odlišit od probíhajících RuleSets.

Databáze, ke které má být služba k dispozici, by měla být nakonfigurovaná na hostiteli pomocí konfiguračního souboru aplikace.

#### <a name="to-run-the-tool"></a>Spuštění nástroje

1. Složka, ve které se nastavuje tabulka RuleSet používaná nástrojem a službou, obsahuje soubor Setup. SQL. Spuštěním dávkového souboru Setup. cmd můžete vytvořit databázi pravidel v SQL Express a nastavit tabulku RuleSet.

2. Pokud soubor Batch nebo Setup. SQL upravíte a nechcete použít SQL Express nebo umístit tabulku do databáze s názvem jinou než `Rules`, konfigurační soubory aplikace v nástroji RuleSet a v projektech `UsageSample` by se měly upravovat se stejnými informacemi.

3. Po spuštění skriptu Setup. SQL můžete sestavit `ExternalRuleSetToolkit` řešení a pak spustit nástroj RuleSet z projektu ExternalRuleSetTool.

4. Řešení konzolové aplikace pro `RuleSetToolkitUsageSample` sekvenční pracovní postup obsahuje ukázkový pracovní postup. Pracovní postup se skládá z aktivity `PolicyFromService` a dvou proměnných, `orderValue` a `discount`, proti kterým je cílový RuleSet spuštěn.

5. Chcete-li použít ukázku, sestavte `RuleSetToolkitUsageSample` řešení. Pak z hlavní nabídky nástroje RuleSet klikněte na **data – importovat** a přejděte na soubor DiscountRuleSet. Rules ve složce RuleSetToolkitUsageSample. Kliknutím na možnost v nabídce **úložiště pravidla – Uložit** uložte importované RuleSet do databáze.

6. Vzhledem k tomu, že `PolicyActivities` sestavení je odkazováno z ukázkového projektu pracovního postupu, aktivita `PolicyFromService` se zobrazí v pracovním postupu. Ve výchozím nastavení se ale nezobrazí v sadě nástrojů. Chcete-li jej přidat do sady nástrojů, postupujte následovně:

    - Klikněte pravým tlačítkem myši na panel nástrojů a vyberte možnost **zvolit položky** (Tato akce může chvíli trvat).

    - Když se zobrazí dialogové okno **zvolit položky sady nástrojů** , klikněte na kartu **aktivity** .

    - V řešení `ExternalRuleSetToolkit` přejděte na `PolicyActivities` sestavení a klikněte na **otevřít**.

    - Zajistěte, aby byla v dialogovém okně **zvolit položky sady nástrojů** vybrána aktivita `PolicyFromService` a klikněte na tlačítko **OK**.

    - Tato aktivita by se teď měla zobrazit v sadě nástrojů v kategorii **komponent RuleSetToolkitUsageSample** .

7. Služba RuleSet je už nakonfigurovaná na hostiteli konzolové aplikace pomocí následujícího příkazu v Program.cs.

    ```csharp
    workflowRuntime.AddService(new RuleSetService());
    ```

8. Službu můžete na hostiteli nakonfigurovat taky pomocí konfiguračního souboru. Podrobnosti najdete v dokumentaci k sadě SDK.

9. Do projektu pracovního postupu se přidá konfigurační soubor aplikace, který určuje připojovací řetězec pro databázi, kterou má služba používat. Mělo by se jednat o stejný připojovací řetězec, který používá nástroj RuleSet, který odkazuje na databázi, která obsahuje tabulku RuleSet.

10. Nyní můžete spustit projekt `RuleSetToolkitUsageSample` stejným způsobem jako jakékoli jiné konzolové aplikace pracovního postupu. Stiskněte F5 nebo CTRL + F5 v sadě Visual Studio nebo spusťte soubor RuleSetToolkitUsageSample. exe přímo.

    > [!NOTE]
    > Je nutné zavřít nástroj RuleSet pro rekompilaci ukázky použití, protože nástroj načte ukázkové sestavení pro použití.
