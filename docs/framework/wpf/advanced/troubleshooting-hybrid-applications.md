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
ms.openlocfilehash: b43143fb3f27d127f93f5e8edd55b853ad604ef5
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277676"
---
# <a name="troubleshooting-hybrid-applications"></a>Řešení potíží s hybridními aplikacemi
<a name="introduction"></a> Toto téma uvádí některé běžné problémy, které se mohou vyskytnout při vytváření hybridních aplikací, které obě používají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologie.  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Překrývání ovládacích prvků  
 Ovládací prvky se nemohou překrývat dle očekávání. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] používá samostatné HWND pro každý ovládací prvek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá jednu HWND pro veškerý obsah na stránce. Tento rozdíl implementace způsobí, že překrývající se neočekávané chování.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek hostované v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vždy se zobrazí v horní části [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah hostovaný v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku se zobrazí v pořadí vykreslování z <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. Je možné překrývat <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků, ale hostovanou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah kombinovat nebo pracovat.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Podřízená vlastnost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy může hostovat pouze jeden podřízený ovládací prvek nebo element. K hostování více než jeden ovládací prvek nebo prvek, je nutné použít kontejner jako podřízený obsah. Například můžete přidat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků pro tlačítka a zaškrtávací políčko <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> ovládací prvek a pak přiřaďte panelu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> vlastnost. Však nelze přidat ovládací prvky tlačítka a zaškrtávací políčko samostatně na stejný <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Škálování  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mají různé velikosti modelů. Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] změnu velikosti mají smysl v daném [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků, ale ostatní nejsou. Například, škálování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku na hodnotu 0, bude fungovat, ale pokud se pokusíte škálování stejný ovládací prvek zpět na nenulovou hodnotu, velikost ovládacího prvku zůstává 0. Další informace najdete v tématu [důležité informace o rozložení pro WindowsFormsHost Element](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adaptér  
 Můžou existovat nejasnosti při práci <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy, protože obsahuje skryté kontejneru. Jak <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy mají skryté kontejneru a názvem *adaptér*, které používají k hostování obsahu. Pro <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je odvozen od adaptéru <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> třídy. Pro <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku, je odvozena z adaptéru <xref:System.Windows.Controls.DockPanel> elementu. Až uvidíte odkazy na adaptér v dalších témat, která vzájemné spolupráce, je tento kontejner, co je právě probírali.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Vnoření  
 Vnoření <xref:System.Windows.Forms.Integration.WindowsFormsHost> element v rámci <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek není podporován. Vnoření <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> také element není podporován.  
  
<a name="focus"></a>   
## <a name="focus"></a>fokus  
 Fokus funguje jinak v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], což znamená, že zaměřit problémy mohou nastat v hybridní aplikaci. Například, pokud budete mít fokus uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a je buď minimalizace a obnovení na stránce nebo zobrazí modální dialogové okno, zaměřte uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> element může dojít ke ztrátě. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element stále má fokus, ale ovládací prvek uvnitř nemusí.  
  
 Ověřování dat je také ovlivněny fokus. Ověření funguje v <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, ale nefunguje podle kartu z celkového počtu <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, nebo mezi dvěma různými <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapování vlastností  
 Některé mapování vlastností vyžadují rozsáhlé výkladu pro přemostění rozdílné implementace mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologie. Mapování vlastností povolit kódu reagovat na změny písma, barvy a dalších vlastností. Obecně platí, mapování vlastností fungují tak, že buď poslouchání *vlastnost*změnit události nebo na*vlastnost*změnit volání a příslušné vlastnosti nastavení na podřízený ovládací prvek nebo jeho adaptér. Další informace najdete v tématu [Windows Forms a WPF vlastnost mapování](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Vlastnosti související s rozložením na hostovaný obsah  
 Když <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> je vlastnosti přiřazen, několik vlastností hostovaný obsah související s rozložením se nastaví automaticky. Změna tyto vlastnosti obsahu může způsobit neočekávané rozložení chování.  
  
 Hostovaný obsah je ukotven k vyplnění <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> nadřazené. Pokud chcete povolit toto chování výplň, několik vlastností nastavené, když nastavíte vlastnost podřízeného. Následující tabulka uvádí, které jsou nastaveny vlastnosti obsahu pomocí <xref:System.Windows.Forms.Integration.ElementHost> a <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy.  
  
|Třída hostitele|Vlastnosti obsahu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nenastavujte tyto vlastnosti přímo na hostovaný obsah. Další informace najdete v tématu [důležité informace o rozložení pro WindowsFormsHost Element](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Navigační aplikace  
 Navigační aplikace nemusí udržovat stav uživatele. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek znovu vytvoří jeho ovládacích prvků při použití v aplikaci navigace. Opětovné vytvoření podřízených ovládacích prvků nastane, když uživatel na stránce hostování <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek a vrátí na něj. Veškerý obsah, který má zadané v uživatelem se ztratí.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Vzájemná spolupráce grafického subsystému zpráva smyčky  
 Při práci s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] smyčky zpráv, zpráv nemusí být zpracován podle očekávání. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Metoda je volána <xref:System.Windows.Forms.Integration.WindowsFormsHost> konstruktoru. Tato metoda přidá filtru zprávy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] smyčku zpráv. Volá tento filtr <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metoda Pokud <xref:System.Windows.Forms.Control?displayProperty=nameWithType> byla cílem zprávy a překládá/odešle zprávu.  
  
 Pokud zobrazíte <xref:System.Windows.Window> v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] smyčky zpráv s <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nic nelze zadat, pokud zavoláte <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metoda. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Přijímá metodu <xref:System.Windows.Window> a přidá <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, který přesměrovává klíč související zprávy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] smyčky zpráv. Další informace najdete v tématu [Windows Forms a WPF architektura vstupu Interoperability](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Krytí a vrstvení  
 <xref:System.Windows.Interop.HwndHost> Třída nepodporuje vrstvení. To znamená, že toto nastavení <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> element nemá žádný vliv a žádné prolnutí dojde s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému windows, které mají <xref:System.Windows.Window.AllowsTransparency%2A> nastavena na `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Metody Dispose  
 Není správně uvolnění třídy může způsobit únik těchto prostředků. V hybridních aplikacích, ujistěte se, že <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy jsou odstraněny, nebo by mohly způsobit únik těchto prostředků. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uvolní <xref:System.Windows.Forms.Integration.ElementHost> určovat, kdy jeho nemodálním <xref:System.Windows.Forms.Form> nadřazené zavře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvolní <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky při ukončení aplikace. Je možné zobrazit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element v <xref:System.Windows.Window> v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] smyčku zpráv. V takovém případě váš kód nemusí dostat oznámení, že se aplikace vypíná.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Povolení vizuálních stylů  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] styly vizuálu na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek není povolený. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Metoda je volána v šabloně [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace. I když tato metoda není volána ve výchozím nastavení, pokud používáte [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] vytvořit projekt, zobrazí se [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styly pro ovládací prvky, pokud je k dispozici verzi knihovny Comctl32.dll 6.0. Je třeba zavolat <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda před vytvořením popisovačů u vlákna. Další informace najdete v tématu [postupy: povolení vizuálních stylů v hybridní aplikaci](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencované ovládací prvky  
 Licenci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které zobrazují informace o licencích v okně se zprávou pro uživatele může způsobit neočekávané chování pro hybridní aplikace. Některé licencované ovládací prvky zobrazí dialogové okno v reakci na zpracování vytváření. Licencovaný ovládací prvek může být například informovat uživatele, že je třeba zadat licenci nebo jestli má uživatel tři zbývající zkušební použití ovládacího prvku.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je odvozen od <xref:System.Windows.Interop.HwndHost> třídy a popisovač podřízený ovládací prvek je vytvořen uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metoda. <xref:System.Windows.Interop.HwndHost> Třídy nepovoluje zprávy mají být zpracovány v <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metody, ale zobrazení dialogového okna způsobí, že zprávy k odeslání. Chcete-li povolit tento scénář licencování, zavolejte <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metodu na ovládací prvek před přiřazením jako <xref:System.Windows.Forms.Integration.WindowsFormsHost> podřízeného elementu.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>návrhář WPF  
 Obsah WPF můžete navrhnout pomocí [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. V následujících oddílech jsou uvedeny některé běžné problémy, které se mohou vyskytnout při vytváření hybridních aplikací v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent ignorován v době návrhu  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Vlastnost nemusí fungovat podle očekávání v době návrhu.  
  
 Pokud ovládací prvek WPF není u nadřazené položky viditelné, WPF runtime Ignorovat <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> hodnotu. Z důvodu, který <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> může ignorovat totiž <xref:System.Windows.Forms.Integration.ElementHost> objekt je vytvořen v samostatném <xref:System.AppDomain>. Ale při spuštění aplikace, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funguje podle očekávání.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Když se odstraní složka obj, zobrazí se seznam chyb v době návrhu  
 Pokud se odstraní složka obj, zobrazí se seznam chyb návrhu.  
  
 Při návrhu pomocí <xref:System.Windows.Forms.Integration.ElementHost>, Návrhář formulářů Windows používá generované soubory ve složce ladění nebo vydání v rámci složku obj váš projekt. Pokud odstraníte tyto soubory se zobrazí v seznamu chyb návrhu. Chcete-li tento problém vyřešit, znovu sestavte projekt. Další informace najdete v tématu [chyby doby návrhu v Návrháři formulářů Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>Elementhost – a editoru IME  
 Ovládací prvky WPF hostované v <xref:System.Windows.Forms.Integration.ElementHost> aktuálně nepodporují <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost. Změny <xref:System.Windows.Forms.Control.ImeMode%2A> hostované ovládací prvky se bude ignorovat.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Vzájemná funkční spolupráce v návrháři pro WPF](https://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Architektura vstupu interoperability Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Postupy: Povolení vizuálních stylů v hybridní aplikaci](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [Předpoklady rozložení pro element WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Chyby v rámci doby návrhu v Návrháři formulářů](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
