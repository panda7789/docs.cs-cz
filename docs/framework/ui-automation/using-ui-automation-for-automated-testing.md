---
title: Použití automatizace uživatelského rozhraní pro automatizované testování
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 023c85591ba484e0b8f97a8ef71a4f65a2f05ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691785"
---
# <a name="using-ui-automation-for-automated-testing"></a>Použití automatizace uživatelského rozhraní pro automatizované testování
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] může být užitečné jako rozhraní pro programový přístup v automatizované testování scénářů.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje jednotný objektový model, který umožňuje všem [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] architektury vystavit funkčnost komplexní a funkčně bohaté přístupné a snadno automatizované způsobem.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] byl vyvinut jako nástupce k [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] je existující architekturu navržené pro poskytování řešení pro zpřístupnění ovládací prvky a aplikace. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] díky automatizaci testů v úvahu nebyl navržen, i když se rozvinul tuto roli z důvodu velmi podobné požadavky na usnadnění přístupu a automatizace. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], kromě toho, že přesnější řešení pro usnadnění přístupu, je také určená speciálně k zajištění robustní funkce pro automatické testování. Například [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] spoléhá na jedno rozhraní i zveřejnit informace o uživatelském rozhraní a shromažďovat informace vyžadované na produkty; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odděluje dva modely.  
  
 Zprostředkovatel i klientů je potřeba implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mohla být užitečná jako nástroj automatizovaného testu. Zprostředkovatelé automatizace uživatelského rozhraní jsou aplikace, jako je Microsoft Word, Excel, a na základě jiné aplikace třetí strany nebo ovládací prvky [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] operačního systému. Klienti automatizace uživatelského rozhraní zahrnovat automatizované testovací skripty a technologie pro usnadnění aplikace.  
  
> [!NOTE]
>  Tento přehled zamýšlíte a představte nové a vylepšené automatizované testování možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Tento přehled není určená k poskytování informací o usnadnění funkce a nebude adresa usnadnění jiné než v případě potřeby.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automatizace uživatelského rozhraní ve zprostředkovateli  
 Pro [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] automatizovat, musí vývojář aplikace nebo ovládací prvek zaměřit na to co můžete provádět akce na koncového uživatele na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí standardní interakce klávesnice a myši.  
  
 Jednou tyto klíče byly identifikovány akce, odpovídající [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory (to znamená, vzorů ovládacích prvků, které zrcadlí funkce a chování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element) by měla být implementována v ovládacím prvku. Například interakce uživatele s ovládacím prvkem pole se seznamem (jako je například spuštění dialogového okna) obvykle zahrnuje rozbalení a sbalení pro skrytí nebo zobrazení seznamu položek pole se seznamem, výběrem položky z tohoto seznamu nebo přidat novou hodnotu prostřednictvím vstup z klávesnice.  
  
> [!NOTE]
>  S jinými modely usnadnění musí vývojáři shromáždit informace přímo z jednotlivých tlačítek, nabídek nebo další ovládací prvky. Každý typ ovládacího prvku je bohužel dostupná v desítky malé změny. Jinými slovy i když deset odchylky pushbutton může všechny fungují stejně a provádí stejnou funkci, se musí být zacházeno jako jedinečnými ovládacími prvky. Neexistuje žádný způsob, jak zjistit, že tyto ovládací prvky jsou funkčně ekvivalentní. Vzory ovládacích prvků byly vyvinuty k reprezentaci tyto běžné chování ovládacího prvku. Další informace najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementace automatizace uživatelského rozhraní  
 Jak už bylo zmíněno dříve, bez jednotný model poskytované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], nástroje pro testování a vývojáři je potřeba vědět informace specifické pro architekturu, aby bylo možné zveřejnit vlastnosti a chování ovládacích prvků v dané rozhraní. Protože může existovat několik jiné architektury uživatelského rozhraní k dispozici jeden kdykoli v operačních systémech Windows, včetně [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], a Windows Presentation Foundation (WPF), může být složitý úkol k testování s více aplikacemi ovládací prvky, které mohou vypadat podobně. Například v následující tabulce popisuje názvy vlastností pro konkrétní rozhraní potřebný k načtení název (nebo text) přidružený k ovládacímu prvku tlačítko a zobrazuje ekvivalentní jedné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost.  
  
|Typ ovládacího prvku automatizace uživatelského rozhraní|Architekturu uživatelského rozhraní|Určité vlastnosti rozhraní|Vlastnosti automatizace uživatelského rozhraní|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Tlačítko|Windows Presentation Foundation|Obsah|NameProperty|  
|Tlačítko|Win32|Titulek|NameProperty|  
|Image|HTML|ALT|NameProperty|  
  
 Zprostředkovatelé automatizace uživatelského rozhraní jsou zodpovědné za mapování vlastnosti specifické pro architekturu jejich ovládacích prvků na ekvivalentní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
 Informace o implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve zprostředkovateli lze nalézt v [zprostředkovatelů automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informace o implementaci vzorů ovládacích prvků je k dispozici na [vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) a [vzoru Text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automatizace uživatelského rozhraní v klientovi  
 Cílem mnoho scénářů a nástroje pro automatizované testování je konzistentní a opakovatelné zpracování uživatelského rozhraní. To může zahrnovat testování konkrétní ovládání pomocí záznamu a přehrávání testů skripty, které iteraci v rámci řady obecných akcí pro skupinu ovládacích prvků.  
  
 Komplikace, který vznikl z automatizovaných aplikací jsou problémy synchronizace test dynamické cíl. Například ovládací prvek seznamu, jako jsou například obsažené ve Správci úloh Windows, který zobrazuje seznam aktuálně spuštěných aplikací. Protože položky v seznamu se dynamicky aktualizují mimo ovládací prvek testovací aplikace, pokus opakovat výběr konkrétní položku v seznamu se žádné konzistence není možné. Podobné problémy můžou nastat také při pokusu o opakování změní jednoduché fokus v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , která je mimo ovládací prvek testovací aplikace.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programový přístup  
 Programový přístup poskytuje možnost napodobovat prostřednictvím kódu, všechny interakce a prostředí, které jsou vystavené tradiční myš a klávesnice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umožňuje programový přístup přes pět součástí:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Usnadňuje navigaci struktura stromu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Stromu je sestaven z kolekce od hWnd. Další informace najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Pohyb mezi elementy automatizace jsou jednotlivé komponenty v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. To může často být podrobnější než popisovačem hWnd. Další informace najdete v tématu [přehled typů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Vlastnosti automatizace obsahují podrobné informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy. Další informace najdete v tématu [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Vzory ovládacích prvků definovat konkrétní aspekt funkce ovládacího prvku. se může skládat z vlastnosti, metody, události a informace o struktuře. Další informace najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Události automatizace poskytují oznámení událostí a informace. Další informace najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Klíčové vlastnosti pro automatizaci testů  
 Schopnost jedinečně identifikovat a následně vyhledejte libovolný ovládací prvek v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] poskytuje základ pro automatizované testovací aplikace má provést výpočet, který [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Existuje několik [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používané klienty a poskytovatelé, které pomáhají v této vlastnosti.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznačně identifikuje prvek automatizace z na stejné úrovni. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> není lokalizována, na rozdíl od vlastnosti, jako <xref:System.Windows.Automation.AutomationElement.NameProperty> , který je obvykle lokalizován Pokud získá vydání produktu v různých jazycích. Zobrazit [používání vlastnosti AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nezaručuje jedinečnou identitu v rámci stromu automatizace. Aplikace může například obsahovat ovládací prvek nabídky s více položek nabídek nejvyšší úrovně, které pak obsahovat více podřízených položek nabídky. Tyto položky sekundární nabídka může být označeno obecný schématu, např "Item1, položka 2, Item3, atd.", umožňuje duplicitní identifikátory pro děti napříč položky nabídek nejvyšší úrovně.  
  
#### <a name="controltype"></a>ControlType  
 Určuje typ ovládacího prvku reprezentována element služby automation. Důležité informace lze odvodit z znalost typ ovládacího prvku. Zobrazit [přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Toto je textový řetězec, který identifikuje nebo vysvětlující ovládacího prvku. <xref:System.Windows.Automation.AutomationElement.NameProperty> by měl třeba používat opatrně, protože může být lokalizována. Zobrazit [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementace automatizace uživatelského rozhraní v aplikaci Test  
  
|||  
|-|-|  
|Přidejte odkazy na automatizaci uživatelského rozhraní.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Knihovny dll je nezbytné pro klienty automatizace uživatelského rozhraní jsou zde uvedeny.<br /><br /> -UIAutomationClient.dll poskytuje přístup k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rozhraní API na straně klienta.<br />-UIAutomationClientSideProvider.dll poskytuje možnost automatizovat [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků. Zobrazit [podpora automatizace uživatelského rozhraní pro standardní ovládací prvky](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll poskytuje přístup ke konkrétní typy definované v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Přidat <xref:System.Windows.Automation> oboru názvů.|Tento obor názvů obsahuje všechno, co klienti automatizace uživatelského rozhraní se musí využívat možnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s výjimkou zpracování textu.|  
|Přidat <xref:System.Windows.Automation.Text> oboru názvů.|Tento obor názvů obsahuje všechno, co třeba klienti automatizace uživatelského rozhraní pro využití funkcí aplikace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zpracování textu.|  
|Najít ovládací prvky, které vás zajímají|Automatizované testovací skripty vyhledejte pohyb mezi elementy automatizace uživatelského rozhraní, které představují ovládací prvky, které vás zajímají v rámci stromu automatizace.<br /><br /> Získání elementů automatizace uživatelského rozhraní s kódem několika způsoby.<br /><br /> -Dotazování [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí <xref:System.Windows.Automation.Condition> příkazu. To je obvykle kde neutrální jazyk <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> se používá. **Poznámka:**  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Lze zjistit pomocí nástroje, jako je Inspect.exe, aby bylo možné vytvořit seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností ovládacího prvku. <br /><br /> – Použijte <xref:System.Windows.Automation.TreeWalker> třídy k procházení celého [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu nebo její podmnožinu.<br />-Sledovat fokus.<br />– Použijte hWnd ovládacího prvku.<br />– Použijte umístění na obrazovce, jako je například umístění kurzoru myši.<br /><br /> Zobrazit [získání elementů automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Získat vzorů ovládacích prvků|Vzory ovládacích prvků vystavit společné chování pro funkce podobné ovládací prvky.<br /><br /> Po nalezení ovládací prvky, které vyžadují testování, automatizované testovací skripty získat vzorů ovládacích prvků, které vás zajímají z těchto elementů automatizace uživatelského rozhraní. Například <xref:System.Windows.Automation.InvokePattern> – vzor ovládacích prvků pro tlačítka typické funkce nebo <xref:System.Windows.Automation.WindowPattern> – vzor ovládacích prvků pro okno funkce.<br /><br /> Zobrazit [přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatizace uživatelského rozhraní|Automatizované skripty můžete ovládat některé [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z oblastí zájmu, od [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework pomocí informace a funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Související nástroje a technologie  
 Existuje několik souvisejících nástrojů a technologií, které podporují automatizované testování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Je Inspect.exe [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] aplikaci, která slouží ke shromažďování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace pro poskytovatele a klient vývoj a ladění. Je součástí Inspect.exe [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   Zpřístupňuje MSAABridge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informace, které [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientů. Hlavním cílem přemostění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] k [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] je, aby byl existující [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientů možnost pracovat s libovolné architektury, která se má implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpečení  
 Informace o zabezpečení, najdete v části [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Viz také:
- [Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md)
