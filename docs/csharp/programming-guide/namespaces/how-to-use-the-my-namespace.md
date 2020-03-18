---
title: Použití průvodce programovacím prostorem My namespace – C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700416"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="62627-102">Použití oboru názvů My (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62627-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="62627-103">Obor <xref:Microsoft.VisualBasic.MyServices> názvů`My` (v jazyce Visual Basic) poskytuje snadný a intuitivní přístup k řadě tříd rozhraní .NET Framework, což umožňuje psát kód, který spolupracuje s počítačem, aplikací, nastavením, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="62627-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="62627-104">Přestože byl původně navržen pro `MyServices` použití s jazykem Visual Basic, obor názvů lze použít v aplikacích jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="62627-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="62627-105">Další informace o `MyServices` použití oboru názvů z jazyka Visual Basic naleznete v [tématu Vývoj pomocí aplikace My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="62627-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="62627-106">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="62627-106">Adding a Reference</span></span>  
 <span data-ttu-id="62627-107">Před použitím tříd `MyServices` v řešení je nutné přidat odkaz na knihovnu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="62627-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="62627-108">Přidání odkazu do knihovny jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62627-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="62627-109">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Odkazy** a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="62627-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="62627-110">Po zobrazení dialogového okna **Odkazy** posuňte seznam dolů a vyberte soubor Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="62627-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="62627-111">Můžete také zahrnout následující řádek do `using` oddílu na začátku programu.</span><span class="sxs-lookup"><span data-stu-id="62627-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="62627-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="62627-112">Example</span></span>  
 <span data-ttu-id="62627-113">Tento příklad volá různé statické `MyServices` metody obsažené v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="62627-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="62627-114">Aby se tento kód zkompiloval, musí být do projektu přidán odkaz na soubor Microsoft.VisualBasic.DLL.</span><span class="sxs-lookup"><span data-stu-id="62627-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="62627-115">Ne všechny třídy `MyServices` v oboru názvů lze volat z aplikace <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> Jazyka C#: například třída není kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="62627-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="62627-116">V tomto konkrétním případě statické metody, <xref:Microsoft.VisualBasic.FileIO.FileSystem>které jsou součástí , které jsou také obsaženy v souboru VisualBasic.dll, lze použít místo.</span><span class="sxs-lookup"><span data-stu-id="62627-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="62627-117">Zde je například použití jedné takové metody k duplikaci adresáře:</span><span class="sxs-lookup"><span data-stu-id="62627-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="62627-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="62627-118">See also</span></span>

- [<span data-ttu-id="62627-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62627-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="62627-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="62627-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="62627-121">Použití oborů názvů</span><span class="sxs-lookup"><span data-stu-id="62627-121">Using Namespaces</span></span>](./using-namespaces.md)
