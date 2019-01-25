---
title: Usnadnění – doporučené postupy
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 0f33fb559bb4bf47beebc836a093f4b784559609
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674809"
---
# <a name="accessibility-best-practices"></a>Usnadnění – doporučené postupy
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Implementace následujících osvědčených postupů v ovládacích prvcích nebo aplikace zvýší jejich přístupnost pro uživatelé, kteří používají [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] zařízení. Mnohé z těchto osvědčených postupů zaměřit na funkční [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] návrhu. Každý osvědčený postup zahrnuje informace o implementaci pro [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací prvky nebo aplikace. V mnoha případech je práce, která musí splňovat tyto osvědčené postupy již součástí [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programový přístup  
 Programový přístup zahrnuje zajistit, aby všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky jsou označeny jako hodnoty vlastností jsou přístupné a odpovídající události jsou vyvolány. Pro úroveň standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, většina tuto práci se již provádí prostřednictvím <xref:System.Windows.Automation.Peers.AutomationPeer>. Vlastní ovládací prvky vyžadují další práce k zajištění, že programový přístup správně implementovaná.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Povolit programový přístup ke všem prvky uživatelského rozhraní a Text  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)] prvky by měl povolit programový přístup. Pokud [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] řídit, podporu pro programový přístup je zahrnuta v ovládacím prvku. Pokud je ovládací prvek pomocí vlastního ovládacího prvku – musíte zaškrtnout ovládací prvek, který se má rozčlenit do podtříd z běžného ovládacího prvku nebo ovládací prvek, který se má rozčlenit do podtříd z ovládacího prvku – pak můžete <xref:System.Windows.Automation.Peers.AutomationPeer> implementaci pro oblasti, které může být nutné změny.  
  
 Umožňuje řídit se osvědčeným postupem [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] dodavatelů k identifikaci a manipulaci s prvky váš produkt [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Názvy, názvy a popisy ustaví objekty uživatelského rozhraní, snímky a stránek  
 Technologie pro usnadnění, zejména čtečky obrazovky, použít název k pochopení umístění rámce, objekt nebo stránka v navigační schéma. Proto musí být velmi popisný název. Například název webové stránky z "webové stránce společnosti Microsoft" je nepoužitelný, pokud uživatel přešel hluboko do některé konkrétní oblasti. Popisný název je velmi důležité pro uživatele, kteří jsou nevidomí a závisí na čtečkách obrazovky. Stejně tak v případě [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací prvky, <xref:System.Windows.Automation.AutomationProperties.NameProperty> a <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> jsou důležité pro [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] zařízení.  
  
 Umožňuje řídit se osvědčeným postupem [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s k identifikaci a manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na ukázky ovládacích prvků a v aplikacích.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Ujistěte se, že programový události jsou aktivovány všechny aktivity uživatelského rozhraní  
 Umožňuje řídit se osvědčeným postupem [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s tak, aby naslouchala na změny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a informovat uživatele o těchto změnách.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Uživatelská nastavení  
 Osvědčený postup v této části zajistí, že ovládací prvky nebo aplikace nesmí být přepsána uživatelská nastavení.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Všechna nastavení Celosystémovým respektovat a nejsou v konfliktu s funkcí usnadnění přístupu  
 Uživatelům můžete pomocí ovládacího panelu nastavit některá systémová příznaky; nastavení další příznaky lze nastavit programově. Toto nastavení by neměla změnit ovládací prvky nebo aplikace. Aplikace musí navíc podporují nastavení přístupnost z jejich hostitelských operačních systémů.  
  
 Následující tento osvědčený postup umožňuje uživatelům vědět, že tato nastavení se nezmění aplikace a nastavení usnadnění.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Vizuální uživatelské rozhraní návrhu  
 Osvědčené postupy v této části zajistěte, aby ovládací prvky nebo aplikace efektivně používat color a Image a budou moct využívat [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Neprogramujte barvy pevně  
 Uživatelů, kteří mají barvu nevidomí, mají slabý zrak nebo používáte černobílé obrazovky nebudou moct používat aplikace s pevně zakódované barvami.  
  
 Následující tento osvědčený postup umožňuje uživatelům upravit kombinace barev podle individuálních potřeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Vysoký kontrast – podpora a všechny systémové atributy zobrazení  
 Aplikace by neměl narušit nebo zakažte nastavení kontrastu vybrané uživatele, systémová, výběr barev, nebo jiné nastavení systémová zobrazení a atributy. Systémová nastavení přijata uživatelem vylepšit dostupnost aplikace, proto by neměl být zakázána nebo ignorovány aplikacemi. Barva byste měli použít ve svých správnou kombinaci popředí na pozadí zajistit správné kontrast. Neměli kombinovat nesouvisejících barvy a barvy by neměl vrátit zpět.  
  
 Mnoho uživatelů vyžadují určité kombinace vysokého kontrastu, jako je bílý text na černém pozadí. Kreslení tyto obrácené, jako černý text bílém pozadí způsobí, že na pozadí tvořit přesah přes popředí a mohou ztížit čtení pro některé uživatele.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Zkontrolujte všechny uživatelské rozhraní správně škáluje podle jakékoli nastavení DPI  
 Ujistěte se, že všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] správně můžete škálovat podle [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] nastavení. Také se ujistěte, že [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přizpůsobit prvky na obrazovce 1024 × 768 s 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 Osvědčené postupy v této části Ujistěte se, že vyřeší navigace pro ovládací prvky a aplikace.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Poskytuje rozhraní klávesnice pro všechny prvky uživatelského rozhraní  
 Zarážky, zejména v případě, že vedení pečlivě naplánovat, uživatelům udělit další způsob, jak přejít [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měla poskytnout následující rozhraní klávesnice:  
  
-   zarážky pro všechny ovládací prvky, které uživatelé můžou komunikovat s, jako je například tlačítka, odkazy nebo pole se seznamem  
  
-   logické pořadí  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Zobrazit fokus klávesnice  
 Uživatelé potřebují vědět, který objekt má fokus klávesnice, tak, aby se mohli předvídat efekt jejich stisknutí kláves. Abyste měli na očích fokus klávesnice, použijte barvy, písma nebo grafické třeba obdélníky nebo zvětšení. Zvýrazněte zvukově fokus klávesnice, změňte svazek, od nebo tónů kvality.  
  
 Aby nedocházelo k záměně, by měla aplikace skrýt všechny ukazatele fokusu visual a dim možnosti, které se nacházejí v neaktivní windows (nebo podokna).  
  
 Aplikace by měl provést pomocí fokus klávesnice:  
  
-   jedna položka by měla vždy mít fokus klávesnice  
  
-   fokus klávesnice by měly být viditelné a zřejmé  
  
-   Výběr a/nebo cílené položky by měl být vizuálně zvýrazněn  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Podpora navigace standardy a schémata navigace výkonné  
 Různé aspekty navigaci pomocí klávesnice poskytují různé způsoby pro uživatele, přejděte [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měla poskytnout následující rozhraní klávesnice:  
  
-   klávesové zkratky a podtržené přístupových klíčů pro všechny příkazy, nabídky a ovládací prvky  
  
-   klávesové zkratky pro důležité odkazy  
  
-   mají všechny položky nabídky přístupové klávesy; klávesové zkratky máte všechna tlačítka, všechny příkazy mají klíče akcelerátoru k.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nenechte myši umístění v konfliktu s navigaci pomocí klávesnice  
 Kurzor myši nesmí ovlivňovat navigaci pomocí klávesnice. Pro příklad, pokud je ukazatel myši umístěn někde a uživatel je navigaci pomocí klávesnice, kliknutí myší nemělo stát. není-li zahájit uživatel.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Multimodální rozhraní  
 Osvědčené postupy v této části ověřte tuto aplikaci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zahrnuje alternativy pro vizuální prvky.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Zadejte uživatelsky volitelných ekvivalenty pro prvky  
 Pro každý prvek jiné textové zadání uživatelsky volitelných ekvivalent text, záznamy o studiu nebo zvukový popisy, jako jsou alternativní text, titulky nebo vizuální zpětnou vazbu.  
  
 Jiných textových prvků pokrývají širokou škálu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, včetně: Image, image mapa oblastí, animace, aplety, snímky, skripty, grafické tlačítka, zvuky, samostatné zvukové soubory a video. Jiných textových prvků jsou důležité, pokud obsahují vizuální informace, řeč nebo obecné zvukových informací, že uživatel potřebuje přístup k Chcete-li pochopit obsah [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Použít barvu, ale také nabízí alternativu barva  
 Použití barvy k vylepšení, zdůrazňují nebo ještě jednou zdůraznit informace zobrazené jiným způsobem, ale nekomunikují informace pomocí samostatně barvy. Uživatelé, kteří jsou nevidomí barvu nebo mají monochromatický zobrazení musí alternativy k barvě.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Standardní vstupní rozhraní API pomocí volání nezávislých na zařízení  
 Volání nezávislých na zařízení zkontrolujte funkci rovnosti klávesnici a myš, při poskytování [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] s potřebné informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Automation.Peers>
- [Ovládací prvek NumericUpDown vlastní motiv a ukázka podpora automatizace uživatelského rozhraní](https://msdn.microsoft.com/library/9aed3c10-68eb-419e-a57f-1d2af15a8253)
- [Pokyny pro návrh uživatelského rozhraní klávesnice](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
