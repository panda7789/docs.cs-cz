---
title: 'Postupy: Přejděte na stránku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: a5a0e7a8e7effac7c51f4dee92d30de56d60d90c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369333"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="a4f67-102">Postupy: Přejděte na stránku</span><span class="sxs-lookup"><span data-stu-id="a4f67-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="a4f67-103">Tento příklad ukazuje několik způsobů, jimiž stránku se dá Navigovat z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="a4f67-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f67-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4f67-104">Example</span></span>  
 <span data-ttu-id="a4f67-105">Je možné, <xref:System.Windows.Navigation.NavigationWindow> přejít na stránku pomocí jedné z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a4f67-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="a4f67-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a4f67-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="a4f67-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metody.</span><span class="sxs-lookup"><span data-stu-id="a4f67-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] <span data-ttu-id="a4f67-108">může být relativní nebo absolutní.</span><span class="sxs-lookup"><span data-stu-id="a4f67-108">can be either relative or absolute.</span></span> <span data-ttu-id="a4f67-109">Další informace najdete v tématu [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a4f67-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f67-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4f67-110">See also</span></span>
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
