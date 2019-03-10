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
ms.openlocfilehash: d62c0081c128693861a9fd21360f09f65d485a79
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709774"
---
# <a name="listview-control-overview-windows-forms"></a>ListView – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek zobrazuje seznam položek s ikonami. Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je pravém podokně Průzkumníka Windows. Ovládací prvek má čtyři režimy zobrazení: Zobrazení LargeIcon, SmallIcon, seznamu a podrobností.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co můžete dělat pomocí ovládacího prvku ListView  
  
> [!NOTE]
>  Další zobrazení režimu, dlaždice, je dostupná pouze na Windows XP a operační systém Windows Server 2003. Další informace najdete v tématu [jak: Povolení zobrazení Tile v Windows Forms ovládací prvek ListView](how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Režim zobrazení LargeIcon zobrazuje velké ikony vedle textu položky. položky se zobrazí ve více sloupcích, pokud ovládací prvek je příliš velká. Režimem SmallIcon. je stejná s tím rozdílem, že zobrazuje malé ikony. Režim seznamu malé ikony se zobrazí, ale je vždy v jednom sloupci. Podrobnosti o režimu zobrazí položky ve více sloupcích. Podrobnosti najdete v tématu [jak: Přidání sloupce, které chcete Windows Forms ovládací prvek ListView](how-to-add-columns-to-the-windows-forms-listview-control.md). Režim zobrazení je určeno <xref:System.Windows.Forms.ListView.View%2A> vlastnost. Všechny režimy zobrazení můžete zobrazit obrázky ze seznamů obrázků. Podrobnosti najdete v tématu [jak: Zobrazení ikon pro Windows Forms ovládací prvek ListView](how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 V následující tabulce jsou uvedeny některé <xref:System.Windows.Forms.ListView> členy a jsou platné v zobrazení.  
  
|Člen ListView|Zobrazit|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> Vlastnost|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> Vlastnost|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> – Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> Vlastnost|<xref:System.Windows.Forms.View.Details> Nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> Události|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> – Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> – Metoda|<xref:System.Windows.Forms.View.SmallIcon> Nebo <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> – Metoda|<xref:System.Windows.Forms.View.Details> Nebo <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> Vlastnost|Všechna zobrazení s výjimkou <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> Vlastnost|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> Vlastnost|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, nebo <xref:System.Windows.Forms.View.Tile>|  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.ListView> je ovládací prvek <xref:System.Windows.Forms.ListView.Items%2A>, který obsahuje položky zobrazené ovládacím prvkem. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Vlastnost obsahuje kolekci položek aktuálně vybraného v ovládacím prvku. Uživatel může vybrat více položek, například přetažení několik položek najednou k jinému ovládacímu prvku, pokud <xref:System.Windows.Forms.ListView.MultiSelect%2A> je nastavena na `true`. <xref:System.Windows.Forms.ListView> Ovládací prvek mohl zobrazit zaškrtávací políčka vedle položek, pokud <xref:System.Windows.Forms.ListView.CheckBoxes%2A> je nastavena na `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Vlastnost určuje, jaký typ akce, musí uživatel provést k aktivaci položky v seznamu: možnosti jsou <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, a <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick> Aktivace vyžaduje jedním kliknutím k aktivaci položky. <xref:System.Windows.Forms.ItemActivation.TwoClick> Aktivace vyžaduje, aby uživatel dvakrát kliknout na aktivaci položky; jediným kliknutím změní barvu textu položky. <xref:System.Windows.Forms.ItemActivation.Standard> Aktivace vyžaduje, aby uživatel dvakrát kliknout na aktivovat položku, ale položka nedojde ke změně vzhledu.  
  
 <xref:System.Windows.Forms.ListView> Ovládací prvek podporuje také vizuálních stylů a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení tile a značky pro vložení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- [Ovládací prvek ListView](listview-control-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
- [Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](how-to-add-search-capabilities-to-a-listview-control.md)
- [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms](how-to-create-a-multipane-user-interface-with-windows-forms.md)
