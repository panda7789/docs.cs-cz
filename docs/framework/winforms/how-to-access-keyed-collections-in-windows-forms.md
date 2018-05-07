---
title: 'Postupy: Přístup ke kolekcím s klíči ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 59e5cea29ee520b1f13f8fae98ae4042cc86fef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Postupy: Přístup ke kolekcím s klíči ve Windows Forms
-   Jednotlivé kolekce položek můžete přejít pomocí klíče. Tato funkce se přidal do mnoho kolekce tříd, které jsou obvykle používány formulářových aplikací Windows. Následující seznam uvádí některé z kolekce tříd, které mají přístupné kolekce s klíči:  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klíč přidružený položku v kolekci je obvykle název položky. Následující postupy ukazují, jak provádět běžné úlohy pomocí třídy kolekce.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>K vyhledání a fokus se vnořené ovládací prvek v kolekci ovládacího prvku  
  
-   Použití <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> a <xref:System.Windows.Forms.Control.Focus%2A> metody k zadání názvu k vyhledání a fokus se do ovládacího prvku.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Pro přístup k obrazu v kolekci bitové kopie  
  
-   Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> vlastnosti a určit název obrázku, kterému chcete přistupovat.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Nastavení stránky karty jako vybraná karta  
  
-   Použití <xref:System.Windows.Forms.TabControl.SelectedTab%2A> vlastnost společně s <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> vlastnosti a určit název stránky karty lze nastavit jako vybraná karta.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
