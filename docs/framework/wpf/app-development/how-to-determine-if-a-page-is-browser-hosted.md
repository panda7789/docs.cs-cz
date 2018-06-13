---
title: 'Postupy: určení, zda je na stránce hostované prohlížečem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: 6eb83429cb4f9dac5f3561b41997d24bcaa2c62f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545886"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Postupy: určení, zda je na stránce hostované prohlížečem
Tento příklad ukazuje, jak zjistit, jestli <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.  
  
## <a name="example"></a>Příklad  
 A <xref:System.Windows.Controls.Page> může být nezávislá na hostitele a v důsledku toho může být načtena do několika různých typů hostitele, včetně <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, nebo prohlížeč. K tomu může dojít v případě, že máte sestavení knihovny obsahující jednu nebo více stránek a který se odkazuje víc samostatné a procházet ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) hostování aplikací.  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> k určení, zda <xref:System.Windows.Controls.Page> je hostovaná v prohlížeči.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
