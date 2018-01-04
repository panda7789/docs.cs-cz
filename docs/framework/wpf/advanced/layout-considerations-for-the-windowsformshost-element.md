---
title: "Předpoklady rozložení pro element WindowsFormsHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 895185797ebdef2145caec4c1c5ac26e3688c463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Předpoklady rozložení pro element WindowsFormsHost
Toto téma popisuje, jak <xref:System.Windows.Forms.Integration.WindowsFormsHost> element komunikuje s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení systému.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podporovat jiné, ale podobné, logiku pro změny velikosti a rozmístění prvků na formuláři nebo na stránce. Když vytvoříte hybridní uživatelské rozhraní (UI), který je hostitelem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> element integruje dvě rozložení schémat.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Rozdíly v rozložení WPF a Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá nezávislé na rozlišení rozložení. Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení dimenze jsou určeny pomocí *pixelů nezávislé na zařízení*. Pixel nezávislé na zařízení je jeden 90 šestinu palce velikostí a nezávislé na rozlišení, proto podobné výsledky bez ohledu na to, jestli jsou vykreslování monitorování 72 dpi nebo 19 200 dpi tiskárny.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je také na základě *dynamické rozložení*. To znamená, že prvku uživatelského rozhraní samotného uspořádá na formuláři nebo na stránce podle jeho obsah, jeho nadřazený kontejner rozložení a velikost dostupné obrazovky. Dynamické rozložení usnadňuje lokalizaci tak, že pokud řetězců, které obsahují změnit délku automaticky upraví velikost a umístění prvků uživatelského rozhraní.  
  
 Rozložení v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je závislé na zařízení a vyšší pravděpodobnost být statická. Obvykle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky jsou umístěny absolutně na formuláři pomocí dimenzí zadané v pixelech hardwaru. Ale [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podporuje některé funkce dynamické rozložení dle souhrnu v následující tabulce.  
  
|Funkce rozložení|Popis|  
|--------------------|-----------------|  
|Automatická změna velikosti|Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky změnit a zobrazit jejich obsah správně. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Ukotvení a dokování|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky podporují umístění a nastavení velikosti podle nadřazený kontejner. Další informace naleznete v tématu <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Automatické škálování|Ovládací prvky kontejneru změnit velikost sami a jejich podřízené podle rozlišení výstupní zařízení nebo velikost v pixelech výchozího kontejneru písma. Další informace najdete v tématu [automatické škálování ve Windows Forms](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Kontejnerů rozložení|<xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky uspořádat jejich podřízené ovládací prvky a velikost sami podle jejich obsah.|  
  
## <a name="layout-limitations"></a>Omezení rozložení  
 Obecně platí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze škálovat a transformovat možném v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Následující seznam popisuje známá omezení při <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat jeho hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení systému.  
  
-   V některých případech [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze změnit velikost nebo může být dimenzovány pouze pro konkrétní dimenze. Například [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> řízení podporuje pouze jeden výška, který je definovaný velikost písma ovládacího prvku. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamické rozložení, kde elementy lze roztáhnout ve svislém směru hostovaný <xref:System.Windows.Forms.ComboBox> řízení nebude stretch podle očekávání.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky nelze otáčet nebo nesouměrně rozdělí. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element vyvolá <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událost, pokud použijete transformaci zkosení nebo otočení. Pokud není zpracovat <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> události, <xref:System.InvalidOperationException> je vyvolána.  
  
-   Ve většině případů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporují přímo úměrná škálování. I když bude škálovat celkové rozměry ovládacího prvku, podřízené ovládací prvky a součásti elementy ovládacího prvku nesmí změnit velikost podle očekávání. Toto omezení závisí na tom, jak dobře každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení podporuje škálování. Kromě toho nelze škálovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky dolů velikost 0 pixelů.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky podporují automatické škálování, ve kterém bude formulář automaticky přizpůsobit samostatně a jeho ovládací prvky založené na velikost písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, změny velikosti písma není změnit velikost celého rozložení, i když může dynamicky změnit velikost jednotlivých elementů.  
  
### <a name="z-order"></a>Pořadí Z-order  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, můžete změnit pořadí vykreslování elementů na ovládací prvek překrývání chování. Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení se vykresluje v samostatných HWND, takže je vždy vykreslován na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy.  
  
 Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení vykreslením také na všechny <xref:System.Windows.Documents.Adorner> elementy.  
  
## <a name="layout-behavior"></a>Chování rozložení  
 Následující části popisují konkrétní aspektů rozložení chování při hostování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Změna velikosti, převod jednotek a nezávislost zařízení  
 Vždy, když <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provádí operace zahrnující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se podílejí dimenzí, dvěma systémy souřadnic: pixelů nezávislé na zařízení pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a pixelů hardwaru pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto je nutné použít správné jednotky a škálování převody k dosažení konzistentního rozložení.  
  
 Převod mezi systémy souřadnic závisí na aktuální řešení zařízení a všechny rozložení nebo vykreslování transformací použitá na <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a jeho předchůdců.  
  
 Pokud výstupní zařízení je 96 dpi a žádné škálování byl použit <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, jeden bod. nezávislé na zařízení se rovná jednoho pixelu hardwaru.  
  
 Všech ostatních případech vyžadují systém souřadnic škálování. Hostované ovládacího prvku se nezmění. Místo toho <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí škálovat hostovaného ovládacího prvku a všechny jeho podřízené ovládací prvky. Protože [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nepodporuje plně škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element škáluje na úroveň podporuje konkrétní ovládací prvky.  
  
 Přepsání <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> metody můžete zajistit vlastní chování škálování pro hostované [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládacího prvku.  
  
 Kromě škálování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává zaokrouhlení a přetečení případů, jak je popsáno v následující tabulce.  
  
|Převod problém|Popis|  
|----------------------|-----------------|  
|Zaokrouhlení|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nezávislé na zařízení v pixelech jsou zadané jako `double`, a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hardwaru v pixelech jsou zadané jako `int`. V případech, kde `double`– na základě dimenze se převedou na `int`– na základě dimenzí, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element používá standardní zaokrouhlení tak, aby desetinné číslo menší než 0,5 se zaokrouhlí směrem dolů na 0.|  
|Přetečení|Když <xref:System.Windows.Forms.Integration.WindowsFormsHost> element převádí z `double` hodnoty k `int` hodnoty, je možné přetečení. Hodnoty, které jsou větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Vlastnosti související s rozložením  
 Vlastnosti, které řídí chování rozložení v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy jsou správně pomocí namapované <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu. Další informace najdete v tématu [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Rozložení změny v hostované ovládacího prvku  
 Rozložení změny v hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení rozšířeny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k aktivaci rozložení aktualizace. <xref:System.Windows.UIElement.InvalidateMeasure%2A> Metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> zajistí, že změny rozložení v ovládacím prvku hostované způsobit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modul rozložení ke spuštění.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Nepřetržitě velikosti ovládacích prvků Windows Forms  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které podporují průběžné škálování plně pracovat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení systému. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody obvyklým pro velikost a uspořádání hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
### <a name="sizing-algorithm"></a>Změna velikosti algoritmus  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element používá následující postup pro velikost hostovaného ovládacího prvku:  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element přepsání <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody.  
  
2.  K určení velikosti prvku hostované <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoda volá hostované ovládacího prvku <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda s omezením na přeložit z omezení předaný <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metoda.  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Metoda pokus o nastavení ovládacího prvku, hostované na danou velikost omezení.  
  
4.  Pokud hostované ovládacího prvku <xref:System.Windows.Forms.Control.Size%2A> vlastnost odpovídá zadané omezení, je velikost hostované ovládacího prvku na omezení.  
  
 Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost neodpovídá zadané omezení, hostované ovládací prvek nepodporuje průběžné velikosti. Například <xref:System.Windows.Forms.MonthCalendar> řízení umožňuje pouze diskrétní velikosti. Povolené velikosti pro tento ovládací prvek se skládá z celých čísel (představující počet měsíců) pro výškou a šířkou. V případech, například <xref:System.Windows.Forms.Integration.WindowsFormsHost> element se chová takto:  
  
-   Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost vrací větší velikost než zadané omezení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element klipy hostovaného ovládacího prvku. Výška a šířka jsou zpracovávány samostatně, takže může být oříznut hostovaného ovládacího prvku v obou směrech.  
  
-   Pokud <xref:System.Windows.Forms.Control.Size%2A> vlastnost vrací menší velikost než zadané omezení <xref:System.Windows.Forms.Integration.WindowsFormsHost> přijímá tuto hodnotu velikosti a vrátí hodnotu na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [Uspořádání Windows Forms – ovládací prvky v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
