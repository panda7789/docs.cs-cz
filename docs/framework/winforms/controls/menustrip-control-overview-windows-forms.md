---
title: MenuStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b72fcf75aeebc297d09cbaa9dbf00bb2370b1222
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625755"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip – přehled ovládacího prvku (Windows Forms)
Nabídky poskytují funkcionalitu uživatele tím, že se příkazy, které jsou seskupeny podle společnými tématy.  
  
 <xref:System.Windows.Forms.MenuStrip> Ovládací prvek je nová pro tuto verzi sady Visual Studio a rozhraní .NET Framework. Pomocí ovládacího prvku můžete snadno vytvořit nabídky například výstrahám nacházejícím se v aplikaci Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Ovládací prvek podporuje rozhraní více dokumentů (MDI) a slučování nabídek, popisy tlačítek a přetečení. Přidáním přístupových klíčů, klávesové zkratky, značky zaškrtnutí, obrázky a oddělovacích pruhů můžete vylepšit použitelnosti a srozumitelnost vaší nabídky.  
  
 <xref:System.Windows.Forms.MenuStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.MainMenu> řízení; však <xref:System.Windows.Forms.MainMenu> ovládací prvek je zachován z důvodu zpětné kompatibility a budoucí použití, pokud se rozhodnete.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Způsoby, jak pomocí ovládacího prvku MenuStrip  
 Použití <xref:System.Windows.Forms.MenuStrip> ovládacího prvku:  
  
- Vytvářejte snadno přizpůsobená, běžně proces nabídek, které podporují rozšířené uživatelské rozhraní a rozložení funkce, jako je text a obrázek řazení a zarovnání, operace přetažení myší, MDI, přetečení a alternativní způsoby přístup k příkazům nabídky.  
  
- Podpora typické vzhled a chování operačního systému.  
  
- Zpracování událostí konzistentní pro všechny kontejnery a upravovat položky, stejně jako zpracování událostí pro ostatní ovládací prvky.  
  
 V následující tabulce jsou uvedeny některé zvlášť důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a související třídy.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem> , který slouží k zobrazení seznamu podřízených formulářů MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Získá nebo nastaví, jak slučování podřízených nabídek s nabídkami nadřazená aplikace MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Získá nebo nastaví pozici sloučené položky v nabídce aplikace MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Získá nebo nastaví hodnotu určující, zda je formulář jako kontejner pro podřízené formuláře MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Získá nebo nastaví hodnotu určující, zda jsou uvedeny popisy tlačítek pro <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.MenuStrip> podporuje přetečení funkce.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Získá nebo nastaví klávesových zkratek přidružené <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Získá nebo nastaví hodnotu určující, zda klávesové zkratky, které jsou přidružené k <xref:System.Windows.Forms.ToolStripMenuItem> se zobrazí vedle položky <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.MenuStrip> doprovodné třídy.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Představuje volitelnou možnost zobrazí na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Představuje místní nabídky.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne <xref:System.Windows.Forms.ToolStripDropDownButton> nebo vyšší úrovně položku nabídky.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Poskytuje základní funkce pro ovládací prvky je odvozena z <xref:System.Windows.Forms.ToolStripItem> , který zobrazí rozevírací seznam položek při kliknutí na.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
