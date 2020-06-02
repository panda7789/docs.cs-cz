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
ms.openlocfilehash: 7152fb02abf430c0d0e27b82550e4006e3958e93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288885"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Předávání identifikátorů URI do prostředí Windows Runtime
Metody prostředí Windows Runtime přijímají pouze absolutní identifikátory URI. Pokud předáte relativní identifikátor URI metodě prostředí Windows Runtime, <xref:System.ArgumentException> je vyvolána výjimka. Důvody: když použijete prostředí Windows Runtime v kódu .NET Framework, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Třída se zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v IntelliSense. <xref:System.Uri?displayProperty=nameWithType>Třída umožňuje relativní identifikátory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Třída ne. To platí také pro metody, které vystavíte v prostředí Windows Runtimech součástech. Pokud vaše komponenta zpřístupňuje metodu, která přijímá identifikátor URI, signatura v kódu zahrnuje <xref:System.Uri?displayProperty=nameWithType> . Pro uživatele vaší komponenty však signatura zahrnuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType> . Identifikátor URI, který je předán vaší komponentě, musí být absolutním identifikátorem URI.  
  
V tomto tématu se dozvíte, jak zjistit absolutní identifikátor URI a jak ho vytvořit při odkazování na prostředek v balíčku aplikace.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Zjištění a použití absolutního identifikátoru URI  
Pomocí <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> vlastnosti zajistěte, aby byl identifikátor URI před předáním do prostředí Windows Runtime absolutní. Použití této vlastnosti je efektivnější než zachycení a manipulace s <xref:System.ArgumentException> výjimkou.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Použití absolutního identifikátoru URI pro prostředek v balíčku aplikace  
Pokud chcete zadat identifikátor URI pro prostředek, který obsahuje balíček aplikace, můžete použít `ms-appx` `ms-appx-web` schéma nebo k vytvoření ABSOLUTNÍho identifikátoru URI.  
  
Následující příklad ukazuje, jak nastavit <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> vlastnost pro <xref:Windows.UI.Xaml.Controls.WebView> ovládací prvek a <xref:Windows.UI.Xaml.Controls.Image.Source%2A> vlastnost <xref:Windows.UI.Xaml.Controls.Image> ovládacího prvku na prostředky, které jsou obsaženy ve složce s názvem Pages, pomocí XAML a kódu.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Další informace o těchto schématech najdete v tématu [schémata identifikátorů URI](/windows/uwp/app-resources/uri-schemes) na stránce Windows Dev Center.  
  
## <a name="see-also"></a>Viz také

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](support-for-windows-store-apps-and-windows-runtime.md)
