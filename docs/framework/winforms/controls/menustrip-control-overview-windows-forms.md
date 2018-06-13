---
title: MenuStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b09d653210c72a38bbc4dc0858ae2553ad9cbeef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537483"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip – přehled ovládacího prvku (Windows Forms)
Nabídky vystavit funkcionalitu pro vaše uživatele tím, že se příkazy, které jsou seskupené podle běžné motiv.  
  
 <xref:System.Windows.Forms.MenuStrip> Řízení je nové na tuto verzi sady Visual Studio a rozhraní .NET Framework. Pomocí ovládacího prvku můžete snadno vytvořit nabídky například výstrahám nacházejícím se v Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Řízení podporuje rozhraní více dokumentů (MDI) a slučování nabídek, popisy a přetečení. Přidáním přístupové klíče, klávesové zkratky, značky zaškrtnutí, Image a oddělovacích pruhů můžete zlepšují použitelnost a čitelnost vaší nabídky.  
  
 <xref:System.Windows.Forms.MenuStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.MainMenu> řízení; však <xref:System.Windows.Forms.MainMenu> řízení se zachovává kvůli zpětné kompatibility a budoucí použití, pokud si zvolíte.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Způsoby použití ovládacího prvku MenuStrip  
 Použití <xref:System.Windows.Forms.MenuStrip> řídit k:  
  
-   Vytvořit snadno přizpůsobené, běžně zaměstnání nabídky, které podporují rozšířené uživatelské rozhraní a rozložení funkce, jako je text a řazení bitové kopie a zarovnání, operací přetažení myší, MDI, přetečení a alternativní režimy přístup k příkazům nabídky.  
  
-   Podpora typické vzhled a chování operačního systému.  
  
-   Zpracování událostí konzistentně pro všechny kontejnery a obsažených položek, stejně jako zpracování událostí pro další ovládací prvky.  
  
 Následující tabulka uvádí některé důležité zvláště tehdy, vlastnosti <xref:System.Windows.Forms.MenuStrip> a související třídy.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem> sloužící k zobrazení seznamu podřízených formulářů MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Získá nebo nastaví, jak slučování nabídek podřízené s nabídkami nadřazené v aplikace MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Získá nebo nastaví pozici sloučené položky v rámci nabídky v aplikace MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Získá nebo nastaví hodnotu určující, zda je kontejner pro podřízených formulářů MDI formulář.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Získá nebo nastaví hodnotu určující, zda jsou pro zobrazen popisy tlačítek <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Získá nebo nastaví hodnotu, která určuje zda <xref:System.Windows.Forms.MenuStrip> podporuje přetečení funkce.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Získá nebo nastaví klávesové zkratky přidružené <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Získá nebo nastaví hodnotu určující, zda zástupce klíče, které jsou přidružené <xref:System.Windows.Forms.ToolStripMenuItem> se zobrazí vedle možnosti <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.MenuStrip> doprovodné třídy.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Představuje volitelný možnost zobrazí na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Představuje místní nabídky.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Reprezentuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne <xref:System.Windows.Forms.ToolStripDropDownButton> nebo vyšší úrovni položku nabídky.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Poskytuje základní funkce pro ovládací prvky odvozené od <xref:System.Windows.Forms.ToolStripItem> , zobrazí rozevírací seznam položky při kliknutí na.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
