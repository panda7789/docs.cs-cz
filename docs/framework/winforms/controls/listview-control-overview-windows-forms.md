---
title: "ListView – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda009beb429345d05aeba4e04f2ce1f07e627da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="listview-control-overview-windows-forms"></a>ListView – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListView> ovládací prvek zobrazí seznam položky s ikonami. Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je v pravém podokně Průzkumníka Windows. Ovládací prvek má čtyři režimy zobrazení: LargeIcon, SmallIcon, seznamu a podrobností.  
  
## <a name="what-you-can-do-with-the-listview-control"></a>Co můžete dělat pomocí ovládacího prvku ListView  
  
> [!NOTE]
>  Další zobrazení režimu, dlaždice, je dostupná pouze na systémy Windows XP a operační systém Windows Server 2003. Další informace najdete v tématu [postupy: povolení zobrazení Tile v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Režim LargeIcon zobrazí ikony. velké ikony vedle textu položky; Pokud ovládací prvek je dostatečně velké na to, zobrazí položky ve více sloupců. Režim SmallIcon je stejný, s tím rozdílem, že se zobrazí ikony. Malé ikony. Režim seznamu zobrazí ikony. Malé ikony, ale je vždy v jeden sloupec. Podrobnosti o režimu zobrazí položky v více sloupců. Podrobnosti najdete v tématu [postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md). Režim zobrazení je dáno <xref:System.Windows.Forms.ListView.View%2A> vlastnost. Všechny režimy zobrazení můžete zobrazit obrázky ze seznamů obrázků. Podrobnosti najdete v tématu [postupy: zobrazení ikon pro ovládací prvek Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Následující tabulka uvádí některé <xref:System.Windows.Forms.ListView> členy a zobrazení jsou platné v.  
  
|Člen ListView|Zobrazit|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A>Vlastnost|<xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A>Vlastnost|<xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>– Metoda|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A>Vlastnost|<xref:System.Windows.Forms.View.Details>nebo<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>události|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A>– Metoda|<xref:System.Windows.Forms.View.Details>, <xref:System.Windows.Forms.View.List>, nebo<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A>– Metoda|<xref:System.Windows.Forms.View.SmallIcon>nebo<xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A>– Metoda|<xref:System.Windows.Forms.View.Details>nebo<xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A>Vlastnost|Všechna zobrazení s výjimkou<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A>Vlastnost|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A>Vlastnost|<xref:System.Windows.Forms.View.LargeIcon>, <xref:System.Windows.Forms.View.SmallIcon>, nebo<xref:System.Windows.Forms.View.Tile>|  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.ListView> ovládací prvek je <xref:System.Windows.Forms.ListView.Items%2A>, který obsahuje položky zobrazené ovládacím prvkem. <xref:System.Windows.Forms.ListView.SelectedItems%2A> Vlastnost obsahuje kolekce položek v ovládacím prvku aktuálně vybranou. Uživatel může vybrat více položek, například přetáhnout několik položek najednou do jiného ovládacího prvku, pokud <xref:System.Windows.Forms.ListView.MultiSelect%2A> je nastavena na `true`. <xref:System.Windows.Forms.ListView> Řízení zobrazíte zaškrtnutí políček vedle položky, když <xref:System.Windows.Forms.ListView.CheckBoxes%2A> je nastavena na `true`.  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> Vlastnost určuje, jaký typ akce uživatel musí přijmout aktivovat položku v seznamu: možnosti <xref:System.Windows.Forms.ItemActivation.Standard>, <xref:System.Windows.Forms.ItemActivation.OneClick>, a <xref:System.Windows.Forms.ItemActivation.TwoClick>. <xref:System.Windows.Forms.ItemActivation.OneClick>Aktivace vyžaduje jedním kliknutím aktivujte položky. <xref:System.Windows.Forms.ItemActivation.TwoClick>Aktivace vyžaduje, aby uživatel k dvakrát klikněte na panel aktivace položky; jedním kliknutím změní barvu textu položky. <xref:System.Windows.Forms.ItemActivation.Standard>Aktivace vyžaduje, aby uživatel k dvakrát klikněte na položku aktivovat, ale položka nezmění vzhled.  
  
 <xref:System.Windows.Forms.ListView> Řízení také podporuje vizuální styly a další funkce, které jsou k dispozici na platformě Windows XP, včetně seskupení, zobrazení tile a značky pro vložení. Další informace najdete v tématu [funkce systému Windows XP a Windows Forms – ovládací prvky](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 [ListView – ovládací prvek](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Postupy: zobrazení ikon pro Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Postupy: vyberte položku v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [Postupy: seskupení položek v systému Windows Forms ListView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [Postupy: zobrazení značky vložení v ovládacím prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [Postupy: přidání schopností vyhledávání do ovládacího prvku ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Postupy: vytváření více podokny uživatelského rozhraní s Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
