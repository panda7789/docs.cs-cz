---
title: "Postupy: Odebrání všech doplňků z elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9b69b9150e8d2c2938c53fcd47e72b7fcb6d238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="c85b1-102">Postupy: Odebrání všech doplňků z elementu</span><span class="sxs-lookup"><span data-stu-id="c85b1-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="c85b1-103">Tento příklad ukazuje, jak programově odebrat všechny ozdobného prvku ze zadané <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="c85b1-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c85b1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c85b1-104">Example</span></span>  
 <span data-ttu-id="c85b1-105">Tento příklad kódu podrobné odebere všechny ozdobného prvku v poli ozdobného prvku vrácený <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="c85b1-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="c85b1-106">V tomto příkladu se stane, načíst ozdobného prvku na <xref:System.Windows.UIElement> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="c85b1-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="c85b1-107">Pokud element zadané ve volání <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nemá žádné ozdobného prvku `null` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="c85b1-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="c85b1-108">Tento kód explicitně kontroluje pro pole hodnotu null a je nejvhodnější pro aplikace, kde je očekávána null pole relativně běžně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c85b1-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="c85b1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c85b1-109">Example</span></span>  
 <span data-ttu-id="c85b1-110">Tento příklad kódu zhuštěné je funkčně srovnatelný podrobné výše uvedený příklad.</span><span class="sxs-lookup"><span data-stu-id="c85b1-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="c85b1-111">Tento kód nekontroluje explicitně pro pole hodnotu null, takže je možné, <xref:System.NullReferenceException> může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c85b1-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="c85b1-112">Tento kód je nejvhodnější pro aplikace, kde null pole musí být výjimečných.</span><span class="sxs-lookup"><span data-stu-id="c85b1-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="c85b1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c85b1-113">See Also</span></span>  
 [<span data-ttu-id="c85b1-114">Přehled ozdobného prvku</span><span class="sxs-lookup"><span data-stu-id="c85b1-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
