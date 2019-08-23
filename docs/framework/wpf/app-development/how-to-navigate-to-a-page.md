---
title: 'Postupy: Přechod na stránku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 38814268c9bb271ad3d88d549fb6ec4c6cbfed40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966032"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="3b2eb-102">Postupy: Přechod na stránku</span><span class="sxs-lookup"><span data-stu-id="3b2eb-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="3b2eb-103">Tento příklad znázorňuje několik způsobů, jak lze na stránku přejít z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="3b2eb-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b2eb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b2eb-104">Example</span></span>  
 <span data-ttu-id="3b2eb-105">Může <xref:System.Windows.Navigation.NavigationWindow> přejít na stránku pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="3b2eb-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
- <span data-ttu-id="3b2eb-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> Vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3b2eb-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
- <span data-ttu-id="3b2eb-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3b2eb-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]<span data-ttu-id="3b2eb-108">může být buď relativní, nebo absolutní.</span><span class="sxs-lookup"><span data-stu-id="3b2eb-108">can be either relative or absolute.</span></span> <span data-ttu-id="3b2eb-109">Další informace najdete v tématu [identifikátory URI Pack v](pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="3b2eb-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2eb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b2eb-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
