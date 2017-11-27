---
title: "Usnadnění – doporučené postupy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d8714bb211c649d783cb1cfc46058e3b097def26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-best-practices"></a>Usnadnění – doporučené postupy
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Implementace následujících osvědčených postupů v ovládacích prvcích nebo aplikace se zvýšit jejich usnadnění pro osoby, které používají [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] zařízení. Řadu tyto doporučené postupy pro soustředit na dobré [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] návrhu. Každý osvědčený postup obsahuje informace o implementaci k [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací prvky nebo aplikace. V mnoha případech je práce, kterou splňovat tyto doporučené postupy pro již součástí [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programový přístup  
 Programový přístup zahrnuje kontrolu, všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jsou označeny elementy, jsou zveřejněné hodnoty vlastností a příslušné události jsou vyvolány. Pro standardní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, většina tato práce je už hotové prostřednictvím <xref:System.Windows.Automation.Peers.AutomationPeer>. Vlastní ovládací prvky vyžadují další kroky k zajištění správně provádění programový přístup.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Povolit programový přístup ke všem prvky uživatelského rozhraní a Text  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]elementy musí povolit programový přístup. Pokud [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je standard [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] řídit, podporu pro programový přístup je zahrnuta v ovládacím prvku. Pokud ovládací prvek je vlastního ovládacího prvku – ovládací prvek, který má byla rozčlenění z běžného ovládacího prvku nebo ovládací prvek, který má byla rozčlenění z ovládacího prvku – pak můžete zkontrolovat <xref:System.Windows.Automation.Peers.AutomationPeer> implementace pro oblasti, které může být nutné změny.  
  
 Následující tento osvědčený postup umožňuje [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] modulů plug-in pro manipulaci s prvky svůj produkt [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umístěte jména, názvy a popisy na rámce, objektů uživatelského rozhraní a stránky  
 Technologie pro usnadnění, zejména čtečky obrazovky slouží k pochopení umístění stránka ve schématu navigační rámečku, objekt nebo název. Proto musí být velmi popisný název. Název webové stránky z "webovou stránku Microsoft" je například nepoužitelný, pokud uživatel přešel hluboko do některé konkrétní oblasti. Popisný název je velmi důležitá pro uživatele, kteří jsou skrytá a závisí na čtečky obrazovky. Stejně tak v případě [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ovládací prvky, <xref:System.Windows.Automation.AutomationProperties.NameProperty> a <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> jsou důležité pro [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] zařízení.  
  
 Následující tento osvědčený postup umožňuje [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]k identifikaci a manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Ukázka ovládací prvky a v aplikacích.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Ujistěte se, že programový události jsou aktivovány všechny aktivity uživatelského rozhraní  
 Následující tento osvědčený postup umožňuje [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s tak, aby naslouchala na změny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a upozornit uživatele o těchto změnách.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Uživatelská nastavení  
 Osvědčený postup v této části zajistí, že ovládací prvky nebo aplikace přepsat nastavení uživatele.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Dodržovat všechny systémové nastavení a nebudou v konfliktu s funkcí usnadnění přístupu  
 Uživatele můžete použít ovládací panely nastavit některé systémové příznaky; nastavení další příznaky můžete nastavit prostřednictvím kódu programu. Ovládací prvky nebo aplikacemi, neměli byste ji měnit tato nastavení. Aplikace také musí podporovat nastavení usnadnění jejich operačního systému hostitele.  
  
 Následující tento osvědčený postup umožňuje uživatelům vědět, že tato nastavení se nezmění aplikace a nastavení usnadnění.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Návrh Visual uživatelského rozhraní  
 Osvědčené postupy v této části zajistěte, aby ovládací prvky nebo aplikace efektivně používat barvy a bitové kopie a mohou být používán [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Neprogramujte barvy pevně  
 Lidé, kteří jsou barva skrytá, slabým zrakem nebo používáte černobílý obrazovky nemusí být možné používat aplikace s pevně zakódovaným barvy.  
  
 Následující tento osvědčený postup umožňuje uživatelům upravit podle potřeb jednotlivých kombinace barev.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Podpora vysoký kontrast a všechny atributy zobrazení systému  
 Aplikace by neměly by narušilo nebo zakázat kontrast vybrané uživatele, systémová nastavení, výběr barev, nebo jiné zobrazení systémového nastavení a atributy. Systémové nastavení přijat uživatele zvýšit usnadnění aplikací, takže by neměly být zakázán nebo ignorovány aplikace. Barva slouží v jejich správnou kombinaci popředí na pozadí zajistit správné kontrastu. By neměl být ve smíšeném nesouvisejícími barvy a barvy by neměla vrátit zpět.  
  
 Řada uživatelů vyžadovat určité kombinace vysoký kontrast, jako je například bílý text na černém pozadí. Kreslení tyto odstínech, jako černý text na bílé pozadí způsobí, že na pozadí tvořit přesah přes popředí a může ztížit čtení pro některé uživatele.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Ujistěte se, všechny uživatelského rozhraní správně škáluje žádné nastavení DPI  
 Ujistěte se, že všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] možné správně škálovat podle [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] nastavení. Také zajistěte, aby [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy nevešla obrazovky 1024 × 768 s 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 Osvědčené postupy v této části Ujistěte se, že navigační vyřeší pro ovládací prvky a aplikace.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Poskytují rozhraní klávesnice pro všechny prvky uživatelského rozhraní  
 Karta zastaví, zejména v případě, že pečlivě naplánovat, uživatelům udělit jiný způsob, jak procházet [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měl poskytovat rozhraní následující klávesové:  
  
-   Karta zastaví pro všechny ovládací prvky, které uživatel mohl pracovat s, například tlačítka, odkazy nebo seznamy  
  
-   logické pořadí  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Zobrazit fokus klávesnice  
 Uživatelé potřebovat vědět, který objekt má fokus klávesnice, takže se můžete odhadnout účinku jejich stisknutí kláves. Pokud chcete zvýraznit fokus klávesnice, použijte barvy, písma nebo grafiky, jako je například obdélníků nebo zvětšení. Abyste měli na očích zvukově fokus klávesnice, změňte svazku, výšky nebo tónů kvality.  
  
 Pokud chcete předejít nejasnostem, by měla aplikace skrýt všechny indikátory visual fokus a dim možnosti, které se nacházejí v neaktivní windows (nebo podokna).  
  
 Aplikace by měl provést na následujícím obrázku se fokus klávesnice:  
  
-   jednu položku měli mít vždy fokus klávesnice  
  
-   fokus klávesnice by měl být viditelné a zřejmé  
  
-   Výběr anebo cílených položky by měl mít vizuálně zvýrazněná  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Podpora navigace standardů a výkonné navigační schémata  
 Různé aspekty navigace klávesnice poskytují různé způsoby přechody [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikace by měl poskytovat rozhraní následující klávesové:  
  
-   klávesové zkratky a podtržené přístupové klávesy pro všechny příkazy, nabídky a ovládací prvky  
  
-   klávesové zkratky pro důležité odkazy  
  
-   všechny položky nabídky mají přístupový klíč; klávesy akcelerátoru mít všechna tlačítka, všechny příkazy mít klávese akcelerátoru.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nenechte myši umístění narušovat navigační klávesnice  
 Umístění myši neměla mít vliv na navigační klávesnice. Pro příklad, pokud, myš není umístěný někde a uživatel je navigaci pomocí klávesnice, klikněte na tlačítko myši došlo k neočekávané chybě pokud iniciováno uživatelem.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Multimodální rozhraní  
 Osvědčené postupy v této části, zkontrolujte, že aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zahrnuje alternativami pro vizuální prvky.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Zadejte uživatel vybírat ekvivalenty pro elementy bez textu  
 Pro každý element jiný text zadejte uživatel vybírat ekvivalentní pro text, přepisy nebo zvuk popisy, například alternativní text, titulky nebo vizuální zpětnou vazbu.  
  
 Elementy bez textu zahrnují širokou škálu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy, včetně: bitové kopie, oblasti mapy obrázku, animací, aplety, rámců, skripty, grafické tlačítka, zvuky, samostatné zvukových souborů a video. Elementy bez textu jsou důležité, které obsahují vizuální informace, řeči nebo obecné zvuk informace, že uživatel potřebuje přístup k Chcete-li pochopit obsah [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Pomocí barev, ale také zadat alternativy barev  
 Použít barvu vylepšit, zdůraznil nebo znovu opakují informace zobrazené jiným způsobem, ale nekomunikují informace pomocí barev samostatně. Uživatelé, kteří jsou barva slepé nebo mají černobílý zobrazení potřebovat alternativy barev.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Standardní vstupní rozhraní API pomocí volání nezávislé na zařízení  
 Volání nezávislé na zařízení zkontrolujte rovnosti funkce klávesnici a myš, při současném poskytování [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] s potřebné informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.Peers>  
 [NumericUpDown vlastní ovládací prvek s motiv a ukázkové podpora automatizace uživatelského rozhraní](http://msdn.microsoft.com/en-us/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Pokyny pro návrh klávesnice uživatelského rozhraní](http://msdn2.microsoft.com/library/ms971323.aspx)
