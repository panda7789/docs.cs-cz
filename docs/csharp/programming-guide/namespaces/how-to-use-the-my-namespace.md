---
title: Jak používat můj obor názvů – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700416"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="20605-102">Použití oboru názvů My (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="20605-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="20605-103">Obor názvů <xref:Microsoft.VisualBasic.MyServices> (`My` v Visual Basic) poskytuje snadný a intuitivní přístup k řadě tříd .NET Framework a umožňuje psát kód, který komunikuje s počítačem, aplikací, nastavením, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="20605-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="20605-104">I když je původně určený pro použití s Visual Basic, `MyServices` obor názvů se dá C# použít v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="20605-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="20605-105">Další informace o použití `MyServices` oboru názvů z Visual Basic naleznete v tématu [vývoj s My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="20605-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="20605-106">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="20605-106">Adding a Reference</span></span>  
 <span data-ttu-id="20605-107">Než budete moci použít třídy `MyServices` ve vašem řešení, je nutné přidat odkaz na knihovnu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20605-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="20605-108">Přidání odkazu do knihovny Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20605-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="20605-109">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="20605-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="20605-110">Když se zobrazí dialogové okno **odkazy** , přejděte dolů na seznam a vyberte Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="20605-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="20605-111">Můžete také zahrnout následující řádek do části `using` na začátku programu.</span><span class="sxs-lookup"><span data-stu-id="20605-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="20605-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="20605-112">Example</span></span>  
 <span data-ttu-id="20605-113">Tento příklad volá různé statické metody obsažené v oboru názvů `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="20605-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="20605-114">Pro zkompilování tohoto kódu musí být do projektu přidán odkaz na Microsoft. VisualBasic. DLL.</span><span class="sxs-lookup"><span data-stu-id="20605-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="20605-115">Ne všechny třídy v oboru názvů `MyServices` mohou být volány z C# aplikace: například třída <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> není kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="20605-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="20605-116">V tomto konkrétním případě lze místo toho použít statické metody, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem>, které jsou také obsaženy v souboru VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="20605-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="20605-117">Tady je příklad, jak použít jednu takovou metodu pro duplikaci adresáře:</span><span class="sxs-lookup"><span data-stu-id="20605-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="20605-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20605-118">See also</span></span>

- [<span data-ttu-id="20605-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="20605-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="20605-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="20605-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="20605-121">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="20605-121">Using Namespaces</span></span>](./using-namespaces.md)
