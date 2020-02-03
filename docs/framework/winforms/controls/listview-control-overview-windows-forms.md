---
title: Přehled ovládacího prvku ListView
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 9308ff6646704d16b32669827a1f26bebf6958d8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745154"
---
# <a name="listview-control-overview-windows-forms"></a>ListView – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> zobrazí seznam položek s ikonami. Pomocí zobrazení seznamu můžete vytvořit uživatelské rozhraní, jako je například pravé podokno Průzkumníka Windows. Ovládací prvek má čtyři režimy zobrazení: zobrazení LargeIcon, SmallIcon, list a detail.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co se dá dělat s ovládacím prvkem ListView  
  
> [!NOTE]
> Další režim zobrazení, dlaždice, je k dispozici pouze v operačním systému Windows XP a Windows Server 2003. Další informace najdete v tématu [Postup: povolení zobrazení dlaždic v ovládacím prvku ListView model Windows Forms](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Režim zobrazení LargeIcon zobrazuje velké ikony vedle textu položky; Pokud je ovládací prvek dostatečně velký, zobrazí se položky ve více sloupcích. Režim SmallIcon je stejný s tím rozdílem, že zobrazuje malé ikony. V režimu seznamu se zobrazí malé ikony, ale vždy se nachází v jednom sloupci. V režimu podrobností se zobrazí položky ve více sloupcích. Podrobnosti najdete v tématu [Postup: Přidání sloupců do ovládacího prvku model Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md). Režim zobrazení je určený vlastností <xref:System.Windows.Forms.ListView.View%2A>. Všechny režimy zobrazení mohou zobrazovat obrázky ze seznamů obrázků. Podrobnosti najdete v tématu [Postup: zobrazení ikon pro ovládací prvek model Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Následující tabulka uvádí některé z <xref:System.Windows.Forms.ListView> členů a zobrazení, která jsou platná v.  
  
|Člen ListView|Zobrazení|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> – vlastnost|<xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> – vlastnost|<xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> – metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> – vlastnost|<xref:System.Windows.Forms.View.Details> nebo <xref:System.Windows.Forms.View.Tile>|  
|událost <xref:System.Windows.Forms.ListView.DrawSubItem>|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> – metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> – metoda|<xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> – metoda|<xref:System.Windows.Forms.View.Details> nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> – vlastnost|Všechna zobrazení kromě <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> – vlastnost|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> – vlastnost|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>nebo <xref:System.Windows.Forms.View.Tile>|  
  
 Vlastnost Key ovládacího prvku <xref:System.Windows.Forms.ListView> je <xref:System.Windows.Forms.ListView.Items%2A>, která obsahuje položky zobrazené ovládacím prvkem. Vlastnost <xref:System.Windows.Forms.ListView.SelectedItems%2A> obsahuje kolekci položek, které jsou aktuálně vybrány v ovládacím prvku. Uživatel může vybrat více položek, například pro přetahování několika položek současně na jiný ovládací prvek, pokud je vlastnost <xref:System.Windows.Forms.ListView.MultiSelect%2A> nastavena na hodnotu `true`. Ovládací prvek <xref:System.Windows.Forms.ListView> může zobrazit zaškrtávací políčka vedle položek, pokud je vlastnost <xref:System.Windows.Forms.ListView.CheckBoxes%2A> nastavena na `true`.  
  
 Vlastnost <xref:System.Windows.Forms.ListView.Activation%2A> určuje, jaký typ akce musí uživatel provést při aktivaci položky v seznamu: možnosti jsou <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>a <xref:System.Windows.Forms.ItemActivation.TwoClick>. Aktivace <xref:System.Windows.Forms.ItemActivation.OneClick> vyžaduje, abyste položku aktivovali jediným kliknutím. Aktivace <xref:System.Windows.Forms.ItemActivation.TwoClick> vyžaduje, aby uživatel mohl položku aktivovat dvakrát kliknutím. jediným kliknutím se změní barva textu položky. Aktivace <xref:System.Windows.Forms.ItemActivation.Standard> vyžaduje, aby uživatel poklepal na aktivaci položky, ale položka se nezmění.  
  
 Ovládací prvek <xref:System.Windows.Forms.ListView> také podporuje vizuální styly a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení dlaždic a značek vložení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Výběr položky v ovládacím prvku Windows Forms ListView](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
