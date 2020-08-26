---
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
ms.openlocfilehash: d495ef76dc390d8dd2a361d5530f9e39d7128b3e
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867604"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="cdb4a-102">-Warn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="cdb4a-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="cdb4a-103">Možnost **-warn** určuje úroveň upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdb4a-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="cdb4a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cdb4a-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="cdb4a-106">Úroveň upozornění, kterou chcete zobrazit pro kompilaci: nižší čísla zobrazují pouze upozornění s vysokou závažností; vyšší čísla zobrazují více upozornění.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="cdb4a-107">Hodnota musí být nula nebo kladné celé číslo:</span><span class="sxs-lookup"><span data-stu-id="cdb4a-107">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="cdb4a-108">Úroveň upozornění</span><span class="sxs-lookup"><span data-stu-id="cdb4a-108">Warning level</span></span>|<span data-ttu-id="cdb4a-109">Význam</span><span class="sxs-lookup"><span data-stu-id="cdb4a-109">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="cdb4a-110">0</span><span class="sxs-lookup"><span data-stu-id="cdb4a-110">0</span></span>|<span data-ttu-id="cdb4a-111">Vypne emise všech varovných zpráv.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-111">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="cdb4a-112">1</span><span class="sxs-lookup"><span data-stu-id="cdb4a-112">1</span></span>|<span data-ttu-id="cdb4a-113">Zobrazí závažné varovné zprávy.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="cdb4a-114">2</span><span class="sxs-lookup"><span data-stu-id="cdb4a-114">2</span></span>|<span data-ttu-id="cdb4a-115">Zobrazí upozornění úrovně 1 a některá, méně závažná upozornění, například upozornění na skrývání členů třídy.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="cdb4a-116">3</span><span class="sxs-lookup"><span data-stu-id="cdb4a-116">3</span></span>|<span data-ttu-id="cdb4a-117">Zobrazí upozornění úrovně 2 plus určitá méně závažná upozornění, například upozornění na výrazy, které vždy vyhodnotí `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="cdb4a-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="cdb4a-118">4 (výchozí)</span><span class="sxs-lookup"><span data-stu-id="cdb4a-118">4 (the default)</span></span>|<span data-ttu-id="cdb4a-119">Zobrazí všechna upozornění úrovně 3 a informační upozornění.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-119">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="cdb4a-120">5</span><span class="sxs-lookup"><span data-stu-id="cdb4a-120">5</span></span>|<span data-ttu-id="cdb4a-121">Zobrazí upozornění úrovně 4 a [Další upozornění](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) z kompilátoru dodaného s C# 9,0.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-121">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="cdb4a-122">Větší než 5</span><span class="sxs-lookup"><span data-stu-id="cdb4a-122">Greater than 5</span></span>|<span data-ttu-id="cdb4a-123">Jakákoli hodnota vyšší než 5 bude zpracována jako 5.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-123">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="cdb4a-124">Obecně umísťujete libovolnou velkou hodnotu (například), `9999` abyste měli jistotu, že budete mít vždy všechna upozornění, pokud je kompilátor aktualizován novými úrovněmi upozornění.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-124">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="cdb4a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdb4a-125">Remarks</span></span>  
 <span data-ttu-id="cdb4a-126">Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu Nápověda.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-126">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="cdb4a-127">Další způsoby, jak získat informace o chybě nebo upozornění, najdete v tématu [chyby kompilátoru jazyka C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="cdb4a-127">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="cdb4a-128">Pomocí [-warnaserror –](./warnaserror-compiler-option.md) považovat všechna upozornění za chyby.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-128">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="cdb4a-129">Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-129">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="cdb4a-130">**-w** je krátká forma **varování**.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-130">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cdb4a-131">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cdb4a-131">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="cdb4a-132">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="cdb4a-132">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="cdb4a-133">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="cdb4a-133">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="cdb4a-134">Upravte vlastnost **úroveň upozornění** .</span><span class="sxs-lookup"><span data-stu-id="cdb4a-134">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="cdb4a-135">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> .</span><span class="sxs-lookup"><span data-stu-id="cdb4a-135">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb4a-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdb4a-136">Example</span></span>  
 <span data-ttu-id="cdb4a-137">Kompilovat `in.cs` a mít jenom zobrazení upozornění úrovně 1 pro kompilátor:</span><span class="sxs-lookup"><span data-stu-id="cdb4a-137">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdb4a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdb4a-138">See also</span></span>

- [<span data-ttu-id="cdb4a-139">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="cdb4a-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cdb4a-140">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="cdb4a-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
