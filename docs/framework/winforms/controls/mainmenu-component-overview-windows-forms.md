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
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168477"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> komponenty zobrazí nabídku v době běhu. Všechny dílčích nabídek z hlavní nabídky a jednotlivé položky <xref:System.Windows.Forms.MenuItem> objekty.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Položka nabídky lze označit jako výchozí položku tak, že nastavíte <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> vlastnost `true`. Výchozí položka se zobrazí tučně, když dojde ke kliknutí na nabídky. Položka nabídky <xref:System.Windows.Forms.MenuItem.Checked%2A> vlastnost je buď `true` nebo `false`a označuje, zda je vybrána položka nabídky. Položka nabídky <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> vlastnost přizpůsobí vzhledu vybrané položky: Pokud <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `true`, přepínač se zobrazí vedle položky; v případě <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `false`, se zobrazí zaškrtávací políčko vedle položky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
