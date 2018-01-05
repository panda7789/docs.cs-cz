---
title: "Použití automatizace uživatelského rozhraní pro automatizované testování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
caps.latest.revision: "26"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 128af9a015d25985b7075f5b670fea36c6773267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-ui-automation-for-automated-testing"></a>Použití automatizace uživatelského rozhraní pro automatizované testování
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] může být užitečné jako rozhraní pro programový přístup v automatizované testování scénáře.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje jednotné objektový model, který umožňuje všechny [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] architektury vystavit komplexní a bohaté funkce dostupné a snadno automatizované způsobem.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]byl vyvinut jako následníka k [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]existující framework určená k poskytování řešení pro zpřístupnění ovládací prvky a aplikace. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]nebyl navržen s testovací automatizace v paměti, i když se vyvinul tuto roli z důvodu velmi podobné požadavky na usnadnění přístupu a automatizace. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], kromě poskytování přesnější řešení pro usnadnění přístupu, je také určená speciálně pro poskytuje robustní funkce pro automatizované testování. Například [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] spoléhá na jednom rozhraní jak vystavit informace o uživatelském rozhraní a shromažďovat informace, které na produkty; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odděluje dva modely.  
  
 Zprostředkovatel i klienta jsou nutné k implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mohla sloužit jako nástroj na automatizovaných testů. Zprostředkovatelé automatizace uživatelského rozhraní jsou aplikace, jako je Microsoft Word, Excel, a na základě jiné aplikace třetí strany nebo ovládací prvky [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] operačního systému. Klienti automatizace uživatelského rozhraní patří automatizovaných testů skripty a aplikací využívajících technologie usnadnění.  
  
> [!NOTE]
>  Tohoto přehledu je cílem prezentují nových a vylepšených automatizované testování možností [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tento přehled není určená k poskytování informace o usnadnění funkce a nebude adresy usnadnění jiné služby než potřeby.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automatizace uživatelského rozhraní v zprostředkovatele  
 Pro [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na automatizaci, musí vývojář aplikace nebo ovládací prvek podívejte se na co můžete provádět akce na koncového uživatele na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí standardní interakce klávesnici a myš.  
  
 Jednou tyto klíče akce byly zjištěny a odpovídající [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory (to znamená vzory ovládacích prvků, aby odpovídaly funkce a chování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element) by měla být implementována na ovládací prvek. Například uživatelské interakce s ovládacím prvkem pole se seznamem (například spustit dialogové okno) obvykle zahrnuje rozbalení a sbalení pole se seznamem skrytí nebo zobrazení Seznam položek, výběrem položky z tohoto seznamu nebo prostřednictvím vstup z klávesnice, přidejte novou hodnotu.  
  
> [!NOTE]
>  S jinými modely usnadnění musí vývojáři shromáždit informace přímo z jednotlivých tlačítka, nabídky nebo jiných ovládacích prvků. Bohužel se každých – typ ovládacího prvku se dodává v desítek malé změny. Jinými slovy i když deset variace pushbutton může všechny fungovat stejným způsobem a provádí stejnou funkci, se musí být zacházeno jako jedinečný ovládací prvky. Neexistuje žádný způsob, jak zjistit, že tyto ovládací prvky jsou funkčně rovnocenné. Vzory ovládacích prvků byly vyvinuty představují tyto společné chování ovládacího prvku. Další informace najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementace automatizace uživatelského rozhraní  
 Jak už bylo zmíněno dříve, bez jednotný model poskytované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], je vyžadován nástroje test a vývojáři vědět informace specifické pro framework tak, aby získal vlastnosti a chování ovládacích prvků v dané platformy. Vzhledem k tomu může být několik různých uživatelského rozhraní architektury přítomen jeden kdykoli v rámci [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] operačních systémů, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], a [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)], může být složitý úkol k testování více aplikací s ovládacími prvky, které pravděpodobně Podobně jako u. Například následující tabulka popisuje názvy vlastností konkrétní rozhraní potřebnou k načtení název (nebo text) přidružené k ovládacímu prvku tlačítko a zobrazuje ekvivalentní jedné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost.  
  
|Automatizace uživatelského rozhraní – typ ovládacího prvku|Uživatelské rozhraní Framework|Určité vlastnosti Framework|Vlastnosti automatizace uživatelského rozhraní|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Tlačítko|Windows Presentation Foundation|Obsah|NameProperty|  
|Tlačítko|Win32|Popisek|NameProperty|  
|Image|HTML|ALT|NameProperty|  
  
 Zprostředkovatelé automatizace uživatelského rozhraní jsou zodpovědní za mapování vlastností konkrétní rozhraní jejich ovládacích prvků na ekvivalent [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
 Informace o implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] u zprostředkovatele lze nalézt na [zprostředkovatelů automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informace o implementaci vzory ovládacích prvků je k dispozici na [vzory ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) a [vzoru prvků Text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automatizace uživatelského rozhraní v klientovi  
 Cílem mnoho nástrojů automatizovaných testů a scénáře je konzistentní a Opakovatelný manipulaci uživatelského rozhraní. To může zahrnovat konkrétní ovládací prvky prostřednictvím záznam a přehrávání testu skriptů, které iteraci v rámci sérii obecné akcí pro skupinu ovládacích prvků testování částí.  
  
 Komplikace, který vyplývá z automatizované aplikace je potíže synchronizace testu s dynamické cíl. Například ovládací prvek seznamu, například ten, který obsažené ve Správci úloh systému Windows, který zobrazí seznam aktuálně spuštěných aplikací. Vzhledem k tomu, že položky v seznamu jsou mimo kontrolu testovací aplikaci aktualizuje dynamicky, pokouší zopakovat výběr konkrétní položku v seznamu všechny konzistence není možné. Podobné problémy může nastat při pokusu o opakování ve změní fokus jednoduché [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se mimo kontrolu testovací aplikace.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programový přístup  
 Programový přístup poskytuje schopnost napodobují prostřednictvím kódu, všechny interakce a prostředí, které jsou vystavené tradiční myši a vstup z klávesnice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Umožňuje programový přístup prostřednictvím pět součásti:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Stromu usnadňuje navigace prostřednictvím strukturu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Stromu vychází z kolekce hWnd společnosti. Další informace najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Elementy automatizace jsou jednotlivé komponenty v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Často to mohou být podrobnější než popisovačem hWnd. Další informace najdete v tématu [přehled typů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Vlastnosti automatizace poskytnout konkrétní informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy. Další informace najdete v tématu [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Vzory ovládacích prvků definovat určitý aspekt funkce ovládacího prvku; se může skládat z vlastností, metoda, událostí a informace o struktuře. Další informace najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Události automatizace zadejte oznamování událostí a informace. Další informace najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Klíčové vlastnosti automatizace testu  
 Možnost jednoznačně identifikovat a následně vyhledat libovolný ovládací prvek v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] poskytuje základ pro aplikace v automatizovaných testů pracovat, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Existuje několik [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používané klienty a poskytovatelů, které pomáhají v této vlastnosti.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznačně identifikuje element automation z uzlů na stejné úrovni. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nelokalizovaný, na rozdíl od vlastnosti, jako <xref:System.Windows.Automation.AutomationElement.NameProperty> , je obvykle lokalizované Pokud produkt získá dodaný v několika jazycích. V tématu [používání vlastnosti AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nezaručuje jedinečnou identitu v rámci stromu automatizace. Aplikace může například obsahovat ovládacího prvku nabídka s více položek nabídek nejvyšší úrovně, které obsahovat více podřízených položek nabídky. Tyto položky sekundárním nabídce může být označeno obecné schématu, jako je například "Item1, položka 2, Item3, atd.", což duplicitní identifikátory pro podřízené mezi nabídek na nejvyšší úrovni.  
  
#### <a name="controltype"></a>ControlType  
 Určuje typ ovládacího prvku reprezentována element automatizace. Důležité informace lze odvodit z znalosti o typ ovládacího prvku. V tématu [typy – Přehled ovládacího prvku automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Toto je textový řetězec, který identifikuje nebo vysvětlující ovládacího prvku. <xref:System.Windows.Automation.AutomationElement.NameProperty>musí být použit s opatrní, protože je možné lokalizovat. V tématu [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementace automatizace uživatelského rozhraní v testovací aplikace  
  
|||  
|-|-|  
|Přidejte odkazy na automatizace uživatelského rozhraní.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Dll je nezbytné pro klienty automatizace uživatelského rozhraní jsou zde uvedeny.<br /><br /> -UIAutomationClient.dll poskytuje přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rozhraní API klienta.<br />-UIAutomationClientSideProvider.dll umožňuje automatizovat [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky. V tématu [podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll poskytuje přístup k určité typy definované v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Přidat <xref:System.Windows.Automation> oboru názvů.|Tento obor názvů obsahuje všechno, co klienti automatizace uživatelského rozhraní musí použít možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kromě zpracování textu.|  
|Přidat <xref:System.Windows.Automation.Text> oboru názvů.|Tento obor názvů obsahuje všechno, co potřebuje klientů automatizace uživatelského rozhraní používat možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zpracování textu.|  
|Najít ovládací prvky, které vás zajímají|Skripty automatizovaných testů vyhledejte elementů automatizace uživatelského rozhraní, které představují ovládací prvky zájmu v rámci stromu automatizace.<br /><br /> Získání elementů automatizace uživatelského rozhraní pomocí kódu několika způsoby.<br /><br /> -Zadat dotaz [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí <xref:System.Windows.Automation.Condition> příkaz. To je obvykle kde jazykově neutrální <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> se používá. **Poznámka:** <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> lze zjistit pomocí nástroje, jako je Inspect.exe aby bylo možné vytvořit seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností ovládacího prvku. <br /><br /> -Použít <xref:System.Windows.Automation.TreeWalker> třída procházení celý [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu nebo jejich podmnožinu.<br />-Sledovat fokus.<br />-Použijte hWnd ovládacího prvku.<br />-Použijte obrazovky umístění, jako je například umístění myší.<br /><br /> V tématu [získání elementů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Získat vzory ovládacích prvků|Vzory ovládacích prvků vystavit společné chování pro funkčně podobné ovládací prvky.<br /><br /> Po vyhledání ovládacích prvků, které vyžadují testování, skripty automatizovaných testů získat vzory ovládacích prvků, které vás zajímají z těchto elementů automatizace uživatelského rozhraní. Například <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků pro tlačítko typické funkce nebo <xref:System.Windows.Automation.WindowPattern> pro funkci okno – vzor ovládacích prvků.<br /><br /> V tématu [vzory – Přehled ovládacího prvku automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatizace uživatelského rozhraní|Skripty automatizovaných testů můžete nyní řídit všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zájmu z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework pomocí informací a funkcí, které jsou zveřejněné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Související nástroje a technologie  
 Existuje řada souvisejících nástrojů a technologií, které podporují automatizované testování s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Je Inspect.exe [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] aplikace, která slouží k shromažďování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace pro poskytovatele a klient vývoj a ladění. Je součástí Inspect.exe [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   Zpřístupní MSAABridge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace, které [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientů. Primární cílem přemostění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] k [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] je umožnit existující [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klienti umožňuje interakci s libovolnou architekturu, která je implementována [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpečení  
 Informace o zabezpečení, najdete v části [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md)
