---
title: "Řešení potíží s hybridními aplikacemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0fed9a491c91881a9e0296e2c849d8430bb954
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-hybrid-applications"></a>Řešení potíží s hybridními aplikacemi
<a name="introduction"></a>Toto téma uvádí některé běžné problémy, ke kterým dochází při vytváření hybridní aplikace, které používají obě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologie.  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Překrývající se ovládací prvky  
 Ovládací prvky nesmí překrývat, jako byste očekávali. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]používá samostatné HWND pro každý ovládací prvek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]použije jeden HWND pro veškerý obsah na stránce. Tento rozdíl implementace způsobí, že neočekávané chování překrývající se.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení hostované v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vždy se zobrazí na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsah hostované v <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek se zobrazuje v pořadí vykreslování z <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. Je možné překrývat <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky, ale hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah kombinovat nebo interakci.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Podřízená – vlastnost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy můžou hostovat pouze jeden podřízený ovládací prvek nebo elementu. K hostování více než jeden ovládací prvek nebo prvek, je nutné použít kontejner jako podřízené obsah. Například můžete přidat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky pro tlačítko a zaškrtněte políčko <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> řízení a pak mu přiřaďte na panelu <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> vlastnost. Však nelze přidat ovládací prvky tlačítko a zaškrtněte políčko samostatně na stejnou <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Změna měřítka  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mají různé modely škálování. Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] škálování transformace dávat smysl [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, ale jiné nejsou. Například škálování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku na hodnotu 0, budou fungovat, ale pokud se pokusíte škálování stejný ovládací prvek zpět na hodnotu nula, velikost ovládacího prvku zůstává 0. Další informace najdete v tématu [aspekty rozložení pro WindowsFormsHost Element](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adaptér  
 Je možné, nejasnosti při práci <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy, protože obsahují kontejner skrytá. Jak <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy mají skrytá kontejneru, názvem *adaptér*, které používají jako hostitele obsahu. Pro <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu je odvozena z adaptéru <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> třídy. Pro <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek, je odvozena z adaptéru <xref:System.Windows.Controls.DockPanel> elementu. Až uvidíte odkazy na adaptéru v dalších tématech součinnosti, je tento kontejner, co popsané.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Vnoření  
 Vnoření <xref:System.Windows.Forms.Integration.WindowsFormsHost> element uvnitř <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek není podporován. Vnoření <xref:System.Windows.Forms.Integration.ElementHost> řízení uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> také nepodporuje element.  
  
<a name="focus"></a>   
## <a name="focus"></a>Fokus  
 Fokus funguje jinak v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], což znamená, že zaměřit problémy může dojít v hybridní aplikace. Například, pokud máte fokus uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a je buď minimalizovat a obnovit stránku nebo zobrazí modální dialogové okno, zaměřit uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> element mohou být ztracena. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Stále má právě fokus, elementu, ale ovládací prvek v rámci ho může není.  
  
 Ověřování dat má vliv také fokus. Ověření funguje v <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, ale nefunguje, protože kartě mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, nebo mezi dvěma různými <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapování vlastností  
 Některé mapování vlastností vyžadovat rozsáhlé interpretaci přemostění odlišné implementace mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologie. Mapování vlastností Povolit kód a reagovat na změny v písma, barvy a další vlastnosti. Obecně platí, mapování vlastností fungovat prostřednictvím naslouchání pro buď *vlastnost*změnit události nebo na*vlastnost*změnit volání a odpovídající vlastnosti nastavení na podřízený ovládací prvek nebo jeho adaptér. Další informace najdete v tématu [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Vlastnosti související s rozložením hostované obsahu  
 Když <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> vlastnost je přiřazen, jsou automaticky nastavit několik vlastností souvisejících s rozložením hostované obsahu. Změna těchto vlastností obsahu může způsobit neočekávané rozložení chování.  
  
 Hostované obsah je ukotven k vyplnění <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> nadřazené. Chcete-li toto chování výplň, několik vlastností, které se nastavují při nastavení vlastnosti podřízené. Následující tabulka uvádí, které lze nastavit vlastnosti obsahu pomocí <xref:System.Windows.Forms.Integration.ElementHost> a <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy.  
  
|Třída hostitele|Vlastnosti obsahu|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nenastavujte tyto vlastnosti přímo na hostované obsah. Další informace najdete v tématu [aspekty rozložení pro WindowsFormsHost Element](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Navigace aplikace  
 Navigace aplikace nemusí udržovat stav uživatele. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element vytvoří jeho ovládacích prvků při použití v aplikaci navigace. Vytvořením podřízené ovládací prvky nastane, když uživatel přejde mimo stránku hostování <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a pak vrátí do ní. Veškerý obsah, který má zadané v uživatelem se ztratí.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Vzájemná spolupráce zpráva smyčky  
 Při práci s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] smyčky zpráv, zpráv nemusí být zpracovány podle očekávání. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Metoda je volána <xref:System.Windows.Forms.Integration.WindowsFormsHost> konstruktor. Tato metoda přidá filtr zpráv pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpráva smyčky. Tento filtr volá <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metoda Pokud <xref:System.Windows.Forms.Control?displayProperty=nameWithType> byl cíl zprávy a překládá nebo odešle zprávu.  
  
 Pokud můžete zobrazit <xref:System.Windows.Window> v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpráva smyčky pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nic nelze zadat, pokud zavoláte <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metoda. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Metoda trvá <xref:System.Windows.Window> a přidá <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, který bude přesměrována klíč související zprávy a pokuste se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpráva smyčky. Další informace najdete v tématu [architektura vstup interoperabilita WPF a Windows Forms](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Krytí a vrstvení  
 <xref:System.Windows.Interop.HwndHost> Třída nepodporuje rozvrstvení. To znamená, že nastavení <xref:System.Windows.UIElement.Opacity%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> element nemá žádný vliv, a žádné prolnutí dojde s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] windows, které mají <xref:System.Windows.Window.AllowsTransparency%2A> nastavena na `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Uvolnění.  
 Není správně uvolnění třídy může se nevrací prostředky. V hybridní aplikace, ujistěte se, že <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost> třídy jsou zapomenuty a může se nevrací prostředky. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]uvolní <xref:System.Windows.Forms.Integration.ElementHost> určí, kdy se jeho nemodálním <xref:System.Windows.Forms.Form> nadřazených zavře. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uvolní <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvků při ukončení aplikace. Je možné zobrazit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element v <xref:System.Windows.Window> v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpráva smyčky. V takovém případě kódu dostávat oznámení, že se aplikace vypíná.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Povolení vizuální styly  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]Visual styly na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení možná není zapnuté. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Metoda je volána v šabloně pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace. I když tato metoda není volána ve výchozím nastavení, pokud používáte [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] k vytvoření projektu, zobrazí se [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styly pro ovládací prvky, pokud je k dispozici verze 6.0 Comctl32.dll. Je třeba zavolat <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda před vytvořením obslužné rutiny na vlákno. Další informace najdete v tématu [postupy: povolení vizuální styly v hybridní aplikace](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencované ovládací prvky  
 Licenci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které zobrazují informace o licencích v okně se zprávou uživateli může způsobit neočekávané chování pro hybridní aplikace. Některé licencované ovládací prvky zobrazení dialogového okna v reakci na zpracování vytvoření. Licencované ovládací prvek například může informovat uživatele, že je vyžadována licence, nebo že uživatel má tři zbývající zkušební používá ovládacího prvku.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Je odvozen z elementu <xref:System.Windows.Interop.HwndHost> třídy a podřízený ovládací prvek popisovač je vytvořit uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metoda. <xref:System.Windows.Interop.HwndHost> Třída neumožňuje zpráv, které mají být zpracovány v <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metoda, ale zobrazení dialogového okna způsobí, že odesílání zpráv. Chcete-li povolit tento scénář licencování, zavolejte <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metoda na ovládací prvek před přiřazením jej jako <xref:System.Windows.Forms.Integration.WindowsFormsHost> podřízené elementu.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>návrhář WPF  
 Obsah WPF můžete navrhnout pomocí [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. Následující části uvádějí některé běžné problémy, ke kterým dochází při vytváření hybridní aplikace pomocí [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent je ignorován v době návrhu  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Vlastnost nemusí fungovat podle očekávání v době návrhu.  
  
 Pokud ovládací prvek WPF není u nadřazené viditelné, ignoruje runtime grafického subsystému WPF <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> hodnotu. Z důvodu, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> může být ignorována totiž <xref:System.Windows.Forms.Integration.ElementHost> objekt se vytvoří v samostatném <xref:System.AppDomain>. Však při spuštění aplikace, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funguje podle očekávání.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Seznam chyb návrhu se zobrazí, když je odstraněn složce obj.  
 Pokud se odstraní složku obj, zobrazí se v seznamu chyb návrhu.  
  
 Při návrhu pomocí <xref:System.Windows.Forms.Integration.ElementHost>, Návrhář formulářů Windows používá generované soubory ve složce ladění nebo verze ve složce obj. vašeho projektu. Pokud odstraníte tyto soubory, zobrazí se v seznamu chyb návrhu. Chcete-li tento problém vyřešit, znovu sestavte projekt. Další informace najdete v tématu [chyby při návrhu v Návrháři formulářů](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>Elementhost – a editoru IME  
 Hostitelem ovládacích prvků WPF <xref:System.Windows.Forms.Integration.ElementHost> aktuálně nepodporují <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost. Změny <xref:System.Windows.Forms.Control.ImeMode%2A> ovládacími prvky hostované budou ignorovány.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Interoperabilita v Návrháře WPF](http://msdn.microsoft.com/en-us/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Architektura vstupu interoperability Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Postupy: Povolení vizuálních stylů v hybridní aplikaci](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [Předpoklady rozložení pro element WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Chyby v rámci doby návrhu v Návrháři formulářů](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
