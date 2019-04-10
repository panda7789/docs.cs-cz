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
ms.openlocfilehash: fdd3a56ab9a267990bb0e832c0d4cc2af9334034
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214037"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Postupy: Přístup ke kolekcím s klíči ve Windows Forms
-   Jednotlivé kolekce položek můžete přistupovat pomocí klíče. Tato funkce byla přidána k mnoha třídy kolekcí, které jsou obvykle používány aplikací modelu Windows Forms. V následujícím seznamu jsou uvedeny některé třídy kolekcí, které mají přístupné kolekce s klíči:  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klíč přidružený k položce v kolekci je obvykle název položky. Následující postupy ukazují, jak provádět běžné úlohy pomocí třídy kolekcí.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Najít a fokus se přesune na ovládací prvek vnořené v kolekci ovládací prvek  
  
-   Použití <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> a <xref:System.Windows.Forms.Control.Focus%2A> metody k zadání názvu najít a fokus se přesune do ovládacího prvku.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Pro přístup k obrazu v kolekci obrázků  
  
-   Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> vlastnosti a určit název image, které chcete získat přístup.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Nastavení stránky karty jako vybraná karta  
  
-   Použití <xref:System.Windows.Forms.TabControl.SelectedTab%2A> vlastnost spolu s <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> vlastnosti a určit název stránky karty jako vybraná karta nastavení.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
