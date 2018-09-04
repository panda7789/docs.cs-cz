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
ms.openlocfilehash: 5856e710ad5a70fd740a5bb99ff241b8d9f2037a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518945"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Předpoklady rozložení pro element WindowsFormsHost
Toto téma popisuje, jak <xref:System.Windows.Forms.Integration.WindowsFormsHost> element komunikuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém rozložení.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podporují jiné, ale podobné, logiku pro velikost a umístění prvků na formuláři nebo na stránce. Při vytváření hybridního uživatelského rozhraní (UI), který je hostitelem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> element integruje schémata dvě rozložení.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Rozdíly v rozložení mezi rozhraními WPF a Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá nezávislé na překladu rozložení. Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení dimenze jsou určeny pomocí *pixelech nezávislých na zařízení*. Pixel nezávislých na zařízení je jedna devadesát čtvrtinu, šestinu palce velikost a nezávislé na rozlišení, proto zobrazí podobné výsledky bez ohledu na to, jestli jsou vykreslování 72 dpi monitorování nebo tiskárnu 19 200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také je založená na *dynamické rozložení*. To znamená, že prvek uživatelského rozhraní samotného uspořádá ve formuláři nebo na stránku podle její obsah, jeho nadřazeného kontejneru rozložení a obrazovku k dispozici. Dynamické rozložení usnadňuje lokalizaci úpravou automaticky velikost a umístění prvků uživatelského rozhraní při změně délku řetězce, které obsahují.  
  
 Rozložení v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je závislé na zařízení a pravděpodobně být statické. Obvykle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky jsou absolutně na formulář pomocí dimenze zadaný v pixelech hardwaru. Ale [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nepodporuje některé funkce dynamické rozložení dle souhrnu v následující tabulce.  
  
|Funkce rozložení|Popis|  
|--------------------|-----------------|  
|Automatické přizpůsobení velikosti|Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Změna velikosti ovládacích prvků samy o sobě správně zobrazit jejich obsah. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Ukotvení a dokování|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídí podporu umístění a velikosti podle nadřazeného kontejneru. Další informace naleznete v tématu <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Automatické škálování|Ovládací prvky kontejneru velikost sami sebe i jejich podřízené prvky podle rozlišení výstupní zařízení nebo velikost v pixelech výchozí písmo kontejneru. Další informace najdete v tématu [automatické změně měřítka ve Windows Forms](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Kontejnery rozložení|<xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky uspořádejte jejich podřízených ovládacích prvků a nastavení velikosti sami podle jejich obsah.|  
  
## <a name="layout-limitations"></a>Omezení rozložení  
 Obecně platí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze škálovat a transformovat možném v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Následující seznam popisuje známých omezeních při <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat své prostředí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém rozložení.  
  
-   V některých případech [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze změnit velikost nebo můžou mít velikost pouze na určité dimenze. Například [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> ovládací prvek podporuje pouze jeden výšku, které jsou definovány pomocí ovládacího prvku velikost písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamického rozložení, kde prvky můžete roztáhnout svisle, hostovaný <xref:System.Windows.Forms.ComboBox> ovládací prvek nebude roztáhnout podle očekávání.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze otáčet nebo zešikmená. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element vyvolává <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událost, když je použijete transformace zkosení nebo otočení. Pokud jste ke zpracování <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> události, <xref:System.InvalidOperationException> je vyvolána.  
  
-   Ve většině případů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků nepodporují proporcionální škálování. I když bude možné škálovat celkové rozměry ovládacího prvku podřízených ovládacích prvků a komponent ovládacího prvku nemusí měnit velikost podle očekávání. Toto omezení závisí na tom, jak dobře se každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek podporuje škálování. Kromě toho už nebude možné škálovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků na velikost 0 v pixelech.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídí podporu automatického škálování, ve kterém formuláři automaticky změní velikost sebe sama a jejích ovládacích prvků na základě velikosti písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, změna velikosti písma se velikost celé rozložení, i když může dynamicky velikost jednotlivých prvků.  
  
### <a name="z-order"></a>Pořadí vykreslování  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelského rozhraní, můžete změnit pořadí vykreslování prvků překrývající se chování ovládacího prvku. Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek vykreslen v samostatných HWND, takže je vždy vykreslován nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy.  
  
 Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] také ovládací prvek vykreslen na libovolné <xref:System.Windows.Documents.Adorner> elementy.  
  
## <a name="layout-behavior"></a>Chování rozložení  
 Následující části popisují konkrétní aspekty chování rozložení, při hostování za nástrojem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Změna velikosti, převod jednotek a nezávislost zařízení  
 Pokaždé, když <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provádí operace týkající se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dimenze, dvěma systémy souřadnic souvisejí: pixelech nezávislých na zařízení pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a hardware pixelů pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto je nutné použít správné jednotky a škálování převody zajištění konzistentního rozložení.  
  
 Převod mezi systémy souřadnic závisí na aktuální řešení zařízení a libovolný rozložení nebo vykreslování transformací použitá na <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a jeho nadřazenými prvky.  
  
 Pokud výstupní zařízení je 96 dpi a bez škálování byl použit <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, jeden pixel nezávislých na zařízení se rovná na jeden pixel hardwaru.  
  
 Všech ostatních případech vyžadovat škálování systém souřadnic. Hostovaného ovládacího prvku se změněnou velikostí. Místo toho <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí škálování hostovaného ovládacího prvku a všechny jeho podřízené ovládací prvky. Protože [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] plně nepodporuje škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element se škáluje, aby do jaké míry podporuje konkrétní ovládací prvky.  
  
 Přepsat <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> metodu k dispozici vlastní chování škálování pro hostované ovládací prvek Windows Forms.  
  
 Kromě škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek zpracovává zaokrouhlení a přetečení případy, jak je popsáno v následující tabulce.  
  
|Převod problém|Popis|  
|----------------------|-----------------|  
|Zaokrouhlení|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v pixelech nezávislých na zařízení jsou zadané jako `double`, a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hardwaru v pixelech, které jsou určeny jako `int`. V případech, kde `double`– na základě rozměry jsou převedeny na `int`– na základě dimenze, <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek používá standardní zaokrouhlení tak, aby desetinné hodnoty menší než 0,5 zaokrouhlená dolů na 0.|  
|přetečení|Když <xref:System.Windows.Forms.Integration.WindowsFormsHost> element převede z `double` hodnoty `int` hodnoty, je možné přetečení. Hodnoty, které jsou větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Vlastnosti související s rozložením  
 Vlastnosti, které řídí chování rozložení v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky jsou odpovídajícím způsobem podle mapovány <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Další informace najdete v tématu [Windows Forms a WPF vlastnost mapování](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Změny rozložení v hostovaného ovládacího prvku  
 Změny rozložení v hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek se rozšíří na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aktivovat aktualizaci rozložení. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> zajistí, že způsobit změny rozložení v ovládacím prvku hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modul rozložení pro spuštění.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Průběžně velikosti ovládacích prvků Windows Forms  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které podporují průběžné škálování plně pracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém rozložení. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody jako obvykle pro velikost a uspořádání hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
### <a name="sizing-algorithm"></a>Nastavení velikosti algoritmus  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek používá následující postup pro nastavení velikosti hostovaného ovládacího prvku:  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> Přepíše element <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.  
  
2.  K určení velikosti hostované ovládací prvek, <xref:System.Windows.FrameworkElement.MeasureOverride%2A> hostovaného ovládacího prvku volá metodu <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metodu s omezením přeložit z omezení předán <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoda.  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Metoda se pokusí hostovaného ovládacího prvku nastavte na danou velikost omezení.  
  
4.  Pokud hostovaného ovládacího prvku <xref:System.Windows.Forms.Control.Size%2A> vlastnosti odpovídají zadané omezení, omezení velikostí hostovaného ovládacího prvku.  
  
 Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost neodpovídá zadané omezení, hostované ovládací prvek nepodporuje průběžné velikosti. Například <xref:System.Windows.Forms.MonthCalendar> ovládací prvek umožňuje pouze diskrétní velikosti. Povolené velikosti pro tento ovládací prvek se skládá z celých čísel (představující počet měsíců) pro výšku a šířku. V případech, jako je například to <xref:System.Windows.Forms.Integration.WindowsFormsHost> element se chová takto:  
  
-   Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost vrací větší velikost než zadaná omezení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element klipy hostovaného ovládacího prvku. Výška a šířka jsou zpracovány samostatně, takže hostovaného ovládacího prvku může být oříznut v obou směrech.  
  
-   Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost vrací menší než zadaná omezení <xref:System.Windows.Forms.Integration.WindowsFormsHost> přijme tuto hodnotu velikosti a vrátí hodnotu, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém rozložení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [Uspořádání Windows Forms ovládací prvky v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
