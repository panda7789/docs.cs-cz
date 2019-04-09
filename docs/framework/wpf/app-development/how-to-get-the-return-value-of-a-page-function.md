---
title: 'Postupy: Načtení návratové hodnoty funkce stránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- functions [WPF], getting return values of
- page functions [WPF], getting return values of
- return values of page functions [WPF]
- getting [WPF], return values of page functions
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
ms.openlocfilehash: 054ffe16690425e118fcac481b2a5ff63f9450f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125065"
---
# <a name="how-to-get-the-return-value-of-a-page-function"></a><span data-ttu-id="4763b-102">Postupy: Načtení návratové hodnoty funkce stránky</span><span class="sxs-lookup"><span data-stu-id="4763b-102">How to: Get the Return Value of a Page Function</span></span>
<span data-ttu-id="4763b-103">Tento příklad ukazuje, jak získat výsledek, který je vrácen funkce stránky.</span><span class="sxs-lookup"><span data-stu-id="4763b-103">This example shows how to get the result that is returned by a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4763b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4763b-104">Example</span></span>  
 <span data-ttu-id="4763b-105">K získání výsledku, který je vrácen z funkce stránky, je potřeba zpracovat <xref:System.Windows.Navigation.PageFunction%601.Return> se označuje jako volání funkce stránky.</span><span class="sxs-lookup"><span data-stu-id="4763b-105">To get the result that is returned from a page function, you need to handle <xref:System.Windows.Navigation.PageFunction%601.Return> of the page function you are calling.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="4763b-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4763b-106">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
