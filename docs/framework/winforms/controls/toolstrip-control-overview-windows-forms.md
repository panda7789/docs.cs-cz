---
title: Přehled ovládacího prvku ToolStrip
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741075"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ToolStrip> a jeho přidružené třídy poskytují společné rozhraní pro kombinování prvků uživatelského rozhraní do panelů nástrojů, stavových pruhů a nabídek. ovládací prvky <xref:System.Windows.Forms.ToolStrip> nabízejí bohatě dostupné prostředí pro návrh, které zahrnuje místní aktivaci a úpravy, vlastní rozložení a vory, což je schopnost panelů nástrojů sdílet horizontální nebo svislý prostor.  
  
 I když <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidává funkce do ovládacího prvku v předchozích verzích, <xref:System.Windows.Forms.ToolBar> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud to bude potřeba.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkce ovládacích prvků ToolStrip  
 Pomocí ovládacího prvku <xref:System.Windows.Forms.ToolStrip>:  
  
- Prezentovat společné uživatelské rozhraní napříč kontejnery.  
  
- Vytvářejte snadno přizpůsobené, běžně používané panely nástrojů, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například ukotvení, vytahování, tlačítka s textem a obrázky, rozevírací tlačítka a ovládací prvky, tlačítka přetečení a změna pořadí <xref:System.Windows.Forms.ToolStrip>ch položek v době běhu.  
  
- Podpora přetečení a přeřazení položek běhu. Funkce přetečení přesune položky do rozevírací nabídky, pokud není dostatek místa k jejich zobrazení v <xref:System.Windows.Forms.ToolStrip>.  
  
- Podporuje typický vzhled a chování operačního systému pomocí společného vykreslovacího modelu.  
  
- Zpracování událostí konzistentně pro všechny kontejnery a obsažené položky ve stejném způsobu, jakým se zpracovávají události pro jiné ovládací prvky.  
  
- Přetáhněte položky z jednoho <xref:System.Windows.Forms.ToolStrip> do jiné nebo v <xref:System.Windows.Forms.ToolStrip>.  
  
- Vytvořte rozevírací ovládací prvky a editory typů uživatelského rozhraní s pokročilými rozloženími v <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Použijte třídu <xref:System.Windows.Forms.ToolStripControlHost> pro použití jiných ovládacích prvků na <xref:System.Windows.Forms.ToolStrip> a získání <xref:System.Windows.Forms.ToolStrip> funkce pro ně.  
  
 Můžete roztáhnout funkce a upravit vzhled a chování pomocí <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>a <xref:System.Windows.Forms.ToolStripManager> spolu s výčty <xref:System.Windows.Forms.ToolStripRenderMode> a <xref:System.Windows.Forms.ToolStripManagerRenderMode>.  
  
 <xref:System.Windows.Forms.ToolStrip> ovládací prvek je vysoce konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí pro přizpůsobení vzhledu a chování. Níže jsou uvedeny někteří zajímavosti členové:  
  
### <a name="important-toolstrip-members"></a>Důležité členové prvku ToolStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Získá nebo nastaví, který okraj nadřazeného kontejneru je <xref:System.Windows.Forms.ToolStrip> ukotvený k.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Získává nebo nastavuje hodnotu, která označuje, jestli se přemístění pomocí přetažení a přeřazení položek provádí soukromě <xref:System.Windows.Forms.ToolStrip> třídou.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Získává nebo nastavuje hodnotu, která indikuje, jak <xref:System.Windows.Forms.ToolStrip> stanoví své položky.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Získává nebo nastavuje, jestli je <xref:System.Windows.Forms.ToolStripItem> připojená k <xref:System.Windows.Forms.ToolStrip> nebo <xref:System.Windows.Forms.ToolStripOverflowButton> nebo může mezi nimi být float.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Získá hodnotu, která označuje, zda <xref:System.Windows.Forms.ToolStripItem> v rozevíracím seznamu při kliknutí na <xref:System.Windows.Forms.ToolStripItem> zobrazit jiné položky.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Získá <xref:System.Windows.Forms.ToolStripItem>, které je tlačítko přetečení pro <xref:System.Windows.Forms.ToolStrip> s povoleným přetečením.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripRenderer>, která slouží k přizpůsobení vzhledu a chování pro <xref:System.Windows.Forms.ToolStrip>(vzhled a chování).|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Získá nebo nastaví styly malby, které mají být použity pro <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Vyvolá se při změně vlastnosti <xref:System.Windows.Forms.ToolStrip.Renderer%2A>.|  
  
 Flexibilita ovládacího prvku <xref:System.Windows.Forms.ToolStrip> se dosahuje pomocí několika doprovodných tříd. Níže jsou uvedeny některé z nejzajímavostich:  
  
### <a name="important-toolstrip-companion-classes"></a>Důležité doprovodné třídy ToolStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Nahrazuje a přidává funkce do <xref:System.Windows.Forms.MainMenu> třídy.|  
|<xref:System.Windows.Forms.StatusStrip>|Nahrazuje a přidává funkce do <xref:System.Windows.Forms.StatusBar> třídy.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Nahrazuje a přidává funkce do <xref:System.Windows.Forms.ContextMenu> třídy.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstraktní základní třída, která spravuje události a rozložení pro všechny prvky, které může obsahovat <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>nebo <xref:System.Windows.Forms.ToolStripDropDown>.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Poskytuje kontejner s panelem na každé straně formuláře, ve kterém mohou být ovládací prvky uspořádány různými způsoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Zpracovává funkci Malování pro objekty <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Poskytuje vzhled systém Microsoft Officeho stylu.|  
|<xref:System.Windows.Forms.ToolStripManager>|Řídí vykreslování <xref:System.Windows.Forms.ToolStrip> a vory a sloučení objektů <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>a <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Určuje styl Malování (Custom, Windows XP nebo systém Microsoft Office Professional), který se použije pro více objektů <xref:System.Windows.Forms.ToolStrip> obsažených ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Určuje styl Malování (Custom, Windows XP nebo systém Microsoft Office Professional), který se použije na jeden objekt <xref:System.Windows.Forms.ToolStrip> obsažený ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hostuje jiné ovládací prvky, které nejsou konkrétně <xref:System.Windows.Forms.ToolStrip> ovládací prvky, ale pro které chcete <xref:System.Windows.Forms.ToolStrip> funkce.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Určuje, zda má být <xref:System.Windows.Forms.ToolStripItem> určeno pro hlavní <xref:System.Windows.Forms.ToolStrip>, v <xref:System.Windows.Forms.ToolStrip>přetečení nebo ani v žádném z nich.|  
  
 Další informace naleznete v tématu [Přehled technologie ToolStrip](toolstrip-technology-summary.md) a [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
