---
title: "Postupy: Odebrání doplňku z elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20d17ef43f99f6815334c0acbf7eb2040959751e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="09a6c-102">Postupy: Odebrání doplňku z elementu</span><span class="sxs-lookup"><span data-stu-id="09a6c-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="09a6c-103">Tento příklad ukazuje, jak programově odebrat konkrétní adorner ze zadané <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="09a6c-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09a6c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="09a6c-104">Example</span></span>  
 <span data-ttu-id="09a6c-105">Tento příklad kódu podrobné Odebere první adorner v poli ozdobného prvku vrácený <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span><span class="sxs-lookup"><span data-stu-id="09a6c-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="09a6c-106">V tomto příkladu se stane, načíst ozdobného prvku na <xref:System.Windows.UIElement> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="09a6c-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="09a6c-107">Pokud element zadané ve volání <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nemá žádné ozdobného prvku `null` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="09a6c-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="09a6c-108">Tento kód explicitně kontroluje pro pole hodnotu null a je nejvhodnější pro aplikace, kde je očekávána null pole relativně běžně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="09a6c-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="09a6c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="09a6c-109">Example</span></span>  
 <span data-ttu-id="09a6c-110">Tento příklad kódu zhuštěné je funkčně srovnatelný podrobné výše uvedený příklad.</span><span class="sxs-lookup"><span data-stu-id="09a6c-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="09a6c-111">Tento kód nekontroluje explicitně pro pole hodnotu null, takže je možné, <xref:System.NullReferenceException> může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="09a6c-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="09a6c-112">Tento kód je nejvhodnější pro aplikace, kde null pole musí být výjimečných.</span><span class="sxs-lookup"><span data-stu-id="09a6c-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="09a6c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="09a6c-113">See Also</span></span>  
 [<span data-ttu-id="09a6c-114">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="09a6c-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
