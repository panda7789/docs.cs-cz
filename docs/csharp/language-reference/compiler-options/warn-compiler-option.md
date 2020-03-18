---
title: -warn (Možnosti kompilátoru Jazyka C#)
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
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602402"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="d800c-102">-warn (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d800c-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="d800c-103">Možnost **-warn** určuje úroveň upozornění, aby se měl kompilátor zobrazit.</span><span class="sxs-lookup"><span data-stu-id="d800c-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d800c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d800c-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="d800c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d800c-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="d800c-106">Úroveň upozornění, kterou chcete zobrazit pro kompilaci: Nižší čísla zobrazují pouze upozornění vysoké závažnosti; vyšší čísla ukazují více varování.</span><span class="sxs-lookup"><span data-stu-id="d800c-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="d800c-107">Platné hodnoty jsou 0-4:</span><span class="sxs-lookup"><span data-stu-id="d800c-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="d800c-108">Úroveň varování</span><span class="sxs-lookup"><span data-stu-id="d800c-108">Warning level</span></span>|<span data-ttu-id="d800c-109">Význam</span><span class="sxs-lookup"><span data-stu-id="d800c-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="d800c-110">0</span><span class="sxs-lookup"><span data-stu-id="d800c-110">0</span></span>|<span data-ttu-id="d800c-111">Vypne emise všech varovných zpráv.</span><span class="sxs-lookup"><span data-stu-id="d800c-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="d800c-112">1</span><span class="sxs-lookup"><span data-stu-id="d800c-112">1</span></span>|<span data-ttu-id="d800c-113">Zobrazí závažné varovné zprávy.</span><span class="sxs-lookup"><span data-stu-id="d800c-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="d800c-114">2</span><span class="sxs-lookup"><span data-stu-id="d800c-114">2</span></span>|<span data-ttu-id="d800c-115">Zobrazí upozornění úrovně 1 a určitá méně závažná upozornění, například upozornění na skrytí členů třídy.</span><span class="sxs-lookup"><span data-stu-id="d800c-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="d800c-116">3</span><span class="sxs-lookup"><span data-stu-id="d800c-116">3</span></span>|<span data-ttu-id="d800c-117">Zobrazí upozornění úrovně 2 a určitá méně závažná upozornění, například `false`upozornění na výrazy, které jsou vždy vyhodnoceny nebo `true` .</span><span class="sxs-lookup"><span data-stu-id="d800c-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="d800c-118">4 (výchozí nastavení)</span><span class="sxs-lookup"><span data-stu-id="d800c-118">4 (the default)</span></span>|<span data-ttu-id="d800c-119">Zobrazí všechna upozornění úrovně 3 a informační upozornění.</span><span class="sxs-lookup"><span data-stu-id="d800c-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d800c-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d800c-120">Remarks</span></span>  
 <span data-ttu-id="d800c-121">Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="d800c-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="d800c-122">Další způsoby získání informací o chybě nebo upozornění naleznete v tématu [C# Compiler Errors](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="d800c-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="d800c-123">Použití [-warnaserror](./warnaserror-compiler-option.md) považovat všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d800c-123">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="d800c-124">Pomocí [funkce -nowarn](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="d800c-124">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="d800c-125">**-w** je krátká forma **-warn**.</span><span class="sxs-lookup"><span data-stu-id="d800c-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d800c-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d800c-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d800c-127">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="d800c-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d800c-128">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="d800c-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="d800c-129">Upravte vlastnost **Úroveň upozornění.**</span><span class="sxs-lookup"><span data-stu-id="d800c-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="d800c-130">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="d800c-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d800c-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="d800c-131">Example</span></span>  
 <span data-ttu-id="d800c-132">Zkompilujte `in.cs` a mají kompilátor pouze zobrazení úrovně 1 upozornění:</span><span class="sxs-lookup"><span data-stu-id="d800c-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d800c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d800c-133">See also</span></span>

- [<span data-ttu-id="d800c-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d800c-134">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d800c-135">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="d800c-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
