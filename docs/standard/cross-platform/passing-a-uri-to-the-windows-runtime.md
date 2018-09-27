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
ms.openlocfilehash: 0f019c1075c119c3d814b3b7add8fe30f3e4d107
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237056"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Předávání identifikátorů URI do prostředí Windows Runtime
Prostředí Windows Runtime metody přijímají pouze absolutní identifikátor URI. Pokud předáte relativní identifikátor URI pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> je vyvolána výjimka. Tady je důvod, proč: při použití [!INCLUDE[wrt](../../../includes/wrt-md.md)] v kódu rozhraní .NET Framework <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída se objeví jako <xref:System.Uri?displayProperty=nameWithType> v technologii Intellisense. <xref:System.Uri?displayProperty=nameWithType> Třída umožňuje relativní identifikátory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída nepodporuje. To platí také pro metody, které vystavíte v [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty. Pokud vaše komponenta zpřístupní metodu, která přijímá identifikátor URI, podpis ve vašem kódu obsahuje <xref:System.Uri?displayProperty=nameWithType>. Ale pro uživatele vaší komponenty, obsahuje podpis <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Identifikátor URI, který je předán vaší komponentě, musí být absolutní identifikátor URI.  
  
 Toto téma ukazuje, jak detekovat absolutní identifikátor URI a jak ji vytvořit při odkazování na prostředek v balíčku aplikace.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Odpojení a používání absolutního identifikátoru URI  
 Použití <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> vlastnost tak, aby byl identifikátor URI absolutní před předáním do [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Pomocí této vlastnosti je efektivnější než zachytávání a manipulace <xref:System.ArgumentException> výjimky.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Použití absolutní identifikátor URI pro prostředek v balíčku aplikace  
 Pokud chcete určit identifikátor URI pro prostředek, který obsahuje balíček aplikace, můžete použít `ms-appx` nebo `ms-appx-web` schéma k vytvoření absolutního identifikátoru URI.  
  
 Následující příklad ukazuje, jak nastavit [zdroj](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) vlastnost pro [WebView](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) ovládacího prvku a [zdroj](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) vlastnost [Image](https://msdn.microsoft.com/library/windows/apps/br242752.aspx) ovládacího prvku k prostředkům, které jsou obsaženy ve složce s názvem stránky pomocí XAML a kódu.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Další informace o těchto schématech naleznete v tématu [schémata identifikátoru URI](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx) Windows Dev Center.  
  
## <a name="see-also"></a>Viz také:

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
