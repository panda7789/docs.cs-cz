---
title: ListView – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952154"
---
# <a name="listview-control-overview-windows-forms"></a>ListView – přehled ovládacího prvku (Windows Forms)
Ovládací prvek <xref:System.Windows.Forms.ListView> model Windows Forms zobrazí seznam položek s ikonami. Pomocí zobrazení seznamu můžete vytvořit uživatelské rozhraní, jako je například pravé podokno Průzkumníka Windows. Ovládací prvek má čtyři režimy zobrazení: Zobrazení LargeIcon, SmallIcon, list a details.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co se dá dělat s ovládacím prvkem ListView  
  
> [!NOTE]
> Další režim zobrazení, dlaždice, je k dispozici pouze v operačním systému Windows XP a Windows Server 2003. Další informace najdete v tématu [jak: Povolí zobrazení dlaždic v ovládacím prvku](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)model Windows Forms ListView.  
  
 Režim zobrazení LargeIcon zobrazuje velké ikony vedle textu položky; Pokud je ovládací prvek dostatečně velký, zobrazí se položky ve více sloupcích. Režim SmallIcon je stejný s tím rozdílem, že zobrazuje malé ikony. V režimu seznamu se zobrazí malé ikony, ale vždy se nachází v jednom sloupci. V režimu podrobností se zobrazí položky ve více sloupcích. Podrobnosti najdete v tématu [How to: Přidejte sloupce do ovládacího prvku](how-to-add-columns-to-the-windows-forms-listview-control.md)model Windows Forms ListView. Režim zobrazení je určen <xref:System.Windows.Forms.ListView.View%2A> vlastností. Všechny režimy zobrazení mohou zobrazovat obrázky ze seznamů obrázků. Podrobnosti najdete v tématu [How to: Zobrazí ikony pro ovládací prvek](how-to-display-icons-for-the-windows-forms-listview-control.md)model Windows Forms ListView.  
  
 V následující tabulce jsou uvedeny některé <xref:System.Windows.Forms.ListView> členy a zobrazení, která jsou v nástroji platná.  
  
|Člen ListView|Zobrazit|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>majetek|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>majetek|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>majetek|<xref:System.Windows.Forms.View.Details> Nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>událostí|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>nebo<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>Metoda|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>Metoda|<xref:System.Windows.Forms.View.Details> Nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>majetek|Všechna zobrazení kromě<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>majetek|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>majetek|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.Tile>|  
  
 Klíčovou vlastností <xref:System.Windows.Forms.ListView> ovládacího prvku je <xref:System.Windows.Forms.ListView.Items%2A>, který obsahuje položky zobrazené ovládacím prvkem. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Vlastnost obsahuje kolekci položek, které jsou aktuálně vybrány v ovládacím prvku. Uživatel může vybrat více položek, například pro přetahování několika položek v čase na jiný ovládací prvek, pokud <xref:System.Windows.Forms.ListView.MultiSelect%2A> je vlastnost nastavena na `true`hodnotu. Ovládací prvek může zobrazit zaškrtávací políčka vedle položek, <xref:System.Windows.Forms.ListView.CheckBoxes%2A> Pokud je vlastnost nastavena na `true`hodnotu. <xref:System.Windows.Forms.ListView>  
  
 Vlastnost určuje, jaký typ akce musí uživatel provést, aby se aktivovala položka v seznamu: možnosti jsou <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>a <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ListView.Activation%2A> <xref:System.Windows.Forms.ItemActivation.OneClick>Aktivace vyžaduje, abyste položku aktivovali jediným kliknutím. <xref:System.Windows.Forms.ItemActivation.TwoClick>Aktivace vyžaduje, aby uživatel poklikáním aktivoval položku. jediným kliknutím se změní barva textu položky. <xref:System.Windows.Forms.ItemActivation.Standard>Aktivace vyžaduje, aby uživatel poklikáním aktivoval položku, ale nezměnil vzhled položky.  
  
 <xref:System.Windows.Forms.ListView> Ovládací prvek také podporuje vizuální styly a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení dlaždic a značek vložení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku model Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit ikony pro ovládací prvek model Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit podpoložky ve sloupcích s ovládacím prvkem model Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Vybrat položku v ovládacím prvku model Windows Forms ListView](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Postupy: Seskupení položek v ovládacím prvku ListView model Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Postupy: Zobrazit značku vložení v ovládacím prvku model Windows Forms ListView](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Postupy: Vytvoření uživatelského rozhraní s více podokny pomocí model Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
