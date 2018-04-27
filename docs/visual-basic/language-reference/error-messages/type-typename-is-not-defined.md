---
title: Typ &#39; &lt;typename&gt; &#39; není definován
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7c3efbcabf1e40c7f550b5f54d16e697561cf82c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="a2a37-102">Typ &#39; &lt;typename&gt; &#39; není definován</span><span class="sxs-lookup"><span data-stu-id="a2a37-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="a2a37-103">Příkaz provedl odkaz na typ, který nebyl definován.</span><span class="sxs-lookup"><span data-stu-id="a2a37-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="a2a37-104">Typ v deklaraci příkazu můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.</span><span class="sxs-lookup"><span data-stu-id="a2a37-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="a2a37-105">**ID chyby:** BC30002</span><span class="sxs-lookup"><span data-stu-id="a2a37-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2a37-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a2a37-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a2a37-107">Zkontrolujte, jestli definici typu a jeho referenční obě používají stejné pravopis.</span><span class="sxs-lookup"><span data-stu-id="a2a37-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="a2a37-108">Ujistěte se, že je dostupný pro odkaz na definici tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a2a37-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="a2a37-109">Například, pokud je v jiném modulu typu a bylo deklarováno `Private`, přesuňte definici typu modulu odkazující nebo deklarujte ji `Public`.</span><span class="sxs-lookup"><span data-stu-id="a2a37-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="a2a37-110">Ujistěte se, že není v rámci projektu předefinovat obor názvů typu.</span><span class="sxs-lookup"><span data-stu-id="a2a37-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="a2a37-111">Pokud je, použijte `Global` – klíčové slovo plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="a2a37-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="a2a37-112">Například pokud projektu definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud je plně kvalifikovaný s `Global` – klíčové slovo: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="a2a37-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="a2a37-113">Pokud je definován typ, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definovaný v Visual Basic, klikněte na tlačítko **přidat odkaz na** na **projektu** nabídce a pak vyberte příslušný objekt Knihovna nebo knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a2a37-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="a2a37-114">Ujistěte se, že typ je v sestavení, které je součástí profilu cílové rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2a37-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="a2a37-115">Další informace najdete v tématu [řešení potíží s chybami cílení na rozhraní .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="a2a37-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a37-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2a37-116">See Also</span></span>  
 [<span data-ttu-id="a2a37-117">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2a37-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="a2a37-118">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="a2a37-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="a2a37-119">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a2a37-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="a2a37-120">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="a2a37-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="a2a37-121">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="a2a37-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="a2a37-122">Správa odkazů v projektu</span><span class="sxs-lookup"><span data-stu-id="a2a37-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
