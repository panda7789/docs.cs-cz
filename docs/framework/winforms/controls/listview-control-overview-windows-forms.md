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
ms.openlocfilehash: ab2d0d9456f64f215ddbc0003833db1858f0ce1a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208680"
---
# <a name="listview-control-overview-windows-forms"></a>ListView – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek zobrazuje seznam položek s ikonami. Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je pravém podokně Průzkumníka Windows. Ovládací prvek má čtyři režimy zobrazení: zobrazení LargeIcon, SmallIcon, seznam a podrobnosti.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co můžete dělat pomocí ovládacího prvku ListView  
  
> [!NOTE]
>  Další zobrazení režimu, dlaždice, je dostupná pouze na Windows XP a operační systém Windows Server 2003. Další informace najdete v tématu [postupy: povolení zobrazení Tile v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Režim zobrazení LargeIcon zobrazuje velké ikony vedle textu položky. položky se zobrazí ve více sloupcích, pokud ovládací prvek je příliš velká. Režimem SmallIcon. je stejná s tím rozdílem, že zobrazuje malé ikony. Režim seznamu malé ikony se zobrazí, ale je vždy v jednom sloupci. Podrobnosti o režimu zobrazí položky ve více sloupcích. Podrobnosti najdete v tématu [postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Režim zobrazení je určeno <xref:System.Windows.Forms.ListView.View%2A> vlastnost. Všechny režimy zobrazení můžete zobrazit obrázky ze seznamů obrázků. Podrobnosti najdete v tématu [postupy: zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
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
  
 <xref:System.Windows.Forms.ListView> Ovládací prvek podporuje také vizuálních stylů a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení tile a značky pro vložení. Další informace najdete v tématu [funkce Windows XP a ovládací prvky Windows Forms](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Postupy: Výběr položky v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
