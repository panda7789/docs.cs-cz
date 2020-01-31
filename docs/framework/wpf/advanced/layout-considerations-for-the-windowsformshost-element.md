---
title: Předpoklady rozložení pro element WindowsFormsHost
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 9f97639447284b792d52cf4aa25b81f584d7291a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787906"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Předpoklady rozložení pro element WindowsFormsHost
Toto téma popisuje, jak <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek komunikuje se systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms podporují různé, ale podobné logiky pro určení velikosti a umístění prvků na formuláři nebo na stránce. Při vytváření hybridního uživatelského rozhraní (UI), které je hostitelem model Windows Forms ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> integruje dvě schémata rozložení.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Rozdíly v rozložení mezi WPF a model Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá rozložení nezávislé na rozlišení. Všechny rozměry [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení se zadává v *pixelech nezávislých na zařízení*. Pixel nezávislý na zařízení je o jednu devadesátou velikost palce a nezávisle na rozlišení, takže získáte podobné výsledky bez ohledu na to, jestli vykreslujete na monitor 72-dpi nebo na tiskárnu 19 200-dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je také založen na *dynamickém rozložení*. To znamená, že se prvek uživatelského rozhraní uspořádá sám na formuláři nebo na stránce podle jeho obsahu, nadřazeného kontejneru rozložení a dostupné velikosti obrazovky. Dynamické rozložení usnadňuje lokalizaci tím, že automaticky upraví velikost a polohu prvků uživatelského rozhraní, když řetězce obsahují změnu délky.  
  
 Rozložení v model Windows Forms je závislé na zařízení a pravděpodobně je statické. Obvykle jsou ovládací prvky model Windows Forms umístěny absolutně na formuláři pomocí dimenzí zadaných v pixelech hardwaru. Model Windows Forms však podporuje některé funkce dynamického rozložení, které jsou shrnuty v následující tabulce.  
  
|Funkce rozložení|Popis|  
|--------------------|-----------------|  
|Automatické přizpůsobení velikosti|Některé model Windows Forms řídí změnu velikosti sebe sama tak, aby se jejich obsah správně zobrazoval. Další informace naleznete v tématu [Přehled vlastností AutoSize](../../winforms/controls/autosize-property-overview.md).|  
|Ukotvení a ukotvení|Model Windows Forms ovládací prvky podporují umístění a velikost na základě nadřazeného kontejneru. Další informace naleznete v tématu <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Automatické škálování|Ovládací prvky kontejneru mění velikost sebe sama a jejich podřízené položky na základě rozlišení výstupního zařízení nebo velikosti (v pixelech) výchozího písma kontejneru. Další informace najdete v tématu [Automatické škálování v model Windows Forms](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Kontejnery rozložení|Ovládací prvky <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel> uspořádají své podřízené ovládací prvky a velikost samy na základě jejich obsahu.|  
  
## <a name="layout-limitations"></a>Omezení rozložení  
 Obecně model Windows Forms ovládací prvky nelze škálovat a transformovat v rozsahu možném [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Následující seznam popisuje známá omezení, když se <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat svůj hostovaný model Windows Forms ovládací prvek do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho systému rozložení.  
  
- V některých případech nelze změnit velikost model Windows Forms ovládacích prvků, nebo může být velikost nastavena pouze na konkrétní rozměry. Například ovládací prvek model Windows Forms <xref:System.Windows.Forms.ComboBox> podporuje pouze jednu výšku, která je definována velikostí písma ovládacího prvku. Ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamické rozložení, kde lze prvky roztáhnout svisle, se hostovaný <xref:System.Windows.Forms.ComboBox> ovládací prvek nebude roztahovat podle očekávání.  
  
- Ovládací prvky model Windows Forms nelze otáčet ani zkosit. <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek vyvolá událost <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, pokud použijete transformaci zkosení nebo otočení. Pokud nezpracováváte událost <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, je vyvolána <xref:System.InvalidOperationException>.  
  
- Ve většině případů ovládací prvky model Windows Forms nepodporují proporcionální škálování. I když budou celkové rozměry ovládacího prvku škálované, podřízené ovládací prvky a prvky komponenty ovládacího prvku se nemusí měnit podle očekávání. Toto omezení závisí na tom, jak dobře každý ovládací prvek model Windows Forms podporuje škálování. Navíc nemůžete škálovat model Windows Forms ovládací prvky na velikost 0 pixelů.  
  
- Model Windows Forms ovládací prvky podporují automatické škálování, ve kterém se formulář automaticky změní na sebe sama a jeho ovládací prvky na základě velikosti písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m uživatelském rozhraní změna velikosti písma nemění velikost celého rozložení, i když jednotlivé prvky mohou dynamicky měnit velikost.  
  
### <a name="z-order"></a>Pořadí vykreslování  
 V uživatelském rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete změnit pořadí vykreslování prvků pro řízení překrývajících se chování. Hostovaný model Windows Forms ovládací prvek je vykreslen v samostatném elementu HWND, takže je vždy vykreslen nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky.  
  
 Hostovaný model Windows Forms ovládací prvek je také vykreslen nad všemi <xref:System.Windows.Documents.Adorner> prvky.  
  
## <a name="layout-behavior"></a>Chování rozložení  
 V následujících částech jsou popsány konkrétní aspekty chování rozložení při hostování model Windows Forms ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Škálování, Konverze jednotek a nezávislost zařízení  
 Vždy, když <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek provádí operace zahrnující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a model Windows Forms dimenze, jsou zapojeny dva systémy souřadnic: pixely nezávislé na zařízení pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a hardwarové pixely pro model Windows Forms. Proto je nutné použít správné rozvržení jednotek a škálování, aby bylo dosaženo konzistentního rozložení.  
  
 Převod mezi systémy souřadnic závisí na aktuálním rozlišení zařízení a všech transformacích rozložení nebo vykreslování použitých u <xref:System.Windows.Forms.Integration.WindowsFormsHost>ho prvku nebo na jeho nadřazených prvcích.  
  
 Pokud je výstupní zařízení 96 dpi a pro <xref:System.Windows.Forms.Integration.WindowsFormsHost> element není použité žádné škálování, jeden pixel nezávislý na zařízení se rovná jednomu hardwarovému pixelu.  
  
 Všechny ostatní případy vyžadují souřadnicový systém pro škálování. U hostovaného ovládacího prvku není změněna velikost. Místo toho se prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> pokusí škálovat hostovaný ovládací prvek a všechny jeho podřízené ovládací prvky. Vzhledem k tomu, že model Windows Forms plně nepodporuje škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek se škáluje na míru podporovanou konkrétními ovládacími prvky.  
  
 Přepište metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A>, aby poskytovala vlastní chování škálování pro hostovaný model Windows Forms ovládací prvek.  
  
 Kromě škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává případy zaokrouhlování a přetečení, jak je popsáno v následující tabulce.  
  
|Problém s převodem|Popis|  
|----------------------|-----------------|  
|Kusov|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dimenze v pixelech nezávislých na zařízení se zadává jako `double`a model Windows Forms velikosti hardwarových pixelů se zadává jako `int`. V případech, kdy jsou dimenze založené na `double`převedeny na dimenze založené na `int`, <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek používá standardní zaokrouhlování, aby desetinné hodnoty menší než 0,5 byly zaokrouhleny dolů na 0.|  
|Plně|Když <xref:System.Windows.Forms.Integration.WindowsFormsHost> element převede z hodnot `double` na hodnoty `int`, je možné přetečení. Hodnoty větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Vlastnosti související s rozložením  
 Vlastnosti, které řídí chování rozložení v ovládacích prvcích model Windows Forms a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky jsou mapovány vhodně pomocí elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Další informace najdete v tématu [mapování vlastností model Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Změny rozložení v hostovaném ovládacím prvku  
 Změny rozložení v hostovaném ovládacím prvku model Windows Forms jsou rozšířeny, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohly aktivovat aktualizace rozložení. Metoda <xref:System.Windows.UIElement.InvalidateMeasure%2A> v <xref:System.Windows.Forms.Integration.WindowsFormsHost> zajišťuje, aby změny rozložení v hostovaném ovládacím prvku způsobily spuštění modulu rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="continuously-sized-windows-forms-controls"></a>Průběžně měnit velikost model Windows Formsch ovládacích prvků  
 Model Windows Forms ovládací prvky, které podporují nepřetržité škálování plně spolupracuje se systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout. <xref:System.Windows.Forms.Integration.WindowsFormsHost> element používá metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> jako obvykle pro velikost a uspořádání hostovaného model Windows Formsho ovládacího prvku.  
  
### <a name="sizing-algorithm"></a>Algoritmus velikosti  
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> používá následující postup pro nastavení velikosti hostovaného ovládacího prvku:  
  
1. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> Přepisuje metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  
  
2. Chcete-li určit velikost hostovaného ovládacího prvku, metoda <xref:System.Windows.FrameworkElement.MeasureOverride%2A> volá metodu <xref:System.Windows.Forms.Control.GetPreferredSize%2A> hostovaného ovládacího prvku s omezením přeloženým z omezení předaného metodě <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
3. Metoda <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> se pokusí nastavit hostovaný ovládací prvek na dané omezení velikosti.  
  
4. Pokud vlastnost <xref:System.Windows.Forms.Control.Size%2A> hostovaného ovládacího prvku odpovídá zadanému omezení, má hostovaný ovládací prvek velikost omezení.  
  
 Pokud vlastnost <xref:System.Windows.Forms.Control.Size%2A> neodpovídá zadanému omezení, hostovaný ovládací prvek nepodporuje průběžnou změnu velikosti. Například ovládací prvek <xref:System.Windows.Forms.MonthCalendar> povoluje pouze diskrétní velikosti. Povolené velikosti pro tento ovládací prvek se skládají z celých čísel (představujících počet měsíců) pro výšku i šířku. V takových případech se <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek chová takto:  
  
- Pokud vlastnost <xref:System.Windows.Forms.Control.Size%2A> vrací větší velikost, než je zadané omezení, element <xref:System.Windows.Forms.Integration.WindowsFormsHost> vynechání hostovaného ovládacího prvku. Výška a šířka se zpracovává samostatně, takže hostovaný ovládací prvek může být oříznut v obou směrech.  
  
- Pokud vlastnost <xref:System.Windows.Forms.Control.Size%2A> vrací menší velikost než zadané omezení, <xref:System.Windows.Forms.Integration.WindowsFormsHost> akceptuje tuto hodnotu velikosti a vrátí hodnotu do systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho rozložení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Uspořádání ovládacích prvků model Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Migrace a interoperabilita](migration-and-interoperability.md)
