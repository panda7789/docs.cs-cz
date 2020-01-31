---
title: 'Postupy: přístup ke kolekcím s klíčem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739623"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>Postupy: Přístup ke kolekcím s klíči ve Windows Forms

- Jednotlivé položky kolekce můžete přistupovat pomocí klíče. Tato funkce byla přidána do mnoha tříd kolekcí, které obvykle používá aplikace model Windows Forms. V následujícím seznamu jsou uvedeny některé třídy kolekce, které mají přístupné kolekce s klíčem:  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 Klíčem přidruženým k položce v kolekci je obvykle název položky. Následující postupy ukazují, jak používat třídy kolekcí k provádění běžných úloh.  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>Vyhledání a udělení fokusu vnořenému ovládacímu prvku v kolekci ovládacích prvků  
  
- Pomocí metod <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> a <xref:System.Windows.Forms.Control.Focus%2A> určete název ovládacího prvku, který se má najít a který se má zaměřit na.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>Přístup k obrázku v kolekci imagí  
  
- Pomocí vlastnosti <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> zadejte název bitové kopie, ke které chcete získat přístup.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>Nastavení stránky tabulátoru jako vybrané karty  
  
- Pomocí vlastnosti <xref:System.Windows.Forms.TabControl.SelectedTab%2A> spolu s vlastností <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> určete název stránky karty, která se má nastavit jako vybraná karta.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
