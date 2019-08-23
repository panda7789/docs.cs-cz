---
title: MainMenu – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952138"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
> I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Komponenta model Windows Forms <xref:System.Windows.Forms.MainMenu> zobrazuje v době běhu nabídku. Všechny podnabídky hlavní nabídky a jednotlivé položky jsou <xref:System.Windows.Forms.MenuItem> objekty.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Položka nabídky může být označena jako výchozí položka <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> nastavením vlastnosti na. `true` Výchozí položka se při kliknutí na nabídku zobrazí tučným textem. <xref:System.Windows.Forms.MenuItem.Checked%2A> Vlastnost položky nabídky je buď `true` nebo `false`, a označuje, zda je vybrána položka nabídky. <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> Vlastnost položky nabídky přizpůsobí vzhled vybrané položky: je-li <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> parametr nastaven na `true`hodnotu, zobrazí se vedle položky přepínač. Pokud <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `false`hodnotu, zobrazí se vedle položky značka zaškrtnutí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
