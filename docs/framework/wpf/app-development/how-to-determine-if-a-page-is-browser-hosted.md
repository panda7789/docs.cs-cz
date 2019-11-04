---
title: 'Postupy: určení, zda je stránka hostována prohlížečem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424692"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="a5c97-102">Postupy: určení, zda je stránka hostována prohlížečem</span><span class="sxs-lookup"><span data-stu-id="a5c97-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="a5c97-103">Tento příklad ukazuje, jak určit, zda je <xref:System.Windows.Controls.Page> hostována v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a5c97-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c97-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5c97-104">Example</span></span>  
 <span data-ttu-id="a5c97-105"><xref:System.Windows.Controls.Page> může být hostitelem nezávislá a v důsledku toho může být načten do několika různých typů hostitelů, včetně <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>nebo prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="a5c97-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="a5c97-106">K tomu může dojít v případě, že máte sestavení knihovny, které obsahuje jednu nebo více stránek a na které odkazuje více samostatných a procházích hostitelských aplikací (XAML prohlížeče aplikace (XBAP)).</span><span class="sxs-lookup"><span data-stu-id="a5c97-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable (XAML browser application (XBAP)) host applications.</span></span>  
  
 <span data-ttu-id="a5c97-107">Následující příklad ukazuje, jak použít <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> k určení, zda je <xref:System.Windows.Controls.Page> hostována v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a5c97-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="a5c97-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5c97-108">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
