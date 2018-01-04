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
ms.workload: dotnet
ms.openlocfilehash: dd8a8b8c3bea291afbe41e0c36e0d708bff3ef57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="fd951-102">Postupy: určení, zda je na stránce hostované prohlížečem</span><span class="sxs-lookup"><span data-stu-id="fd951-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="fd951-103">Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="fd951-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd951-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd951-104">Example</span></span>  
 <span data-ttu-id="fd951-105">A <xref:System.Windows.Controls.Page> může být nezávislá na hostitele a v důsledku toho může být načtena do několika různých typů hostitele, včetně <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, nebo prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="fd951-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="fd951-106">K tomu může dojít v případě, že máte sestavení knihovny obsahující jednu nebo více stránek a který se odkazuje víc samostatné a procházet ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostování aplikací.</span><span class="sxs-lookup"><span data-stu-id="fd951-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="fd951-107">Následující příklad ukazuje, jak používat <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> k určení, zda <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="fd951-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="fd951-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd951-108">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
