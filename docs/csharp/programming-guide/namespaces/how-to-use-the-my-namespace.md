---
title: Jak používat můj obor názvů – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241939"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="4caf3-102">Jak používat můj obor názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4caf3-102">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="4caf3-103"><xref:Microsoft.VisualBasic.MyServices>Obor názvů ( `My` v Visual Basic) poskytuje snadný a intuitivní přístup k několika třídám .NET a umožňuje psát kód, který komunikuje s počítačem, aplikací, nastavením, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4caf3-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="4caf3-104">I když je původně určený pro použití s Visual Basic, `MyServices` obor názvů lze použít v aplikacích C#.</span><span class="sxs-lookup"><span data-stu-id="4caf3-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="4caf3-105">Další informace o používání `MyServices` oboru názvů z Visual Basic naleznete v tématu [vývoj s My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="4caf3-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="4caf3-106">Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="4caf3-106">Add a reference</span></span>

 <span data-ttu-id="4caf3-107">Než budete moci použít `MyServices` třídy ve vašem řešení, je nutné přidat odkaz na knihovnu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4caf3-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="4caf3-108">Přidat odkaz na knihovnu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4caf3-108">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="4caf3-109">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="4caf3-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="4caf3-110">Když se zobrazí dialogové okno **odkazy** , přejděte dolů na seznam a vyberte Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="4caf3-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="4caf3-111">V části na začátku programu můžete také chtít zahrnout následující řádek `using` .</span><span class="sxs-lookup"><span data-stu-id="4caf3-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="4caf3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4caf3-112">Example</span></span>  
 <span data-ttu-id="4caf3-113">Tento příklad volá různé statické metody obsažené v `MyServices` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4caf3-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="4caf3-114">Pro zkompilování tohoto kódu musí být do projektu přidán odkaz na Microsoft. VisualBasic. DLL.</span><span class="sxs-lookup"><span data-stu-id="4caf3-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="4caf3-115">Ne všechny třídy v `MyServices` oboru názvů mohou být volány z aplikace jazyka C#: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="4caf3-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="4caf3-116">V tomto konkrétním případě lze místo toho použít statické metody, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem> , které jsou také obsaženy v souboru VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="4caf3-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="4caf3-117">Tady je příklad, jak použít jednu takovou metodu pro duplikaci adresáře:</span><span class="sxs-lookup"><span data-stu-id="4caf3-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="4caf3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4caf3-118">See also</span></span>

- [<span data-ttu-id="4caf3-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4caf3-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4caf3-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="4caf3-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="4caf3-121">Používání oborů názvů</span><span class="sxs-lookup"><span data-stu-id="4caf3-121">Using Namespaces</span></span>](./using-namespaces.md)
