---
title: Řešení potíží s hybridními aplikacemi
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187317"
---
# <a name="troubleshooting-hybrid-applications"></a>Řešení potíží s hybridními aplikacemi
<a name="introduction"></a>Toto téma uvádí některé běžné problémy, které mohou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastat při vytváření hybridních aplikací, které používají technologie windows forms.  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>Překrývající se ovládací prvky  
 Ovládací prvky se nemusí překrývat podle očekávání. Windows Forms používá samostatný HWND pro každý ovládací prvek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá jeden HWND pro veškerý obsah na stránce. Tento rozdíl implementace způsobuje neočekávané překrývající se chování.  
  
 Ovládací prvek Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostovaný v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci se vždy zobrazí nad obsahem.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsah hostovaný <xref:System.Windows.Forms.Integration.ElementHost> v ovládacím prvku se <xref:System.Windows.Forms.Integration.ElementHost> zobrazí v pořadí vykreslovat ovládacího prvku. Je možné překrývat <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky, ale hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah nekombinuje ani neinteraguje.  
  
<a name="child_property"></a>
## <a name="child-property"></a>Podřízená vlastnost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třídy <xref:System.Windows.Forms.Integration.ElementHost> a může hostit pouze jeden podřízený ovládací prvek nebo prvek. Chcete-li hostovat více než jeden ovládací prvek nebo prvek, musíte použít kontejner jako podřízený obsah. Můžete například přidat tlačítko Formuláře systému Windows <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> a ovládací prvky zaškrtávacích políček do ovládacího prvku a potom přiřadit panel k vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> prvku. Ovládací prvky tlačítka a zaškrtávacích <xref:System.Windows.Forms.Integration.WindowsFormsHost> políček však nelze přidat samostatně do stejného ovládacího prvku.  
  
<a name="scaling"></a>
## <a name="scaling"></a>Škálování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a Windows Forms mají různé modely škálování. Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] transformace škálování jsou smysluplné pro ovládací prvky Windows Forms, ale jiné nikoli. Například škálování ovládacího prvku Windows Forms na 0 bude fungovat, ale pokud se pokusíte změnit velikost stejného ovládacího prvku zpět na nenulovou hodnotu, velikost ovládacího prvku zůstane 0. Další informace naleznete v [tématu Aspekty rozložení elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>
## <a name="adapter"></a>Adaptér  
 Může být zmatek <xref:System.Windows.Forms.Integration.WindowsFormsHost> při <xref:System.Windows.Forms.Integration.ElementHost> práci a třídy, protože obsahují skrytý kontejner. A <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy <xref:System.Windows.Forms.Integration.ElementHost> mají skrytý kontejner, nazývaný *adaptér*, který používají k hostování obsahu. Pro <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek adaptér uvozová <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> z třídy. Pro <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek adaptér uvozová z <xref:System.Windows.Controls.DockPanel> prvku. Když se zobrazí odkazy na adaptér v jiných tématech spolupráce, tento kontejner je to, co je diskutováno.  
  
<a name="nesting"></a>
## <a name="nesting"></a>Vnoření  
 Vnoření <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku <xref:System.Windows.Forms.Integration.ElementHost> uvnitř ovládacího prvku není podporováno. Vnoření <xref:System.Windows.Forms.Integration.ElementHost> ovládacího <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku uvnitř prvku také není podporováno.  
  
<a name="focus"></a>
## <a name="focus"></a>Zaměření  
 Fokus funguje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odlišně v a Windows Forms, což znamená, že problémy fokus může dojít v hybridní aplikaci. Například pokud máte fokus <xref:System.Windows.Forms.Integration.WindowsFormsHost> uvnitř prvku a buď minimalizovat a obnovit stránku nebo <xref:System.Windows.Forms.Integration.WindowsFormsHost> zobrazit modální dialogové okno, fokus uvnitř prvku může dojít ke ztrátě. Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> má stále fokus, ale ovládací prvek uvnitř nemusí.  
  
 Ověřování dat je také ovlivněno fokusem. Ověření funguje <xref:System.Windows.Forms.Integration.WindowsFormsHost> v prvku, ale nefunguje jako kartu <xref:System.Windows.Forms.Integration.WindowsFormsHost> z prvku nebo <xref:System.Windows.Forms.Integration.WindowsFormsHost> mezi dvěma různými prvky.  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>Mapování vlastností  
 Některá mapování vlastností vyžadují rozsáhlou interpretaci k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] překlenutí odlišných implementací mezi technologiemi a technologiemi Windows Forms. Mapování vlastností umožňuje kódu reagovat na změny v písmech, barvách a dalších vlastnostech. Obecně platí, že mapování vlastností funguje nasloucháním pro události *Property*Changed nebo On*Property*Changed volání a nastavením vhodných vlastností na podřízeném ovládacím prvku nebo jeho adaptéru. Další informace naleznete v [tématu Windows Forms a WPF Property Mapping](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>Vlastnosti související s rozložením hostovaného obsahu  
 Při <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> přiřazení <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> vlastnosti nebo se automaticky nastaví několik vlastností souvisejících s rozložením v hostovaném obsahu. Změna těchto vlastností obsahu může způsobit neočekávané chování rozložení.  
  
 Hostovaný obsah je ukotven tak, aby vyplnil nadřazený <xref:System.Windows.Forms.Integration.WindowsFormsHost> obsah a. <xref:System.Windows.Forms.Integration.ElementHost> Chcete-li povolit toto chování výplně, několik vlastností jsou nastaveny při nastavení podřízené vlastnosti. V následující tabulce jsou uvedeny, <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> které vlastnosti obsahu jsou nastaveny třídami a.  
  
|Hostitelská třída|Vlastnosti obsahu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nenastavujte tyto vlastnosti přímo na hostovaném obsahu. Další informace naleznete v [tématu Aspekty rozložení elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>Navigační aplikace  
 Navigační aplikace nemusí udržovat stav uživatele. Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> znovu vytvoří své ovládací prvky při použití v navigační aplikaci. K opětovnému vytvoření podřízených ovládacích prvků dochází, když uživatel přejde od stránky hostující <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek a potom se k němu vrátí. Veškerý obsah, který uživatel zadal, bude ztracen.  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>Spolupráce smyčky zpráv  
 Při práci s windows forms smyčky zpráv zprávy nemusí být zpracovány podle očekávání. Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> je volána <xref:System.Windows.Forms.Integration.WindowsFormsHost> konstruktorem. Tato metoda přidá filtr [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpráv do smyčky zpráv. Tento filtr <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> volá metodu, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> pokud a byl cíl zprávy a překládá/odešle zprávu.  
  
 Pokud zobrazíte <xref:System.Windows.Window> ve smyčce zpráv <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>windows forms s , <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> nelze zadat nic, pokud voláte metodu. Metoda <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> trvá <xref:System.Windows.Window> a přidá <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, který přesměruje zprávy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] související s klíčem do smyčky zpráv. Další informace naleznete v [tématech Windows Forms a WPF Interoperability Input Architecture](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>Krytí a vrstvení  
 Třída <xref:System.Windows.Interop.HwndHost> nepodporuje vrstvení. To znamená, <xref:System.Windows.UIElement.Opacity%2A> že nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> vlastnosti prvku nemá žádný vliv a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] žádné <xref:System.Windows.Window.AllowsTransparency%2A> prolnutí nedojde s jinými okny, které mají nastavena na `true`.  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 Není správně disposing třídy může únik unikající prostředky. V hybridních aplikacích se <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> ujistěte, že a třídy jsou uvolněny, nebo může dojít k úniku prostředků. Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> vyloží ovládací <xref:System.Windows.Forms.Form> prvky při ukončení jeho nemodální nadřazené položky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]odstraňuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky při vypnutí aplikace. Je možné zobrazit <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek ve <xref:System.Windows.Window> smyčce zpráv Windows Forms. V takovém případě nemusí váš kód přijímat oznámení, že se aplikace vypíná.  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>Povolení vizuálních stylů  
 Vizuální styly systému Microsoft Windows XP v ovládacím prvku Windows Forms pravděpodobně nejsou povoleny. Metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> je volána v šabloně pro aplikaci Windows Forms. I když tato metoda není volána ve výchozím nastavení, pokud používáte Visual Studio k vytvoření projektu, získáte Microsoft Windows XP vizuální styly pro ovládací prvky, pokud verze 6.0 comctl32.dll je k dispozici. Je nutné <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> volat metodu před popisovače jsou vytvořeny ve vlákně. Další informace naleznete v [tématu How to: Enable Visual Styles in a Hybrid Application](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>Licencované ovládací prvky  
 Licencované ovládací prvky systému Windows Forms, které uživateli zobrazují informace o licencích v poli se zprávou, mohou způsobit neočekávané chování hybridní aplikace. Některé licencované ovládací prvky zobrazují dialogové okno v reakci na vytvoření popisovače. Licencovaný ovládací prvek může například informovat uživatele, že je vyžadována licence nebo že uživatel má tři zbývající zkušební použití ovládacího prvku.  
  
 Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je odvozen <xref:System.Windows.Interop.HwndHost> od třídy a popisovač podřízeného <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> ovládacího prvku je vytvořen uvnitř metody. Třída <xref:System.Windows.Interop.HwndHost> neumožňuje zprávy, které mají <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> být zpracovány v metodě, ale zobrazení dialogového okna způsobí, že zprávy, které mají být odeslány. Chcete-li povolit tento <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> scénář licencování, volání metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> na ovládací prvek před přiřazením jako podřízený prvek.  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>návrhář WPF  
 Obsah WPF můžete navrhnout pomocí WPF Designer pro Visual Studio. V následujících částech jsou uvedeny některé běžné problémy, které mohou nastat při vytváření hybridních aplikací pomocí návrháře WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent je ignorována v době návrhu  
 Vlastnost <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> nemusí fungovat podle očekávání v době návrhu.  
  
 Pokud ovládací prvek WPF není na viditelné nadřazené, wpf runtime ignoruje hodnotu. <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Důvod, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> který může být <xref:System.Windows.Forms.Integration.ElementHost> ignorován, je proto, že objekt je vytvořen v samostatném <xref:System.AppDomain>. Však při spuštění aplikace, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funguje podle očekávání.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Při odstranění složky obj se zobrazí seznam chyb v době návrhu  
 Pokud je složka obj odstraněna, zobrazí se seznam chyb v době návrhu.  
  
 Při návrhu <xref:System.Windows.Forms.Integration.ElementHost>pomocí aplikace Používá Návrhář formulářů systému Windows generované soubory ve složce Ladění nebo Vydání ve složce obj projektu. Pokud tyto soubory odstraníte, zobrazí se seznam chyb v době návrhu. Chcete-li tento problém vyřešit, znovu vytvořte projekt. Další informace naleznete [v tématu Chyby návrhu v Návrháři formulářů systému Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost a IME  
 WPF ovládací prvky <xref:System.Windows.Forms.Integration.ElementHost> hostované v <xref:System.Windows.Forms.Control.ImeMode%2A> aktuálně nepodporují vlastnost. Změny <xref:System.Windows.Forms.Control.ImeMode%2A> budou hostovanými ovládacími prvky ignorovány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperabilita v návrháři WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architektura vstupu interoperability Windows Forms a WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Postupy: Povolení vizuálních stylů v hybridní aplikaci](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Předpoklady rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Chyby při návrhu v Návrháři formulářů Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migrace a interoperabilita](migration-and-interoperability.md)
