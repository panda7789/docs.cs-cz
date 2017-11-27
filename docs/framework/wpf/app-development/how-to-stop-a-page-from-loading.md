---
title: "Postupy: Zastavit načítání stránky"
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
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b68936ed83a61fc6d4c80408bd055c0eb05e030d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-stop-a-page-from-loading"></a><span data-ttu-id="f0daf-102">Postupy: Zastavit načítání stránky</span><span class="sxs-lookup"><span data-stu-id="f0daf-102">How to: Stop a Page from Loading</span></span>
<span data-ttu-id="f0daf-103">Tento příklad ukazuje způsob volání <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> metoda ukončit navigace k obsahu dokončí stahování.</span><span class="sxs-lookup"><span data-stu-id="f0daf-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> method to stop navigation to content before it has finished being downloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0daf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0daf-104">Example</span></span>  
 <span data-ttu-id="f0daf-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>Zastaví stahování požadovaný obsah a způsobí, že <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> událost, která má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f0daf-105"><xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> stops the download of the requested content, and causes the <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> event to be raised.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
