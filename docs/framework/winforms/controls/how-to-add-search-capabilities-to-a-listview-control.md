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
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="90e65-102">Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="90e65-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="90e65-103">Často při práci s velké seznam položek v <xref:System.Windows.Forms.ListView> ovládacího prvku, chcete nabízet možnosti vyhledávání pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="90e65-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="90e65-104"><xref:System.Windows.Forms.ListView> Ovládací prvek tato funkce nabízí dvěma různými způsoby: text párování a vyhledávání umístění.</span><span class="sxs-lookup"><span data-stu-id="90e65-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="90e65-105"><xref:System.Windows.Forms.ListView.FindItemWithText%2A> Metoda vám umožňuje provádět textové vyhledávání na <xref:System.Windows.Forms.ListView> v zobrazení seznamu nebo podrobnosti daného vyhledávacího řetězce a volitelné počáteční a koncové indexu.</span><span class="sxs-lookup"><span data-stu-id="90e65-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="90e65-106">Naproti tomu <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metoda umožňuje vyhledat položku v <xref:System.Windows.Forms.ListView> v ikony nebo dlaždici zobrazení, protože sada souřadnic x a y a směr hledání.</span><span class="sxs-lookup"><span data-stu-id="90e65-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="90e65-107">Chcete-li najít položku pomocí textu</span><span class="sxs-lookup"><span data-stu-id="90e65-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="90e65-108">Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.ListView.View%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.Details> nebo <xref:System.Windows.Forms.View.List>a potom naplnit <xref:System.Windows.Forms.ListView> s položkami.</span><span class="sxs-lookup"><span data-stu-id="90e65-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="90e65-109">Volání <xref:System.Windows.Forms.ListView.FindItemWithText%2A> předejte text položky, které chcete najít.</span><span class="sxs-lookup"><span data-stu-id="90e65-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="90e65-110">Následující příklad kódu ukazuje, jak vytvořit základní <xref:System.Windows.Forms.ListView>, přidejte do ní položek a použití textové zadání od uživatele k vyhledání položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="90e65-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="90e65-111">Chcete-li najít položky pomocí souřadnic x a y</span><span class="sxs-lookup"><span data-stu-id="90e65-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="90e65-112">Vytvoření <xref:System.Windows.Forms.ListView> s <xref:System.Windows.Forms.View> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.View.SmallIcon> nebo <xref:System.Windows.Forms.View.LargeIcon>a potom naplnit <xref:System.Windows.Forms.ListView> s položkami.</span><span class="sxs-lookup"><span data-stu-id="90e65-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="90e65-113">Volání <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metodu požadovanou souřadnic x a y- a směr, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="90e65-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="90e65-114">Následující příklad kódu ukazuje, jak vytvořit základní ikonu <xref:System.Windows.Forms.ListView>, přidejte do ní položky a zachycení <xref:System.Windows.Forms.Control.MouseDown> událostí najít nejbližší položky směrem nahoru.</span><span class="sxs-lookup"><span data-stu-id="90e65-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="90e65-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90e65-115">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [<span data-ttu-id="90e65-116">ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="90e65-116">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="90e65-117">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="90e65-117">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="90e65-118">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="90e65-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
