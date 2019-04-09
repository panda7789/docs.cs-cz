---
title: 'Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: c1c59c3d4bb5d0d35103371575ebdd49d3559bbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108547"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView
Často při práci s velké seznam položek v <xref:System.Windows.Forms.ListView> ovládacího prvku, chcete nabízet možnosti vyhledávání pro uživatele. <xref:System.Windows.Forms.ListView> Ovládací prvek tato funkce nabízí dvěma různými způsoby: text párování a vyhledávání umístění.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Metoda vám umožňuje provádět textové vyhledávání na <xref:System.Windows.Forms.ListView> v zobrazení seznamu nebo podrobnosti daného vyhledávacího řetězce a volitelné počáteční a koncové indexu. Naproti tomu <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metoda umožňuje vyhledat položku v <xref:System.Windows.Forms.ListView> v ikony nebo dlaždici zobrazení, protože sada souřadnic x a y a směr hledání.  
  
### <a name="to-find-an-item-using-text"></a>Chcete-li najít položku pomocí textu  
  
1.  Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.ListView.View%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.Details> nebo <xref:System.Windows.Forms.View.List>a potom naplnit <xref:System.Windows.Forms.ListView> s položkami.  
  
2.  Volání <xref:System.Windows.Forms.ListView.FindItemWithText%2A> předejte text položky, které chcete najít.  
  
3.  Následující příklad kódu ukazuje, jak vytvořit základní <xref:System.Windows.Forms.ListView>, přidejte do ní položek a použití textové zadání od uživatele k vyhledání položky v seznamu.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Chcete-li najít položky pomocí souřadnic x a y  
  
1.  Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.View> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>a potom naplnit <xref:System.Windows.Forms.ListView> s položkami.  
  
2.  Volání <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metodu požadovanou souřadnic x a y- a směr, který chcete vyhledat.  
  
3.  Následující příklad kódu ukazuje, jak vytvořit základní ikonu <xref:System.Windows.Forms.ListView>, přidejte do ní položky a zachycení <xref:System.Windows.Forms.Control.MouseDown> událostí najít nejbližší položky směrem nahoru.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [ListView – ovládací prvek](listview-control-windows-forms.md)
- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
