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
ms.openlocfilehash: 71d427c2d602efbd92dc0128b1fada85a987904a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123620"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Předávání identifikátorů URI do prostředí Windows Runtime
Metody prostředí Windows Runtime přijímají pouze absolutní identifikátory URI. Pokud předáte relativní identifikátor URI metodě prostředí Windows Runtime, je vyvolána výjimka <xref:System.ArgumentException>. Z tohoto důvodu: při použití prostředí Windows Runtime v kódu .NET Framework se třída <xref:Windows.Foundation.Uri?displayProperty=nameWithType> zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v technologii IntelliSense. Třída <xref:System.Uri?displayProperty=nameWithType> povoluje relativní identifikátory URI, ale třída <xref:Windows.Foundation.Uri?displayProperty=nameWithType> ne. To platí také pro metody, které vystavíte v prostředí Windows Runtimech součástech. Pokud vaše komponenta zpřístupňuje metodu, která přebírá identifikátor URI, signatura v kódu zahrnuje <xref:System.Uri?displayProperty=nameWithType>. Pro uživatele vaší komponenty však signatura zahrnuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Identifikátor URI, který je předán vaší komponentě, musí být absolutním identifikátorem URI.  
  
V tomto tématu se dozvíte, jak zjistit absolutní identifikátor URI a jak ho vytvořit při odkazování na prostředek v balíčku aplikace.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Zjištění a použití absolutního identifikátoru URI  
Pomocí vlastnosti <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> zajistěte, aby byl identifikátor URI před předáním do prostředí Windows Runtime absolutní. Použití této vlastnosti je efektivnější než zachycení a zpracování výjimky <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Použití absolutního identifikátoru URI pro prostředek v balíčku aplikace  
Pokud chcete zadat identifikátor URI pro prostředek, který obsahuje váš balíček aplikace, můžete použít schéma `ms-appx` nebo `ms-appx-web` k vytvoření absolutního identifikátoru URI.  
  
Následující příklad ukazuje, jak nastavit vlastnost <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> pro ovládací prvek <xref:Windows.UI.Xaml.Controls.WebView> a vlastnost <xref:Windows.UI.Xaml.Controls.Image.Source%2A> pro ovládací prvek <xref:Windows.UI.Xaml.Controls.Image> na prostředky, které jsou obsaženy ve složce s názvem Pages s použitím XAML a kódu.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Další informace o těchto schématech najdete v tématu [schémata identifikátorů URI](/windows/uwp/app-resources/uri-schemes) na stránce Windows Dev Center.  
  
## <a name="see-also"></a>Viz také

- [Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
