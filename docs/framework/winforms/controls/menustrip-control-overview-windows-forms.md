---
title: MenuStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734465"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip – přehled ovládacího prvku (Windows Forms)
Nabídky pro uživatele zpřístupňují funkce, které jsou seskupeny podle společného motivu.  
  
 <xref:System.Windows.Forms.MenuStrip> ovládací prvek byl představen ve verzi 2,0 .NET Framework. Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> můžete snadno vytvářet nabídky, jako ty, které se nacházejí v systém Microsoft Office.  
  
 Ovládací prvek <xref:System.Windows.Forms.MenuStrip> podporuje slučování rozhraní více dokumentů (MDI) a nabídek, popisy tlačítek a přetečení. Přidáním přístupových klíčů, klávesových zkratek, značek zaškrtnutí, obrázků a oddělovacích pruhů můžete vylepšit použitelnost a čitelnost vašich nabídek.  
  
 Ovládací prvek <xref:System.Windows.Forms.MenuStrip> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.MainMenu>; Nicméně ovládací prvek <xref:System.Windows.Forms.MainMenu> zůstává zachován z důvodu zpětné kompatibility a budoucího použití, pokud zvolíte.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Způsoby použití ovládacího prvku MenuStrip  
 Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip>:  
  
- Vytvářejte snadno přizpůsobené, běžně používané nabídky, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například řazení textu a obrázků a zarovnání, operace přetažení, MDI, přetečení a alternativní režimy přístupu k příkazům nabídky.  
  
- Podporuje typický vzhled a chování operačního systému.  
  
- Zpracování událostí konzistentně pro všechny kontejnery a obsažené položky ve stejném způsobu, jakým se zpracovávají události pro jiné ovládací prvky.  
  
 V následující tabulce jsou uvedeny některé zvláště důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a přidružených tříd.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem>, která se používá k zobrazení seznamu podřízených formulářů MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Získá nebo nastaví způsob, jakým jsou podřízené nabídky sloučeny s nadřazenými nabídkami v aplikacích MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Získá nebo nastaví pozici sloučené položky v rámci nabídky v aplikacích MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Získá nebo nastaví hodnotu označující, zda je formulář kontejner pro podřízené formuláře MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Získá nebo nastaví hodnotu označující, zda jsou pro <xref:System.Windows.Forms.MenuStrip>zobrazeny popisy nástrojů.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Získává nebo nastavuje hodnotu, která označuje, jestli <xref:System.Windows.Forms.MenuStrip> podporuje přetečení funkce.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Získá nebo nastaví klávesové zkratky spojené s <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Získá nebo nastaví hodnotu označující, zda jsou vedle <xref:System.Windows.Forms.ToolStripMenuItem>zobrazeny klávesové zkratky, které jsou spojeny s <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Následující tabulka uvádí důležité doprovodné třídy <xref:System.Windows.Forms.MenuStrip>.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Představuje možnost, která je možné vybrat, která se zobrazuje na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Představuje místní nabídku.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne na <xref:System.Windows.Forms.ToolStripDropDownButton> nebo na položku nabídky vyšší úrovně.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Poskytuje základní funkce pro ovládací prvky odvozené od <xref:System.Windows.Forms.ToolStripItem>, které při kliknutí zobrazují rozevírací položky.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
