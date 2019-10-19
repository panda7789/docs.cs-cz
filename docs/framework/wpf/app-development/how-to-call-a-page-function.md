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
ms.openlocfilehash: f170977860a73d339f2d83bc43992e6e2bc4053f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582050"
---
# <a name="how-to-call-a-page-function"></a><span data-ttu-id="b5d2b-102">Postupy: Volání funkce stránky</span><span class="sxs-lookup"><span data-stu-id="b5d2b-102">How to: Call a Page Function</span></span>
<span data-ttu-id="b5d2b-103">Tento příklad ukazuje, jak zavolat funkci stránky ze stránky [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5d2b-103">This example shows how to call a page function from a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5d2b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5d2b-104">Example</span></span>  
 <span data-ttu-id="b5d2b-105">Můžete přejít na funkci stránky pomocí identifikátoru URI (Uniform Resource Identifier), stejně jako při přechodu na stránku.</span><span class="sxs-lookup"><span data-stu-id="b5d2b-105">You can navigate to a page function using a uniform resource identifier (URI), just as you can when you navigate to a page.</span></span> <span data-ttu-id="b5d2b-106">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b5d2b-106">This is shown in the following example.</span></span>  
  
 [!code-csharp[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#navigatetoapagefunctionlikeapagecodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#NavigateToAPageFunctionLikeAPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#navigatetoapagefunctionlikeapagecodebehind)]  
  
 <span data-ttu-id="b5d2b-107">Pokud potřebujete předat data funkci stránky, můžete vytvořit její instanci a předat data nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b5d2b-107">If you need to pass data to the page function, you can create an instance of it and pass the data by setting a property.</span></span> <span data-ttu-id="b5d2b-108">Nebo, jak ukazuje následující příklad, můžete předat data pomocí konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="b5d2b-108">Or, as the following example shows, you can pass the data using a non-parameterless constructor.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#callapagefunctioncodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#CallAPageFunctionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#callapagefunctioncodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="b5d2b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5d2b-109">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
