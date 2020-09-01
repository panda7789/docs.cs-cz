---
description: -Warn (možnosti kompilátoru C#)
title: -Warn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: ab906912bc4bfab40e459c92a823b915240b8d55
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125082"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="ecc66-103">-Warn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ecc66-103">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="ecc66-104">Možnost **-s upozorněním** umožňuje potlačit, že kompilátor zobrazuje jedno nebo více upozornění.</span><span class="sxs-lookup"><span data-stu-id="ecc66-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="ecc66-105">Více čísel upozornění oddělte čárkou.</span><span class="sxs-lookup"><span data-stu-id="ecc66-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc66-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc66-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ecc66-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ecc66-107">Arguments</span></span>  
 <span data-ttu-id="ecc66-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="ecc66-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="ecc66-109">Čísla upozornění, která má kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="ecc66-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecc66-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecc66-110">Remarks</span></span>  
 <span data-ttu-id="ecc66-111">Měli byste zadat jenom číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="ecc66-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="ecc66-112">Například pokud chcete potlačit CS0028, můžete zadat `-nowarn:28` .</span><span class="sxs-lookup"><span data-stu-id="ecc66-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="ecc66-113">Kompilátor bude tiše ignorovat čísla upozornění předaná do `-nowarn` , která byla platná v předchozích verzích, ale byla odebrána z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ecc66-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="ecc66-114">Například CS0679 byl platný v kompilátoru v aplikaci Visual Studio .NET 2002, ale byl následně odebrán.</span><span class="sxs-lookup"><span data-stu-id="ecc66-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="ecc66-115">Následující upozornění nelze potlačit pomocí `-nowarn` Možnosti:</span><span class="sxs-lookup"><span data-stu-id="ecc66-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="ecc66-116">Upozornění kompilátoru (úroveň 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="ecc66-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="ecc66-117">Upozornění kompilátoru (úroveň 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="ecc66-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="ecc66-118">Upozornění kompilátoru (úroveň 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="ecc66-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ecc66-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ecc66-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ecc66-120">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="ecc66-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="ecc66-121">Podrobnosti naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ecc66-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="ecc66-122">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="ecc66-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ecc66-123">Upravte vlastnost **potlačit upozornění** .</span><span class="sxs-lookup"><span data-stu-id="ecc66-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="ecc66-124">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> .</span><span class="sxs-lookup"><span data-stu-id="ecc66-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc66-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc66-125">See also</span></span>

- [<span data-ttu-id="ecc66-126">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ecc66-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ecc66-127">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ecc66-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="ecc66-128">Chyby kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ecc66-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
