---
description: -Warn (možnosti kompilátoru C#)
title: -Warn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 55e80d0bd05e2119154210503bb277d743050e18
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139070"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="4597d-103">-Warn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4597d-103">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="4597d-104">Možnost **-warn** určuje úroveň upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="4597d-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4597d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4597d-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="4597d-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4597d-106">Arguments</span></span>  
 `option`  
 <span data-ttu-id="4597d-107">Úroveň upozornění, kterou chcete zobrazit pro kompilaci: nižší čísla zobrazují pouze upozornění s vysokou závažností; vyšší čísla zobrazují více upozornění.</span><span class="sxs-lookup"><span data-stu-id="4597d-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="4597d-108">Hodnota musí být nula nebo kladné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="4597d-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="4597d-109">Úroveň upozornění</span><span class="sxs-lookup"><span data-stu-id="4597d-109">Warning level</span></span>|<span data-ttu-id="4597d-110">Význam</span><span class="sxs-lookup"><span data-stu-id="4597d-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="4597d-111">0</span><span class="sxs-lookup"><span data-stu-id="4597d-111">0</span></span>|<span data-ttu-id="4597d-112">Vypne emise všech varovných zpráv.</span><span class="sxs-lookup"><span data-stu-id="4597d-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="4597d-113">1</span><span class="sxs-lookup"><span data-stu-id="4597d-113">1</span></span>|<span data-ttu-id="4597d-114">Zobrazí závažné varovné zprávy.</span><span class="sxs-lookup"><span data-stu-id="4597d-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="4597d-115">2</span><span class="sxs-lookup"><span data-stu-id="4597d-115">2</span></span>|<span data-ttu-id="4597d-116">Zobrazí upozornění úrovně 1 a některá, méně závažná upozornění, například upozornění na skrývání členů třídy.</span><span class="sxs-lookup"><span data-stu-id="4597d-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="4597d-117">3</span><span class="sxs-lookup"><span data-stu-id="4597d-117">3</span></span>|<span data-ttu-id="4597d-118">Zobrazí upozornění úrovně 2 plus určitá méně závažná upozornění, například upozornění na výrazy, které vždy vyhodnotí `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="4597d-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="4597d-119">4 (výchozí)</span><span class="sxs-lookup"><span data-stu-id="4597d-119">4 (the default)</span></span>|<span data-ttu-id="4597d-120">Zobrazí všechna upozornění úrovně 3 a informační upozornění.</span><span class="sxs-lookup"><span data-stu-id="4597d-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="4597d-121">5</span><span class="sxs-lookup"><span data-stu-id="4597d-121">5</span></span>|<span data-ttu-id="4597d-122">Zobrazí upozornění úrovně 4 a [Další upozornění](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) z kompilátoru dodaného s C# 9,0.</span><span class="sxs-lookup"><span data-stu-id="4597d-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="4597d-123">Větší než 5</span><span class="sxs-lookup"><span data-stu-id="4597d-123">Greater than 5</span></span>|<span data-ttu-id="4597d-124">Jakákoli hodnota vyšší než 5 bude zpracována jako 5.</span><span class="sxs-lookup"><span data-stu-id="4597d-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="4597d-125">Obecně umísťujete libovolnou velkou hodnotu (například), `9999` abyste měli jistotu, že budete mít vždy všechna upozornění, pokud je kompilátor aktualizován novými úrovněmi upozornění.</span><span class="sxs-lookup"><span data-stu-id="4597d-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="4597d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4597d-126">Remarks</span></span>  
 <span data-ttu-id="4597d-127">Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu Nápověda.</span><span class="sxs-lookup"><span data-stu-id="4597d-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="4597d-128">Další způsoby, jak získat informace o chybě nebo upozornění, najdete v tématu [chyby kompilátoru jazyka C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="4597d-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="4597d-129">Pomocí [-warnaserror –](./warnaserror-compiler-option.md) považovat všechna upozornění za chyby.</span><span class="sxs-lookup"><span data-stu-id="4597d-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="4597d-130">Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="4597d-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="4597d-131">**-w** je krátká forma **varování**.</span><span class="sxs-lookup"><span data-stu-id="4597d-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4597d-132">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4597d-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4597d-133">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="4597d-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4597d-134">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="4597d-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="4597d-135">Upravte vlastnost **úroveň upozornění** .</span><span class="sxs-lookup"><span data-stu-id="4597d-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="4597d-136">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> .</span><span class="sxs-lookup"><span data-stu-id="4597d-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4597d-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="4597d-137">Example</span></span>  
 <span data-ttu-id="4597d-138">Kompilovat `in.cs` a mít jenom zobrazení upozornění úrovně 1 pro kompilátor:</span><span class="sxs-lookup"><span data-stu-id="4597d-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4597d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4597d-139">See also</span></span>

- [<span data-ttu-id="4597d-140">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="4597d-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4597d-141">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4597d-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
