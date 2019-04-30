---
title: 'Postupy: Odebrání všech doplňků pro úpravy z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770770"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="c1165-102">Postupy: Odebrání všech doplňků pro úpravy z elementu</span><span class="sxs-lookup"><span data-stu-id="c1165-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="c1165-103">Tento příklad ukazuje, jak prostřednictvím kódu programu odebrání všech doplňků z určeného <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c1165-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1165-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1165-104">Example</span></span>  
 <span data-ttu-id="c1165-105">Tento podrobný příklad odebere všechny ozdobného prvku v poli doplňků pro úpravy vrácený <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1165-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="c1165-106">V tomto příkladu dojde k načtení ozdobného prvku na <xref:System.Windows.UIElement> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="c1165-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="c1165-107">Pokud element zadána ve volání <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> doplňky nemá `null` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="c1165-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="c1165-108">Tento kód explicitně kontroluje pole s hodnotou null a je nejvhodnější pro aplikace, kde se očekává se poměrně běžnou pole s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c1165-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="c1165-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1165-109">Example</span></span>  
 <span data-ttu-id="c1165-110">Tento příklad zhuštěnému kód je funkčně srovnatelný s komentářem výše uvedený příklad.</span><span class="sxs-lookup"><span data-stu-id="c1165-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="c1165-111">Tento kód explicitně nekontroluje pro pole s hodnotou null, takže je možné, který <xref:System.NullReferenceException> může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c1165-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="c1165-112">Tento kód je nejvhodnější pro aplikace, kde se očekává pole null docházet zřídka.</span><span class="sxs-lookup"><span data-stu-id="c1165-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="c1165-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1165-113">See also</span></span>

- [<span data-ttu-id="c1165-114">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="c1165-114">Adorners Overview</span></span>](adorners-overview.md)
