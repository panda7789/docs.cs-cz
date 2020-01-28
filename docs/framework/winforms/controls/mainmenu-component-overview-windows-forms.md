---
title: Přehled komponenty MainMenu
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745111"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
> I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Komponenta model Windows Forms <xref:System.Windows.Forms.MainMenu> zobrazí v době běhu nabídku. Všechny podnabídky hlavní nabídky a jednotlivé položky jsou <xref:System.Windows.Forms.MenuItem> objekty.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Položka nabídky se dá určit jako výchozí položka nastavením vlastnosti <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> na `true`. Výchozí položka se při kliknutí na nabídku zobrazí tučným textem. Vlastnost <xref:System.Windows.Forms.MenuItem.Checked%2A> položky nabídky je buď `true` nebo `false`, a označuje, zda je vybrána položka nabídky. Vlastnost <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> položky nabídky přizpůsobí vzhled vybrané položky: je-li <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> nastavena na `true`, zobrazí se vedle položky přepínač. Pokud je <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> nastaveno na `false`, vedle položky se zobrazí označení zaškrtnutí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
