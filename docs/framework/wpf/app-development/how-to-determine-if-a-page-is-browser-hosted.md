---
title: 'Postupy: Určete, jestli je stránka hostovaná prohlížečem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: aa2aa36e4f887c4fa02314f7834e2a46268c8ff9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661292"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="86a38-102">Postupy: Určete, jestli je stránka hostovaná prohlížečem</span><span class="sxs-lookup"><span data-stu-id="86a38-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="86a38-103">Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Controls.Page> je hostována v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="86a38-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a38-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="86a38-104">Example</span></span>  
 <span data-ttu-id="86a38-105">A <xref:System.Windows.Controls.Page> může být nezávislá na hostitele a v důsledku toho může být načtena do několika různých typů hostitele, včetně <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, nebo v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="86a38-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="86a38-106">K tomu může dojít, když máte sestavení knihovny, která obsahuje jednu nebo více stránek a která je odkazovaná více samostatná a nelze procházet ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostování aplikací.</span><span class="sxs-lookup"><span data-stu-id="86a38-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="86a38-107">Následující příklad ukazuje, jak používat <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> k určení, zda <xref:System.Windows.Controls.Page> je hostována v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="86a38-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="86a38-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86a38-108">See also</span></span>
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
