---
title: Usnadnění – doporučené postupy
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: c6f0f31260ffae43e59703ef53dd7ef30a73320b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180302"
---
# <a name="accessibility-best-practices"></a>Usnadnění – doporučené postupy
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Implementace následujících doporučených postupů v ovládacích prvcích nebo aplikacích zlepší jejich přístupnost pro lidi, kteří používají zařízení pro pomocnou technologii. Mnohé z těchto osvědčených [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] postupů se zaměřují na dobrý design. Každý osvědčený postup obsahuje [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] informace o implementaci ovládacích prvků nebo aplikací. V mnoha případech práce na splnění těchto osvědčených postupů je již zahrnuta v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvcích.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Programový přístup  
 Programový přístup zahrnuje zajištění, že jsou označeny všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky, hodnoty vlastností jsou vystaveny a jsou vyvolány příslušné události. U [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] standardních ovládacích prvků se <xref:System.Windows.Automation.Peers.AutomationPeer>většina této práce již provádí prostřednictvím . Vlastní ovládací prvky vyžadují další práci, aby bylo zajištěno, že programový přístup je správně implementován.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Povolení programového přístupu ke všem prvkům uživatelského rozhraní a textu  
 Prvky uživatelského rozhraní (UI) by měly umožnit programový přístup. Pokud [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je standardní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, podpora pro programový přístup je součástí ovládacího prvku. Pokud je ovládací prvek vlastní ovládací prvek – ovládací prvek, který byl podtřídy z společného ovládacího <xref:System.Windows.Automation.Peers.AutomationPeer> prvku nebo ovládací prvek, který byl podtřídy z Control – pak je nutné zkontrolovat implementaci pro oblasti, které mohou vyžadovat změny.  
  
 V návaznosti na tento osvědčený postup umožňuje dodavatelům asistenčních technologií [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]identifikovat prvky produktu a manipulovat s nimi .  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umístění názvů, názvů a popisů na objekty, rámce a stránky v ui  
 Asistenční technologie, zejména programy pro čtení z obrazovky, používají název k pochopení umístění rámce, objektu nebo stránky v navigačním schématu. Proto musí být název velmi popisný. Například název webové stránky "Webová stránka společnosti Microsoft" je k ničemu, pokud uživatel přecvál hluboko do určité oblasti. Popisný název je důležitý pro uživatele, kteří jsou nevidomí a jsou závislí na čtečkách obrazovky. Podobně pro [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací <xref:System.Windows.Automation.AutomationProperties.NameProperty> prvky a <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> jsou důležité pro zařízení asistenční technologie.  
  
 V návaznosti na tento osvědčený postup umožňuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] asistenční technologie k identifikaci a manipulaci v ukázkové ovládací prvky a aplikace.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Zajistit, aby se programové události aktivované všemi aktivitami v oblasti ui  
 V návaznosti na tento osvědčený postup umožňuje asistenční [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] technologie naslouchat změny v a upozornit uživatele o těchto změnách.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>User Settings  
 Osvědčený postup v této části zajišťuje, že ovládací prvky nebo aplikace nepřepíší nastavení uživatele.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Respektujte všechna nastavení celého systému a nezasahujte do funkcí usnadnění přístupu  
 Uživatelé mohou pomocí Ovládacích panelů nastavit některé příznaky pro celý systém. ostatní příznaky lze nastavit programově. Tato nastavení by neměla být změněna ovládacími prvky nebo aplikacemi. Aplikace musí také podporovat nastavení usnadnění jejich hostitelského operačního systému.  
  
 V návaznosti na tento osvědčený postup umožňuje uživatelům nastavit nastavení usnadnění a vědět, že tato nastavení nebudou změněna aplikacemi.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Vizuální návrh ui  
 Doporučené postupy v této části zajišťují, že ovládací prvky nebo aplikace používají barvy a obrázky efektivně a mohou být používány asistenčními technologiemi.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Neprogramujte barvy pevně  
 Lidé, kteří jsou barvoslepé, mají slabozraké nebo používají černobílou obrazovku, nemusí být schopni používat aplikace s pevně zakódovanými barvami.  
  
 V návaznosti na tento osvědčený postup umožňuje uživatelům upravit barevné kombinace na základě individuálních potřeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Podpora vysokého kontrastu a všech atributů zobrazení systému  
 Aplikace by neměly narušovat nebo zakazovat nastavení kontrastu v celém systému, výběr barev ani jiná nastavení a atributy zobrazení v celém systému. Nastavení pro celý systém přijatá uživatelem zvyšují dostupnost aplikací, takže by neměly být aplikacemi zakázány nebo ignorovány. Barva by měla být použita v jejich správné kombinaci popředí na pozadí, aby byl zajištěn správný kontrast. Nesouvisející barvy by neměly být smíchány a barvy by neměly být stornovány.  
  
 Mnoho uživatelů vyžaduje specifické kombinace s vysokým kontrastem, například bílý text na černém pozadí. Kreslení těchto obrácený, jako černý text na bílém pozadí způsobí, že pozadí krvácet přes popředí a může ztížit čtení pro některé uživatele.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Zajistěte správné měřítko všech ui podle libovolného nastavení DPI  
 Ujistěte [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se, že všechny mohou správně škálovat podle libovolného nastavení podle velikosti na palec (dpi). Také zajistěte, aby [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se prvky vešly na obrazovku 1024 x 768 se 120 tečkami na palec (dpi).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navigace  
 Doporučené postupy v této části zajišťují, že navigace byla určena pro ovládací prvky a aplikace.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Poskytnout rozhraní klávesnice pro všechny prvky uživatelského rozhraní  
 Zarážky tabulátoru, zejména při pečlivém plánování, poskytují uživatelům jiný způsob navigace v . [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]  
  
 Aplikace by měly poskytovat následující rozhraní klávesnice:  
  
- Zarážky tabulátoru pro všechny ovládací prvky, se kterými může uživatel pracovat, například tlačítka, odkazy nebo seznamy  
  
- logické pořadí polí  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Zobrazit fokus klávesnice  
 Uživatelé potřebují vědět, který objekt má fokus klávesnice, aby mohli předvídat účinek svých úhozů. Chcete-li zvýraznit fokus klávesnice, použijte barvy, písma nebo grafiku, například obdélníky nebo zvětšení. Chcete-li slyšitelně zvýraznit zaostření klávesnice, změňte hlasitost, výšku nebo tónovou kvalitu.  
  
 Aby nedošlo k záměně, aplikace by měly skrýt všechny indikátory vizuálního zaostření a ztlumené výběry, které jsou umístěny v neaktivních oknech (nebo podložích).  
  
 Aplikace by měly dělat následující akce s fokusem klávesnice:  
  
- jedna položka by měla mít vždy fokus klávesnice  
  
- zaostření klávesnice by mělo být viditelné a zřejmé  
  
- výběry a/nebo zaostřené položky by měly být vizuálně zvýrazněny  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Podpora navigačních standardů a výkonných navigačních schémat  
 Různé aspekty navigace pomocí klávesnice poskytují uživatelům [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]různé způsoby navigace v souboru .  
  
 Aplikace by měly poskytovat následující rozhraní klávesnice:  
  
- klávesové zkratky a podtržené přístupové klávesy pro všechny příkazy, nabídky a ovládací prvky  
  
- klávesové zkratky k důležitým odkazům  
  
- všechny položky nabídky mají přístupový klíč; všechna tlačítka mají klávesy akcelerátoru, všechny příkazy mají klávesu akcelerátoru.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nedovolte, aby umístění myši zasahovalo do navigace pomocí klávesnice  
 Umístění myši by nemělo zasahovat do navigace pomocí klávesnice. Pokud je například myš umístěna někde a uživatel naviguje pomocí klávesnice, nemělo by dojít k klepnutí myší, pokud není iniciováno uživatelem.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Multimodální rozhraní  
 Doporučené postupy v této [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] části zajistit, že aplikace obsahuje alternativy pro vizuální prvky.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Zadejte uživatelsky volitelné ekvivalenty pro netextové prvky  
 Pro každý netextový prvek zadejte uživatelsky volitelný ekvivalent pro text, přepisy nebo zvukové popisy, jako je alternativní text, titulky nebo vizuální zpětná vazba.  
  
 Netextové prvky pokrývají širokou škálu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, včetně: obrázků, oblastí obrazové mapy, animací, aplet, rámečků, skriptů, grafických tlačítek, zvuků, samostatných zvukových souborů a videa. Netextové prvky jsou důležité, pokud obsahují vizuální informace, řeč nebo obecné zvukové informace, ke [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]kterým uživatel potřebuje přístup, aby porozuměl obsahu rozhraní .  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Použít barvu, ale také poskytnout alternativy k barvě  
 Pomocí barvy můžete vylepšit, zvýraznit nebo zopakovat informace zobrazené jinými prostředky, ale nesdělujte informace pouze pomocí barvy. Uživatelé, kteří jsou barvoslepí nebo mají monochromatický displej, potřebují alternativy k barvě.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Použití standardních vstupních rozhraní API s voláními nezávislými na zařízení  
 Volání nezávislá na zařízení zajišťují rovnost funkcí klávesnice a myši a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]zároveň poskytují asistenční technologii potřebné informace o rozhraní .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.Peers>
- [Vlastní ovládací prvek NumericUpDown s ukázkou podpory motivu a automatizace uživatelského rozhraní](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Pokyny pro návrh uživatelského rozhraní klávesnice](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
