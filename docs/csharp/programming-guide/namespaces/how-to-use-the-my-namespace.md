---
title: 'Postupy: Použití My Namespace - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 9621f6a01ef4e30bf34b97df3d2c3033e9b62a23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316021"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="e5d02-102">Postupy: Použití My Namespace (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="e5d02-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="e5d02-103"><xref:Microsoft.VisualBasic.MyServices> Obor názvů (`My` v jazyce Visual Basic) poskytuje jednoduché a intuitivní přístup k počtu tříd rozhraní .NET Framework, což umožňuje napsat kód, který komunikuje s počítačem, aplikace, nastavení, prostředky a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e5d02-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="e5d02-104">Přestože původně navržený pro použití s jazykem Visual Basic `MyServices` oboru názvů lze použít v aplikacích jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e5d02-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="e5d02-105">Další informace o používání `MyServices` oboru názvů z jazyka Visual Basic naleznete v tématu [vývoj aplikací pomocí Moje](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5d02-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="e5d02-106">Přidání odkazu</span><span class="sxs-lookup"><span data-stu-id="e5d02-106">Adding a Reference</span></span>  
 <span data-ttu-id="e5d02-107">Než budete moct použít `MyServices` třídy ve vašem řešení, musíte přidat odkaz na knihovnu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5d02-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="e5d02-108">Chcete-li přidat odkaz na knihovnu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5d02-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="e5d02-109">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="e5d02-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="e5d02-110">Když **odkazy** se zobrazí dialogové okno, přejděte dolů v seznamu a vyberte Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="e5d02-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="e5d02-111">Můžete také přidejte následující řádek v `using` části na začátku programu.</span><span class="sxs-lookup"><span data-stu-id="e5d02-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="e5d02-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5d02-112">Example</span></span>  
 <span data-ttu-id="e5d02-113">Tento příklad příkladu volá různých statických metod, které jsou součástí `MyServices` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5d02-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="e5d02-114">Pro tento kód zkompilovat musí být odkaz na knihovny Microsoft.VisualBasic.DLL přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="e5d02-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="e5d02-115">Ne všechny třídy v `MyServices` oboru názvů může být volána z aplikace v jazyce C#: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="e5d02-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="e5d02-116">V tomto konkrétním případě statických metod, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem>, které jsou také obsaženy v VisualBasic.dll, lze použít místo toho.</span><span class="sxs-lookup"><span data-stu-id="e5d02-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="e5d02-117">Tady je například jak duplikovat adresář pomocí těchto metod:</span><span class="sxs-lookup"><span data-stu-id="e5d02-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="e5d02-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5d02-118">See also</span></span>

- [<span data-ttu-id="e5d02-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e5d02-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e5d02-120">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="e5d02-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="e5d02-121">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="e5d02-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
