---
title: MenuStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733462"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip – přehled ovládacího prvku (Windows Forms)
Nabídky pro uživatele zpřístupňují funkce, které jsou seskupeny podle společného motivu.  
  
 <xref:System.Windows.Forms.MenuStrip> Ovládací prvek byl představen ve verzi 2,0 .NET Framework. <xref:System.Windows.Forms.MenuStrip> Pomocí ovládacího prvku můžete snadno vytvářet nabídky, jako jsou ty, které se nacházejí v systém Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Ovládací prvek podporuje rozhraní MDI (Multiple Document Interface) a slučování nabídek, popisy nástrojů a přetečení. Přidáním přístupových klíčů, klávesových zkratek, značek zaškrtnutí, obrázků a oddělovacích pruhů můžete vylepšit použitelnost a čitelnost vašich nabídek.  
  
 Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.MainMenu> ovládacímu prvku. ovládací prvek však <xref:System.Windows.Forms.MainMenu> zůstává zachován z důvodu zpětné kompatibility a budoucího použití, pokud zvolíte. <xref:System.Windows.Forms.MenuStrip>  
  
## <a name="ways-to-use-the-menustrip-control"></a>Způsoby použití ovládacího prvku MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> Použijte ovládací prvek pro:  
  
- Vytvářejte snadno přizpůsobené, běžně používané nabídky, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například řazení textu a obrázků a zarovnání, operace přetažení, MDI, přetečení a alternativní režimy přístupu k příkazům nabídky.  
  
- Podporuje typický vzhled a chování operačního systému.  
  
- Zpracování událostí konzistentně pro všechny kontejnery a obsažené položky ve stejném způsobu, jakým se zpracovávají události pro jiné ovládací prvky.  
  
 V následující tabulce jsou uvedeny některé zvláště důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a přidružené třídy.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem> hodnotu, která se používá k zobrazení seznamu podřízených formulářů MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Získá nebo nastaví způsob, jakým jsou podřízené nabídky sloučeny s nadřazenými nabídkami v aplikacích MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Získá nebo nastaví pozici sloučené položky v rámci nabídky v aplikacích MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Získá nebo nastaví hodnotu označující, zda je formulář kontejner pro podřízené formuláře MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Získává nebo nastavuje hodnotu, která indikuje, jestli se zobrazují popisy nástrojů <xref:System.Windows.Forms.MenuStrip>pro.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Získá nebo nastaví hodnotu označující, jestli je <xref:System.Windows.Forms.MenuStrip> podporovaná funkce přetečení.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Získá nebo nastaví klávesové zkratky spojené s <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Získává nebo nastavuje hodnotu, která označuje, jestli se vedle pole <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripMenuItem>zobrazí klávesové zkratky, které jsou přidružené k.|  
  
 V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.MenuStrip> doprovodné třídy.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Představuje možnost s možností volby, která se <xref:System.Windows.Forms.MenuStrip> zobrazí <xref:System.Windows.Forms.ContextMenuStrip>na nebo.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Představuje místní nabídku.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne na <xref:System.Windows.Forms.ToolStripDropDownButton> položku nabídky nebo na vyšší úroveň.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Poskytuje základní funkce pro ovládací prvky odvozené <xref:System.Windows.Forms.ToolStripItem> z těchto zobrazených rozevíracích položek při kliknutí.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
