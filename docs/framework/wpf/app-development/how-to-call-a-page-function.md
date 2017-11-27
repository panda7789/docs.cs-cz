---
title: "Postupy: Volání funkce stránky"
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
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bc72b24b29a43e8aed073600ea863824c93ced6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="22e7c-102">Postupy: Volání funkce stránky</span><span class="sxs-lookup"><span data-stu-id="22e7c-102">How to: Call a Page Function</span></span>
<span data-ttu-id="22e7c-103">Tento příklad ukazuje, jak volat funkci stránky z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="22e7c-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e7c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="22e7c-104">Example</span></span>  
 <span data-ttu-id="22e7c-105">Můžete přejít na stránku pomocí funkce [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], stejným způsobem jako když přejdete na stránku.</span><span class="sxs-lookup"><span data-stu-id="22e7c-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="22e7c-106">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="22e7c-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="22e7c-107">Pokud potřebujete k předávání dat na stránce funkce, můžete vytvořit její instanci a předat data nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="22e7c-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="22e7c-108">Nebo, jak ukazuje následující příklad, můžete předat data pomocí jiné než výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="22e7c-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="22e7c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="22e7c-109">See Also</span></span>  
 <xref:System.Windows.Navigation.PageFunction%601>
