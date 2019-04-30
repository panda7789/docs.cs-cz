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
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921378"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="c7147-102">Předávání identifikátorů URI do prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="c7147-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="c7147-103">Prostředí Windows Runtime metody přijímají pouze absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="c7147-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="c7147-104">Pokud předáte relativní identifikátor URI pro [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c7147-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="c7147-105">Tady jsou důvody: Při použití [!INCLUDE[wrt](../../../includes/wrt-md.md)] v kódu rozhraní .NET Framework <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída se objeví jako <xref:System.Uri?displayProperty=nameWithType> v technologii Intellisense.</span><span class="sxs-lookup"><span data-stu-id="c7147-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="c7147-106"><xref:System.Uri?displayProperty=nameWithType> Třída umožňuje relativní identifikátory URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> třída nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c7147-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="c7147-107">To platí také pro metody, které vystavíte v [!INCLUDE[wrt](../../../includes/wrt-md.md)] komponenty.</span><span class="sxs-lookup"><span data-stu-id="c7147-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="c7147-108">Pokud vaše komponenta zpřístupní metodu, která přijímá identifikátor URI, podpis ve vašem kódu obsahuje <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7147-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7147-109">Ale pro uživatele vaší komponenty, obsahuje podpis <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7147-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7147-110">Identifikátor URI, který je předán vaší komponentě, musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="c7147-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="c7147-111">Toto téma ukazuje, jak detekovat absolutní identifikátor URI a jak ji vytvořit při odkazování na prostředek v balíčku aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7147-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="c7147-112">Odpojení a používání absolutního identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="c7147-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="c7147-113">Použití <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> vlastnost tak, aby byl identifikátor URI absolutní před předáním do [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7147-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="c7147-114">Pomocí této vlastnosti je efektivnější než zachytávání a manipulace <xref:System.ArgumentException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="c7147-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="c7147-115">Použití absolutní identifikátor URI pro prostředek v balíčku aplikace</span><span class="sxs-lookup"><span data-stu-id="c7147-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="c7147-116">Pokud chcete určit identifikátor URI pro prostředek, který obsahuje balíček aplikace, můžete použít `ms-appx` nebo `ms-appx-web` schéma k vytvoření absolutního identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="c7147-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="c7147-117">Následující příklad ukazuje, jak nastavit <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> vlastnost <xref:Windows.UI.Xaml.Controls.WebView> ovládacího prvku a <xref:Windows.UI.Xaml.Controls.Image.Source%2A> vlastnost <xref:Windows.UI.Xaml.Controls.Image> ovládacího prvku na prostředky, které jsou obsaženy ve složce s názvem stránky, pomocí XAML a kódu.</span><span class="sxs-lookup"><span data-stu-id="c7147-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="c7147-118">Další informace o těchto schématech naleznete v tématu [schémata identifikátoru URI](/windows/uwp/app-resources/uri-schemes) Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="c7147-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7147-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7147-119">See also</span></span>

- [<span data-ttu-id="c7147-120">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7147-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
