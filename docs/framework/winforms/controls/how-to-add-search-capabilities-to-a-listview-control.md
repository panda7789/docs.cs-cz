---
title: 'Postupy: Přidání schopností vyhledávání do prvku ListView'
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
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Postupy: Přidání schopností vyhledávání do prvku ListView
Často při práci s velké položek v seznamu <xref:System.Windows.Forms.ListView> ovládací prvek, můžete chtít nabízet možnosti vyhledávání pro uživatele. <xref:System.Windows.Forms.ListView> Řízení nabízí tato funkce dvěma různými způsoby: porovnávání text a hledání umístění.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Metoda umožňuje provádět fulltextové vyhledávání na <xref:System.Windows.Forms.ListView> v zobrazení seznamu nebo podrobnosti, zadaný hledaný řetězec a volitelné počáteční a koncovou index. Naproti tomu <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metoda umožňuje vyhledat položku v <xref:System.Windows.Forms.ListView> v zobrazení ikony nebo dlaždice danou sadu souřadnice x a y a směr pro vyhledávání.  
  
### <a name="to-find-an-item-using-text"></a>Najít položku pomocí textu  
  
1.  Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.ListView.View%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.Details> nebo <xref:System.Windows.Forms.View.List>a pak naplnit <xref:System.Windows.Forms.ListView> s položkami.  
  
2.  Volání <xref:System.Windows.Forms.ListView.FindItemWithText%2A> metodu předáním text položky, kterou chcete najít.  
  
3.  Následující příklad kódu ukazuje, jak vytvořit základní <xref:System.Windows.Forms.ListView>, jeho naplnění položek a použití text vstup od uživatele k vyhledání položky v seznamu.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Chcete-li najít položku pomocí souřadnic x a y  
  
1.  Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.View> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>a pak naplnit <xref:System.Windows.Forms.ListView> s položkami.  
  
2.  Volání <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metodu předáním požadovanou souřadnic x a y- a směr chcete hledat.  
  
3.  Následující příklad kódu ukazuje, jak vytvořit základní ikonu <xref:System.Windows.Forms.ListView>, jeho naplnění položek a zachycení <xref:System.Windows.Forms.Control.MouseDown> událostí najít nejbližší položky v aktuálním směru.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [Ovládací prvek ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Přehled ovládacího prvku ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
