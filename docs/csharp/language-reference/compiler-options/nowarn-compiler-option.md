---
title: "-nowarn (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2784e63b7c1e67b32fc448b4b112ad0252b1abd9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="4e807-102">-nowarn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4e807-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="4e807-103">**- Nowarn** možnost umožňuje potlačit kompilátoru zobrazování jeden nebo více upozornění.</span><span class="sxs-lookup"><span data-stu-id="4e807-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="4e807-104">Více čísel upozornění oddělte čárkou.</span><span class="sxs-lookup"><span data-stu-id="4e807-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e807-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e807-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e807-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4e807-106">Arguments</span></span>  
 <span data-ttu-id="4e807-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="4e807-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="4e807-108">Upozornění čísel, které chcete kompilátorem potlačit.</span><span class="sxs-lookup"><span data-stu-id="4e807-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e807-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e807-109">Remarks</span></span>  
 <span data-ttu-id="4e807-110">Měli byste zadat pouze číselnou část identifikátor upozornění.</span><span class="sxs-lookup"><span data-stu-id="4e807-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="4e807-111">Například pokud chcete potlačit CS0028, můžete zadat `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="4e807-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="4e807-112">Kompilátor bude tiše ignorovat čísla upozornění předaná `-nowarn` , které byly v předchozích verzích platný, ale které byly odebrány z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4e807-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="4e807-113">Například CS0679 platné v kompilátoru v sadě Visual Studio .NET 2002 ale následně bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="4e807-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="4e807-114">Následující upozornění nelze potlačit pomocí `-nowarn` možnost:</span><span class="sxs-lookup"><span data-stu-id="4e807-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="4e807-115">CS2002 kompilátoru upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="4e807-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="4e807-116">CS2023 kompilátoru upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="4e807-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="4e807-117">CS2029 kompilátoru upozornění (úroveň 1)</span><span class="sxs-lookup"><span data-stu-id="4e807-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4e807-118">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e807-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4e807-119">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="4e807-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="4e807-120">Podrobnosti najdete v tématu [stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="4e807-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="4e807-121">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="4e807-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="4e807-122">Změnit **potlačit upozornění** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4e807-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="4e807-123">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e807-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e807-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e807-124">See Also</span></span>  
 [<span data-ttu-id="4e807-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e807-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4e807-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4e807-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="4e807-127">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e807-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
