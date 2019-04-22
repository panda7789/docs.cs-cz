---
title: Typ '<typename>' není definován.
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825037"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="08ad7-102">Typ '\<typename >' není definován</span><span class="sxs-lookup"><span data-stu-id="08ad7-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="08ad7-103">Příkaz provedl odkaz na typ, který nebyl definován.</span><span class="sxs-lookup"><span data-stu-id="08ad7-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="08ad7-104">Typ v příkazu deklarace můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.</span><span class="sxs-lookup"><span data-stu-id="08ad7-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="08ad7-105">**ID chyby:** BC30002</span><span class="sxs-lookup"><span data-stu-id="08ad7-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08ad7-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="08ad7-106">To correct this error</span></span>  
  
-   <span data-ttu-id="08ad7-107">Zajistěte, že definice typu a jeho odkaz obou použít stejné kontroly pravopisu.</span><span class="sxs-lookup"><span data-stu-id="08ad7-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="08ad7-108">Ujistěte se, že definice typu je přístupné pro odkaz.</span><span class="sxs-lookup"><span data-stu-id="08ad7-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="08ad7-109">Například, pokud je typ v jiném modulu a byla deklarována `Private`, přesunutí definice typu pro odkazující modul nebo ji deklarovat `Public`.</span><span class="sxs-lookup"><span data-stu-id="08ad7-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="08ad7-110">Ujistěte se, že obor názvů tohoto typu není předefinovat v rámci svého projektu.</span><span class="sxs-lookup"><span data-stu-id="08ad7-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="08ad7-111">Pokud se jedná, použijte `Global` – klíčové slovo plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="08ad7-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="08ad7-112">Například, pokud projekt definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud to není plně nekvalifikuje pomocí `Global` – klíčové slovo: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="08ad7-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="08ad7-113">Pokud je typ definován, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definována v aplikaci Visual Basic, klikněte na **přidat odkaz** na **projektu** nabídky a pak vyberte příslušný objekt Knihovna nebo knihovna typů.</span><span class="sxs-lookup"><span data-stu-id="08ad7-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="08ad7-114">Zajistěte, aby byl typ v sestavení, která je součástí cíleném profilu rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="08ad7-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="08ad7-115">Další informace najdete v tématu [řešení chyb cílí na .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="08ad7-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ad7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08ad7-116">See also</span></span>

- [<span data-ttu-id="08ad7-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08ad7-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="08ad7-118">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="08ad7-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="08ad7-119">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="08ad7-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="08ad7-120">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="08ad7-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="08ad7-121">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="08ad7-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="08ad7-122">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="08ad7-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
