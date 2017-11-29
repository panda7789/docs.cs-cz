---
title: "Postupy: určení, zda je na stránce hostované prohlížečem"
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
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1da46596bf48d9648830d20758647be753f128fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="a01d8-102">Postupy: určení, zda je na stránce hostované prohlížečem</span><span class="sxs-lookup"><span data-stu-id="a01d8-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="a01d8-103">Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a01d8-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01d8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a01d8-104">Example</span></span>  
 <span data-ttu-id="a01d8-105">A <xref:System.Windows.Controls.Page> může být nezávislá na hostitele a v důsledku toho může být načtena do několika různých typů hostitele, včetně <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, nebo prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="a01d8-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="a01d8-106">K tomu může dojít v případě, že máte sestavení knihovny obsahující jednu nebo více stránek a který se odkazuje víc samostatné a procházet ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostování aplikací.</span><span class="sxs-lookup"><span data-stu-id="a01d8-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="a01d8-107">Následující příklad ukazuje, jak používat <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> k určení, zda <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a01d8-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="a01d8-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a01d8-108">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
