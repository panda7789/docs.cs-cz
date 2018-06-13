---
title: Typ &#39; &lt;typename&gt; &#39; není definován
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595183"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="0772d-102">Typ &#39; &lt;typename&gt; &#39; není definován</span><span class="sxs-lookup"><span data-stu-id="0772d-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="0772d-103">Příkaz provedl odkaz na typ, který nebyl definován.</span><span class="sxs-lookup"><span data-stu-id="0772d-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="0772d-104">Typ v deklaraci příkazu můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.</span><span class="sxs-lookup"><span data-stu-id="0772d-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="0772d-105">**ID chyby:** BC30002</span><span class="sxs-lookup"><span data-stu-id="0772d-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0772d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0772d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="0772d-107">Zkontrolujte, jestli definici typu a jeho referenční obě používají stejné pravopis.</span><span class="sxs-lookup"><span data-stu-id="0772d-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="0772d-108">Ujistěte se, že je dostupný pro odkaz na definici tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="0772d-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="0772d-109">Například, pokud je v jiném modulu typu a bylo deklarováno `Private`, přesuňte definici typu modulu odkazující nebo deklarujte ji `Public`.</span><span class="sxs-lookup"><span data-stu-id="0772d-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="0772d-110">Ujistěte se, že není v rámci projektu předefinovat obor názvů typu.</span><span class="sxs-lookup"><span data-stu-id="0772d-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="0772d-111">Pokud je, použijte `Global` – klíčové slovo plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="0772d-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="0772d-112">Například pokud projektu definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud je plně kvalifikovaný s `Global` – klíčové slovo: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="0772d-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="0772d-113">Pokud je definován typ, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definovaný v Visual Basic, klikněte na tlačítko **přidat odkaz na** na **projektu** nabídce a pak vyberte příslušný objekt Knihovna nebo knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="0772d-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="0772d-114">Ujistěte se, že typ je v sestavení, které je součástí profilu cílové rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0772d-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="0772d-115">Další informace najdete v tématu [řešení potíží s chybami cílení na rozhraní .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="0772d-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0772d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0772d-116">See Also</span></span>  
 [<span data-ttu-id="0772d-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0772d-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="0772d-118">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="0772d-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="0772d-119">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="0772d-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="0772d-120">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="0772d-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="0772d-121">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="0772d-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="0772d-122">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="0772d-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
