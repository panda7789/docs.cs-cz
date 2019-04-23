---
title: 'Postupy: Volání funkce stránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- calling page functions [WPF]
- page functions [WPF], calling
- functions [WPF], calling
ms.assetid: a4808397-c6d5-406a-83e0-0091f0c15ae4
ms.openlocfilehash: fb58d50a63cca41420aa102ca0c8b63f3b14c0d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980184"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="c4b33-102">Postupy: Volání funkce stránky</span><span class="sxs-lookup"><span data-stu-id="c4b33-102">How to: Call a Page Function</span></span>
<span data-ttu-id="c4b33-103">Tento příklad ukazuje, jak volat z funkce stránky [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="c4b33-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b33-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4b33-104">Example</span></span>  
 <span data-ttu-id="c4b33-105">Můžete přejít na stránku pomocí funkce [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], stejně jako když přejdete na stránku.</span><span class="sxs-lookup"><span data-stu-id="c4b33-105">You can navigate to a page function using a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], just as you can when you navigate to a page.</span></span> <span data-ttu-id="c4b33-106">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c4b33-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="c4b33-107">Pokud je potřeba předat data do funkce stránky, můžete vytvořit její instanci a předejte data tak, že nastavíte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c4b33-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="c4b33-108">Nebo, jak ukazuje následující příklad, můžete předat data pomocí jiného než výchozího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4b33-108">Or, as the following example shows, you can pass the data using a non-default constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="c4b33-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4b33-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
