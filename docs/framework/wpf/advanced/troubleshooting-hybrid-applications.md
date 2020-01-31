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
ms.openlocfilehash: 7af110b9b00b080bf40bc9ee4b85aa293940bbc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794265"
---
# <a name="troubleshooting-hybrid-applications"></a>Řešení potíží s hybridními aplikacemi
<a name="introduction"></a>Toto téma uvádí některé běžné problémy, ke kterým může dojít při vytváření hybridních aplikací, které používají technologie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i model Windows Forms.  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Překrývající se ovládací prvky  
 Ovládací prvky se nesmí překrývat, jak byste očekávali. Model Windows Forms používá samostatný HWND pro každý ovládací prvek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá pro veškerý obsah na stránce jeden HWND. Tento rozdíl implementace způsobuje neočekávané překrývající se chování.  
  
 Model Windows Forms ovládací prvek hostovaný v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se vždy zobrazuje nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah hostovaný v ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> se zobrazí v pořadí vykreslování ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>. Je možné překrývat <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky, ale hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah nespojuje ani nekomunikuje.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Podřízená vlastnost  
 Třídy <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> mohou hostovat pouze jeden podřízený ovládací prvek nebo prvek. Chcete-li hostovat více než jeden ovládací prvek nebo prvek, musíte jako podřízený obsah použít kontejner. Můžete například přidat model Windows Forms tlačítko a ovládací prvky zaškrtávací políčko ovládacímu prvku <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> a pak přiřadit panel k <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> vlastnosti ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ovládací prvky tlačítko a zaškrtávací políčko však nelze přidat odděleně ke stejnému ovládacímu prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Škálování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms mají různé modely škálování. Některé transformace škálování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou smysluplné pro model Windows Forms ovládací prvky, ale jiné ne. Například škálování ovládacího prvku model Windows Forms na 0 bude fungovat, ale pokud se pokusíte škálovat stejný ovládací prvek zpět na nenulovou hodnotu, zůstane velikost ovládacího prvku 0. Další informace najdete v tématu [požadavky na rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adaptér  
 Při práci s třídami <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> může dojít k nejasnostem, protože obsahují skrytý kontejner. Třídy <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> mají skrytý kontejner nazvaný *adaptér*, který používá k hostování obsahu. Pro prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je adaptér odvozen z třídy <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>. Pro ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> je adaptér odvozen od <xref:System.Windows.Controls.DockPanel> elementu. Když vidíte odkazy na adaptér v jiných tématech vzájemná spolupráce, tento kontejner je právě diskutován.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Vnoření  
 Vnořování prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> uvnitř ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> není podporováno. Vnoření ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost> uvnitř elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> není také podporováno.  
  
<a name="focus"></a>   
## <a name="focus"></a>Vybrána  
 Fokus funguje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms odlišně, což znamená, že se v hybridní aplikaci můžou objevit problémy s fokusem. Například pokud máte fokus v rámci prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> a buď minimalizujete a obnovíte stránku nebo zobrazíte modální dialogové okno, je možné, že se fokus uvnitř elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ztratí. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> má stále fokus, ale ovládací prvek uvnitř něj není.  
  
 Ověřování dat je také ovlivněno fokusem. Ověřování funguje v prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost>, ale nefunguje jako karta z <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu nebo mezi dvěma různými <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapování vlastností  
 Některá mapování vlastností vyžadují rozsáhlé vyhodnocení pro přemostění nepodobných implementací mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms technologiemi. Mapování vlastností umožňuje vašemu kódu reagovat na změny písem, barev a dalších vlastností. Obecně platí, že mapování vlastností funguje tak, že naslouchá buď událostem změněné *vlastnosti*, nebo voláním změněných*vlastností*a nastavují příslušné vlastnosti buď podřízenému ovládacímu prvku, nebo jeho adaptéru. Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Vlastnosti související s rozložením u hostovaného obsahu  
 Když je přiřazena vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>, jsou automaticky nastaveny některé vlastnosti v hostovaném obsahu, které se týkají rozložení. Změna těchto vlastností obsahu může způsobit neočekávané chování rozložení.  
  
 Hostovaný obsah je ukotven, aby bylo možné vyplnit <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> nadřazený objekt. Pokud chcete povolit toto chování při plnění, nastaví se při nastavování podřízené vlastnosti několik vlastností. Následující tabulka uvádí, které vlastnosti obsahu jsou nastaveny pomocí tříd <xref:System.Windows.Forms.Integration.ElementHost> a <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
|Třída Host|Vlastnosti obsahu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Tyto vlastnosti nenastavujte přímo na hostovaný obsah. Další informace najdete v tématu [požadavky na rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Navigační aplikace  
 Navigační aplikace pravděpodobně neudržují stav uživatele. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> znovu vytvoří své ovládací prvky, pokud se používá v navigační aplikaci. Opětovné vytvoření podřízených ovládacích prvků nastane, když uživatel přejde pryč ze stránky, která je hostitelem prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> a pak se vrátí do něj. Veškerý obsah, který byl zadán uživatelem, bude ztracen.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Prochod smyčky zpráv  
 Pokud pracujete se smyčkami zpráv model Windows Forms, zprávy nemusejí být zpracovány podle očekávání. Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> je volána konstruktorem <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Tato metoda přidá filtr zpráv do smyčky zpráv [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tento filtr volá metodu <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>, pokud byl <xref:System.Windows.Forms.Control?displayProperty=nameWithType> cílem zprávy a překládá/odesílá zprávu.  
  
 Pokud zobrazíte <xref:System.Windows.Window> ve smyčce model Windows Forms zpráv <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nemůžete zadat cokoli, dokud nebudete volat metodu <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>. Metoda <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> přebírá <xref:System.Windows.Window> a přidává <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, který přesměruje zprávy týkající se klíčů na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] smyčku zpráv. Další informace najdete v tématu [Architektura vstupu interoperability model Windows Forms a WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Neprůhlednost a vrstvení  
 Třída <xref:System.Windows.Interop.HwndHost> nepodporuje vrstvení. To znamená, že nastavení vlastnosti <xref:System.Windows.UIElement.Opacity%2A> u elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> nemá žádný účinek a žádné prolnutí nebude provedeno v ostatních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oknech, které mají <xref:System.Windows.Window.AllowsTransparency%2A> nastavené na `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Zrušen  
 Třídy neumožňující správné prostředky způsobit nevracení prostředků. V hybridních aplikacích se ujistěte, že <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy jsou vyřazené nebo že byste mohli zrušit jeho prostředky. Model Windows Forms odřadí <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky při zavření jejího nemodálního <xref:System.Windows.Forms.Form> nadřazeného prvku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odstraní <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky, když se vaše aplikace ukončí. Je možné zobrazit <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek v <xref:System.Windows.Window> ve smyčce zprávy model Windows Forms. V takovém případě váš kód nemusí dostávat oznámení o ukončení aplikace.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Povolení vizuálních stylů  
 Vizuální styly systému Microsoft Windows XP v ovládacím prvku model Windows Forms nemusí být povoleny. Metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> je volána v šabloně model Windows Forms aplikace. I když tato metoda není volána ve výchozím nastavení, pokud použijete sadu Visual Studio k vytvoření projektu, získáte vizuální styly Microsoft Windows XP pro ovládací prvky, pokud je k dispozici verze 6,0 souboru Comctl32. dll. Před vytvořením popisovačů ve vlákně je třeba zavolat metodu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Další informace najdete v tématu [Postup: Povolení vizuálních stylů v hybridní aplikaci](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencované ovládací prvky  
 Licencované model Windows Forms ovládací prvky, které zobrazují informace o licencích v okně se zprávou pro uživatele, můžou způsobit neočekávané chování hybridní aplikace. Některé licencované ovládací prvky zobrazí dialogové okno v reakci na vytvoření popisovače. Licencovaný ovládací prvek může například informovat uživatele o tom, že je požadována licence nebo zda má uživatel tři zbývající zkušební využití tohoto ovládacího prvku.  
  
 Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je odvozen z třídy <xref:System.Windows.Interop.HwndHost> a popisovač podřízeného ovládacího prvku je vytvořen v rámci metody <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>. Třída <xref:System.Windows.Interop.HwndHost> nepovoluje zpracování zpráv v metodě <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>, ale zobrazení dialogového okna způsobí odeslání zpráv. Chcete-li povolit tento scénář licencování, zavolejte metodu <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> ovládacího prvku před přiřazením jako podřízenou položku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>návrhář WPF  
 Obsah WPF můžete navrhnout pomocí Návrháře WPF pro Visual Studio. V následujících částech jsou uvedeny některé běžné problémy, které mohou nastat při vytváření hybridních aplikací pomocí Návrháře WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent se v době návrhu ignoruje.  
 Vlastnost <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> nemusí v době návrhu fungovat podle očekávání.  
  
 Pokud ovládací prvek WPF není na viditelném nadřazeném prvku, modul runtime WPF ignoruje hodnotu <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>. Důvodem, proč <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> může být ignorováno, je, že objekt <xref:System.Windows.Forms.Integration.ElementHost> je vytvořen v samostatném <xref:System.AppDomain>. Při spuštění aplikace ale <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> fungovat podle očekávání.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Při odstranění složky obj se zobrazí Seznam chyb v době návrhu.  
 Pokud je odstraněna složka obj, Seznam chyb zobrazí se čas návrhu.  
  
 Při návrhu pomocí <xref:System.Windows.Forms.Integration.ElementHost>Návrhář formulářů používá generované soubory ve složce pro ladění nebo vydání ve složce obj projektu. Při odstranění těchto souborů se zobrazí Seznam chyb čas návrhu. Chcete-li tento problém vyřešit, znovu sestavte projekt. Další informace najdete v tématu [chyby při návrhu v Návrhář formulářů](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost a IME  
 Ovládací prvky WPF hostované v <xref:System.Windows.Forms.Integration.ElementHost> aktuálně nepodporují vlastnost <xref:System.Windows.Forms.Control.ImeMode%2A>. Změny <xref:System.Windows.Forms.Control.ImeMode%2A> budou v hostovaných ovládacích prvcích ignorovány.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperabilita v Návrháři WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architektura vstupu interoperability Windows Forms a WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Postupy: Povolení vizuálních stylů v hybridní aplikaci](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Předpoklady rozložení pro element WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Chyby v rámci doby návrhu v Návrháři formulářů](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migrace a interoperabilita](migration-and-interoperability.md)
