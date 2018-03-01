---
title: "Typ & č. 39; &lt;typename&gt;& č. 39; není definován"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="e19dd-102">Typ & č. 39; &lt;typename&gt;& č. 39; není definován</span><span class="sxs-lookup"><span data-stu-id="e19dd-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="e19dd-103">Příkaz provedl odkaz na typ, který nebyl definován.</span><span class="sxs-lookup"><span data-stu-id="e19dd-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="e19dd-104">Typ v deklaraci příkazu můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.</span><span class="sxs-lookup"><span data-stu-id="e19dd-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="e19dd-105">**ID chyby:** BC30002</span><span class="sxs-lookup"><span data-stu-id="e19dd-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e19dd-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e19dd-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e19dd-107">Zkontrolujte, jestli definici typu a jeho referenční obě používají stejné pravopis.</span><span class="sxs-lookup"><span data-stu-id="e19dd-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="e19dd-108">Ujistěte se, že je dostupný pro odkaz na definici tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="e19dd-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="e19dd-109">Například, pokud je v jiném modulu typu a bylo deklarováno `Private`, přesuňte definici typu modulu odkazující nebo deklarujte ji `Public`.</span><span class="sxs-lookup"><span data-stu-id="e19dd-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="e19dd-110">Ujistěte se, že není v rámci projektu předefinovat obor názvů typu.</span><span class="sxs-lookup"><span data-stu-id="e19dd-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="e19dd-111">Pokud je, použijte `Global` – klíčové slovo plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="e19dd-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="e19dd-112">Například pokud projektu definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud je plně kvalifikovaný s `Global` – klíčové slovo: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="e19dd-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="e19dd-113">Pokud je definován typ, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definovaný v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], klikněte na tlačítko **přidat odkaz na** na **projektu** nabídce a pak vyberte příslušný objekt Knihovna nebo knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="e19dd-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="e19dd-114">Ujistěte se, že typ je v sestavení, které je součástí profilu cílové rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e19dd-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="e19dd-115">Další informace najdete v tématu [řešení potíží s chybami cílení na rozhraní .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="e19dd-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19dd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e19dd-116">See Also</span></span>  
 [<span data-ttu-id="e19dd-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e19dd-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="e19dd-118">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="e19dd-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="e19dd-119">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="e19dd-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="e19dd-120">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="e19dd-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="e19dd-121">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="e19dd-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="e19dd-122">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="e19dd-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
