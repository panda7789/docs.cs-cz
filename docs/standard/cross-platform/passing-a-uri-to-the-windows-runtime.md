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
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="e3028-102">Předávání identifikátorů URI do prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="e3028-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="e3028-103">Metody prostředí Windows Runtime přijímají pouze absolutní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="e3028-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="e3028-104">Pokud předáte relativní identifikátor URI metodě prostředí Windows Runtime, je vyvolána výjimka <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e3028-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="e3028-105">Z tohoto důvodu: při použití prostředí Windows Runtime v kódu .NET Framework se třída <xref:Windows.Foundation.Uri?displayProperty=nameWithType> zobrazí jako <xref:System.Uri?displayProperty=nameWithType> v technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e3028-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="e3028-106">Třída <xref:System.Uri?displayProperty=nameWithType> povoluje relativní identifikátory URI, ale třída <xref:Windows.Foundation.Uri?displayProperty=nameWithType> ne.</span><span class="sxs-lookup"><span data-stu-id="e3028-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="e3028-107">To platí také pro metody, které vystavíte v prostředí Windows Runtimech součástech.</span><span class="sxs-lookup"><span data-stu-id="e3028-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="e3028-108">Pokud vaše komponenta zpřístupňuje metodu, která přebírá identifikátor URI, signatura v kódu zahrnuje <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3028-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e3028-109">Pro uživatele vaší komponenty však signatura zahrnuje <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e3028-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e3028-110">Identifikátor URI, který je předán vaší komponentě, musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="e3028-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="e3028-111">V tomto tématu se dozvíte, jak zjistit absolutní identifikátor URI a jak ho vytvořit při odkazování na prostředek v balíčku aplikace.</span><span class="sxs-lookup"><span data-stu-id="e3028-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="e3028-112">Zjištění a použití absolutního identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="e3028-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="e3028-113">Pomocí vlastnosti <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> zajistěte, aby byl identifikátor URI před předáním do prostředí Windows Runtime absolutní.</span><span class="sxs-lookup"><span data-stu-id="e3028-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="e3028-114">Použití této vlastnosti je efektivnější než zachycení a zpracování výjimky <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="e3028-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="e3028-115">Použití absolutního identifikátoru URI pro prostředek v balíčku aplikace</span><span class="sxs-lookup"><span data-stu-id="e3028-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="e3028-116">Pokud chcete zadat identifikátor URI pro prostředek, který obsahuje váš balíček aplikace, můžete použít schéma `ms-appx` nebo `ms-appx-web` k vytvoření absolutního identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="e3028-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="e3028-117">Následující příklad ukazuje, jak nastavit vlastnost <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> pro ovládací prvek <xref:Windows.UI.Xaml.Controls.WebView> a vlastnost <xref:Windows.UI.Xaml.Controls.Image.Source%2A> pro ovládací prvek <xref:Windows.UI.Xaml.Controls.Image> na prostředky, které jsou obsaženy ve složce s názvem Pages s použitím XAML a kódu.</span><span class="sxs-lookup"><span data-stu-id="e3028-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="e3028-118">Další informace o těchto schématech najdete v tématu [schémata identifikátorů URI](/windows/uwp/app-resources/uri-schemes) na stránce Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="e3028-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3028-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3028-119">See also</span></span>

- [<span data-ttu-id="e3028-120">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3028-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
