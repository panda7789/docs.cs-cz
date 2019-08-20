---
title: -Warn (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606611"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="29083-102">-Warn (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="29083-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="29083-103">Možnost **-** s upozorněním umožňuje potlačit, že kompilátor zobrazuje jedno nebo více upozornění.</span><span class="sxs-lookup"><span data-stu-id="29083-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="29083-104">Více čísel upozornění oddělte čárkou.</span><span class="sxs-lookup"><span data-stu-id="29083-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29083-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29083-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="29083-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="29083-106">Arguments</span></span>  
 <span data-ttu-id="29083-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="29083-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="29083-108">Čísla upozornění, která má kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="29083-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29083-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29083-109">Remarks</span></span>  
 <span data-ttu-id="29083-110">Měli byste zadat jenom číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="29083-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="29083-111">Například pokud chcete potlačit CS0028, můžete zadat `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="29083-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="29083-112">Kompilátor bude tiše ignorovat čísla upozornění předaná do `-nowarn` , která byla platná v předchozích verzích, ale byla odebrána z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="29083-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="29083-113">Například CS0679 byl platný v kompilátoru v aplikaci Visual Studio .NET 2002, ale byl následně odebrán.</span><span class="sxs-lookup"><span data-stu-id="29083-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="29083-114">Následující upozornění nelze potlačit pomocí `-nowarn` možnosti:</span><span class="sxs-lookup"><span data-stu-id="29083-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="29083-115">Upozornění kompilátoru (úroveň 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="29083-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="29083-116">Upozornění kompilátoru (úroveň 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="29083-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="29083-117">Upozornění kompilátoru (úroveň 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="29083-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="29083-118">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="29083-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="29083-119">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="29083-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="29083-120">Podrobnosti naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="29083-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="29083-121">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="29083-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="29083-122">Upravte vlastnost **potlačit upozornění** .</span><span class="sxs-lookup"><span data-stu-id="29083-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="29083-123">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="29083-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29083-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29083-124">See also</span></span>

- [<span data-ttu-id="29083-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="29083-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="29083-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="29083-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="29083-127">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="29083-127">C# Compiler Errors</span></span>](../compiler-messages/index.md)
