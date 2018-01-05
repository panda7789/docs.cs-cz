---
title: "ToolStrip – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45dab820072b3eb0bcc448ce32251e3ff5a3e622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> ovládací prvek a jeho přidružené třídy zadejte společná architektura pro kombinování prvky uživatelského rozhraní na panely nástrojů, stavové řádky a nabídky. <xref:System.Windows.Forms.ToolStrip>ovládací prvky nabízí bohaté prostředí návrhu, která zahrnuje aktivace na místě a úpravy, vlastní rozložení a rafting, což je možnost panelů nástrojů sdílet vodorovné nebo svislé místa.  
  
 I když <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidá funkce pro ovládací prvek v předchozích verzích <xref:System.Windows.Forms.ToolBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, v případě potřeby.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkce ovládacích prvcích ToolStrip  
 Použití <xref:System.Windows.Forms.ToolStrip> řídit k:  
  
-   K dispozici uživatelské rozhraní společné napříč kontejnery.  
  
-   Vytvořit snadno přizpůsobené, běžně zaměstnání panely nástrojů, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například ukotvení, raftingu, tlačítka s textem a bitové kopie, rozevíracího seznamu tlačítka a ovládací prvky, přetečení tlačítka a změny pořadí spuštění <xref:System.Windows.Forms.ToolStrip> položky.  
  
-   Podpora přetečení a změna pořadí položek běhu. Funkci přetečení při není dostatek místa pro zobrazení je v Přesune položky do rozevírací nabídky <xref:System.Windows.Forms.ToolStrip>.  
  
-   Podpora typické vzhled a chování operačního systému, prostřednictvím společného modelu vykreslování.  
  
-   Zpracování událostí konzistentně pro všechny kontejnery a obsažených položek, stejně jako zpracování událostí pro další ovládací prvky.  
  
-   Přetáhnout položky z jednoho <xref:System.Windows.Forms.ToolStrip> do jiné nebo uvnitř <xref:System.Windows.Forms.ToolStrip>.  
  
-   Vytvořit ovládací prvky rozevíracího seznamu a uživatelské rozhraní typ editory s pokročilé rozložení v <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Použít <xref:System.Windows.Forms.ToolStripControlHost> třídu se má použít na další ovládací prvky <xref:System.Windows.Forms.ToolStrip> a získat <xref:System.Windows.Forms.ToolStrip> funkce pro ně.  
  
 Můžete rozšířit funkce a upravit vzhled a chování pomocí <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, a <xref:System.Windows.Forms.ToolStripManager> spolu s <xref:System.Windows.Forms.ToolStripRenderMode> a <xref:System.Windows.Forms.ToolStripManagerRenderMode> výčty.  
  
 <xref:System.Windows.Forms.ToolStrip> Řízení je vysoce Konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí můžete přizpůsobit vzhled a chování. Tady jsou některé pozoruhodné členy:  
  
### <a name="important-toolstrip-members"></a>Členy důležité ToolStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Získá nebo nastaví které okraje nadřazeného kontejneru <xref:System.Windows.Forms.ToolStrip> ukotven.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Získá nebo nastaví hodnotu určující, zda přetahování myší a změna pořadí položek jsou zpracovávány soukromě pomocí <xref:System.Windows.Forms.ToolStrip> třídy.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Získá nebo nastaví hodnotu, která určuje jak <xref:System.Windows.Forms.ToolStrip> rozložen jeho položky.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Získá nebo nastaví zda <xref:System.Windows.Forms.ToolStripItem> je připojen k <xref:System.Windows.Forms.ToolStrip> nebo <xref:System.Windows.Forms.ToolStripOverflowButton> nebo můžete mezi těmito dvěma float.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Získá hodnotu, která určuje zda <xref:System.Windows.Forms.ToolStripItem> zobrazí další položky v rozevírací seznam při <xref:System.Windows.Forms.ToolStripItem> po kliknutí na.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Získá <xref:System.Windows.Forms.ToolStripItem> tlačítko pro který je přetečení <xref:System.Windows.Forms.ToolStrip> s přetečení povolena.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripRenderer> použít k přizpůsobení vzhledu a chování (vzhled a chování) <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Získá nebo nastaví styly Malování použije <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Vyvolá, když <xref:System.Windows.Forms.ToolStrip.Renderer%2A> změny vlastností.|  
  
 <xref:System.Windows.Forms.ToolStrip> Flexibilitu ovládacího prvku se dosáhne použitím několik tříd doprovodné. Tady jsou některé z nejvíc pozoruhodné:  
  
### <a name="important-toolstrip-companion-classes"></a>Třídy důležitého pomocníka ToolStrip  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Nahradí a přidá funkce <xref:System.Windows.Forms.MainMenu> třídy.|  
|<xref:System.Windows.Forms.StatusStrip>|Nahradí a přidá funkce <xref:System.Windows.Forms.StatusBar> třídy.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Nahradí a přidá funkce <xref:System.Windows.Forms.ContextMenu> třídy.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstraktní základní třídu, která spravuje události a rozložení pro všechny elementy, <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, nebo <xref:System.Windows.Forms.ToolStripDropDown> může obsahovat.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Poskytuje kontejner s panelem na každé straně formuláře, ve kterém mohou být uspořádány ovládací prvky různými způsoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Zpracovává vykreslovací funkce pro <xref:System.Windows.Forms.ToolStrip> objekty.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Poskytuje Microsoft Office – styl.|  
|<xref:System.Windows.Forms.ToolStripManager>|Ovládací prvky <xref:System.Windows.Forms.ToolStrip> vykreslování a rafting a sloučení <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, a <xref:System.Windows.Forms.ToolStripMenuItem> objekty.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Určuje styl Malování (vlastní, Windows XP nebo Microsoft Office Professional) použitý pro více <xref:System.Windows.Forms.ToolStrip> objekty obsažené ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Určuje styl Malování (vlastní, Windows XP nebo Microsoft Office Professional) použitý pro jednu <xref:System.Windows.Forms.ToolStrip> objektů obsažených ve formuláři.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hostitelem jiných ovládacích prvků, které nejsou konkrétně <xref:System.Windows.Forms.ToolStrip> ovládací prvky, ale u kterého chcete <xref:System.Windows.Forms.ToolStrip> funkce.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Určuje, zda <xref:System.Windows.Forms.ToolStripItem> je nastíněny v hlavním <xref:System.Windows.Forms.ToolStrip>, v oblasti přetečení <xref:System.Windows.Forms.ToolStrip>, nebo žádný z nich.|  
  
 Další informace najdete v tématu [souhrn technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) a [architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
