---
title: Předávání identifikátorů URI do prostředí Windows Runtime
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a31a1246fe311c36e7457327c79aeeef30e7813
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Předávání identifikátorů URI do prostředí Windows Runtime
Prostředí Windows Runtime metody přijímají pouze absolutní identifikátory URI. Pokud předáte relativní identifikátor URI k [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> je vyvolána výjimka. Tady je důvod, proč: při použití [!INCLUDE[wrt](../../../includes/wrt-md.md)] v rozhraní .NET Framework kódu <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třídy se zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v Intellisense. <xref:System.Uri?displayProperty=nameWithType> Třída umožňuje relativní identifikátory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída neexistuje. To platí také pro metody vystavit v [!INCLUDE[wrt](../../../includes/wrt-md.md)] součásti. Pokud příslušné součásti zpřístupní metodu, která přebírá identifikátor URI, zahrnuje podpis ve vašem kódu <xref:System.Uri?displayProperty=nameWithType>. Ale uživatelům vaší součásti, obsahuje podpis <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Identifikátor URI, který je předán do příslušné součásti musí být absolutní identifikátor URI.  
  
 Toto téma ukazuje, jak zjistit absolutní identifikátor URI a jak ho vytvořit ve vztahu k prostředku v balíčku aplikace.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Zjišťování a používání absolutní identifikátor URI  
 Použití <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> vlastnost zajistěte, aby byl identifikátor URI absolutní před předáním na [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Pomocí této vlastnosti je efektivnější než zachytávání a zpracování <xref:System.ArgumentException> výjimka.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Pomocí absolutní identifikátor URI pro prostředek v balíčku aplikace  
 Pokud chcete určit identifikátor URI pro prostředek, který obsahuje váš balíček aplikace, můžete použít `ms-appx` nebo `ms-appx-web` schéma vytvořit absolutní identifikátor URI.  
  
 Následující příklad ukazuje, jak nastavit [zdroj](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) vlastnost pro [webové zobrazení](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) řízení a [zdroj](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) vlastnost pro [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) ovládací prvek na prostředky, které jsou obsaženy ve složce s názvem stránek pomocí XAML a kódu.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Další informace o těchto režimů najdete v tématu [schémata identifikátoru URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) ve službě Windows Dev Center.  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
