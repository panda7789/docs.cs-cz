---
title: ToolStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3e532b040d3c7859220b7f73958b63e7208b988c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009523"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> ovládacího prvku a jeho přidružené třídy poskytují běžné rámec pro kombinování prvky uživatelského rozhraní na panely nástrojů, stavovém řádku a nabídky. <xref:System.Windows.Forms.ToolStrip> ovládací prvky nabízejí celou řadu možností návrhu, který zahrnuje aktivace na místě a úpravy, vlastní rozložení a rafting, což je schopnost panely nástrojů sdílet místa na vodorovný nebo svislý.  
  
 I když <xref:System.Windows.Forms.ToolStrip> nahradí a přidá funkce do ovládacího prvku v předchozích verzích <xref:System.Windows.Forms.ToolBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití v případě potřeby.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkce ovládacích prvků ToolStrip  
 Použití <xref:System.Windows.Forms.ToolStrip> ovládacího prvku:  
  
- K dispozici běžného uživatelského rozhraní napříč kontejnery.  
  
- Vytvářejte snadno přizpůsobená, běžně proces panely nástrojů, které podporují rozšířené funkce uživatelského rozhraní a rozložení, jako je například ukotvení, raftingu, tlačítka pomocí textu a obrázků, rozevíracích tlačítek a ovládací prvky, přetečení tlačítka a změny pořadí za běhu <xref:System.Windows.Forms.ToolStrip> položky.  
  
- Podpora přetečení a také přeuspořádání položek za běhu. Funkce přetečení Přesune položky do rozevírací nabídky a není dostatek místa pro zobrazení v <xref:System.Windows.Forms.ToolStrip>.  
  
- Podpora typické vzhled a chování operačního systému prostřednictvím společného modelu vykreslování.  
  
- Zpracování událostí konzistentní pro všechny kontejnery a upravovat položky, stejně jako zpracování událostí pro ostatní ovládací prvky.  
  
- Přetáhněte položky z jednoho <xref:System.Windows.Forms.ToolStrip> do jiné nebo v rámci <xref:System.Windows.Forms.ToolStrip>.  
  
- Vytvoření ovládacích prvků rozevírací seznam a uživatel editory typů rozhraní pomocí pokročilé rozložení <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Použít <xref:System.Windows.Forms.ToolStripControlHost> třídu použít na další ovládací prvky <xref:System.Windows.Forms.ToolStrip> a získat <xref:System.Windows.Forms.ToolStrip> funkce pro ně.  
  
 Můžete rozšířit funkce a upravit vzhled a chování pomocí <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, a <xref:System.Windows.Forms.ToolStripManager> spolu s <xref:System.Windows.Forms.ToolStripRenderMode> a <xref:System.Windows.Forms.ToolStripManagerRenderMode> výčty.  
  
 <xref:System.Windows.Forms.ToolStrip> Ovládací prvek je vysoce konfigurovatelné a rozšiřitelné, a poskytuje mnoho vlastnosti, metody a události upravit vzhled a chování. Níže jsou uvedeny některé zajímavosti členy:  
  
### <a name="important-toolstrip-members"></a>Ovládací prvek ToolStrip důležité členy  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Získá nebo nastaví které okrajem nadřazeného kontejneru <xref:System.Windows.Forms.ToolStrip> ukotven.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Získá nebo nastaví hodnotu určující, zda jsou soukromě podle zpracovány přetahování myší a také přeuspořádání položek <xref:System.Windows.Forms.ToolStrip> třídy.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Získá nebo nastaví hodnotu, která popisuje, jak může <xref:System.Windows.Forms.ToolStrip> rozložen jejích položek.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Získá nebo nastaví, zda <xref:System.Windows.Forms.ToolStripItem> je připojen k <xref:System.Windows.Forms.ToolStrip> nebo <xref:System.Windows.Forms.ToolStripOverflowButton> nebo můžete uvolnit mezi nimi.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Získává hodnotu označující, zda <xref:System.Windows.Forms.ToolStripItem> v rozevíracím seznamu se zobrazí další položky seznamu, když <xref:System.Windows.Forms.ToolStripItem> dojde ke kliknutí na.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Získá <xref:System.Windows.Forms.ToolStripItem> , který je tlačítku přetečení pro <xref:System.Windows.Forms.ToolStrip> s přetečením povolena.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripRenderer> použít k přizpůsobení vzhledu a chování (vzhled a chování) <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Získává nebo nastavuje Styly překreslování použije <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Vyvolá se, když <xref:System.Windows.Forms.ToolStrip.Renderer%2A> změny vlastností.|  
  
 <xref:System.Windows.Forms.ToolStrip> Flexibilitu ovládacího prvku se dosahuje prostřednictvím počet doprovodné třídy. Dále jsou uvedené některé z nejčastěji zajímavosti:  
  
### <a name="important-toolstrip-companion-classes"></a>Třídy důležitého pomocníka ovládací prvek ToolStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Nahradí a přidá funkce, které <xref:System.Windows.Forms.MainMenu> třídy.|  
|<xref:System.Windows.Forms.StatusStrip>|Nahradí a přidá funkce, které <xref:System.Windows.Forms.StatusBar> třídy.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Nahradí a přidá funkce, které <xref:System.Windows.Forms.ContextMenu> třídy.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstraktní základní třídu, která spravuje události a rozložení pro všechny prvky, které <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, nebo <xref:System.Windows.Forms.ToolStripDropDown> může obsahovat.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Poskytuje kontejner s panelem na každé straně formuláře, ve kterém lze uspořádat ovládací prvky různými způsoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Zpracovává funkce Malování pro <xref:System.Windows.Forms.ToolStrip> objekty.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Poskytuje vzhled aplikace Microsoft Office – vizuální styl.|  
|<xref:System.Windows.Forms.ToolStripManager>|Ovládací prvky <xref:System.Windows.Forms.ToolStrip> vykreslování a rafting a sloučení <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, a <xref:System.Windows.Forms.ToolStripMenuItem> objekty.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Určuje styl kreslení (vlastní, Windows XP nebo Microsoft Office Professional) použitý k několika <xref:System.Windows.Forms.ToolStrip> objekty obsažené ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Určuje styl vykreslování (vlastní, Windows XP nebo Microsoft Office Professional) použitý k jednomu <xref:System.Windows.Forms.ToolStrip> objekt obsažený ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hostuje další ovládací prvky, které nejsou konkrétně <xref:System.Windows.Forms.ToolStrip> ovládacích prvků, ale pro který chcete <xref:System.Windows.Forms.ToolStrip> funkce.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Určuje, zda <xref:System.Windows.Forms.ToolStripItem> je rozloží na hlavní <xref:System.Windows.Forms.ToolStrip>, na přetečení <xref:System.Windows.Forms.ToolStrip>, nebo ani jedna.|  
  
 Další informace najdete v tématu [souhrn technologie ToolStrip](toolstrip-technology-summary.md) a [architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
