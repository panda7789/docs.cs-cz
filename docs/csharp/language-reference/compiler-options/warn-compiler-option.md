---
title: -Warn (C# možnosti kompilátoru)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602402"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="bc3e0-102">-Warn (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="bc3e0-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="bc3e0-103">Možnost **-warn** určuje úroveň upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc3e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc3e0-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc3e0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bc3e0-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="bc3e0-106">Úroveň upozornění, kterou chcete zobrazit pro kompilaci: Nižší čísla zobrazují pouze upozornění s vysokou závažností; vyšší čísla zobrazují více upozornění.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="bc3e0-107">Platné hodnoty jsou 0-4:</span><span class="sxs-lookup"><span data-stu-id="bc3e0-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="bc3e0-108">Úroveň upozornění</span><span class="sxs-lookup"><span data-stu-id="bc3e0-108">Warning level</span></span>|<span data-ttu-id="bc3e0-109">Význam</span><span class="sxs-lookup"><span data-stu-id="bc3e0-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="bc3e0-110">0</span><span class="sxs-lookup"><span data-stu-id="bc3e0-110">0</span></span>|<span data-ttu-id="bc3e0-111">Vypne emise všech varovných zpráv.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="bc3e0-112">1</span><span class="sxs-lookup"><span data-stu-id="bc3e0-112">1</span></span>|<span data-ttu-id="bc3e0-113">Zobrazí závažné varovné zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="bc3e0-114">2</span><span class="sxs-lookup"><span data-stu-id="bc3e0-114">2</span></span>|<span data-ttu-id="bc3e0-115">Zobrazí upozornění úrovně 1 a některá, méně závažná upozornění, například upozornění na skrývání členů třídy.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="bc3e0-116">3</span><span class="sxs-lookup"><span data-stu-id="bc3e0-116">3</span></span>|<span data-ttu-id="bc3e0-117">Zobrazí upozornění úrovně 2 plus určitá méně závažná upozornění, například upozornění na `true` výrazy, které vždy vyhodnotí nebo. `false`</span><span class="sxs-lookup"><span data-stu-id="bc3e0-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="bc3e0-118">4 (výchozí)</span><span class="sxs-lookup"><span data-stu-id="bc3e0-118">4 (the default)</span></span>|<span data-ttu-id="bc3e0-119">Zobrazí všechna upozornění úrovně 3 a informační upozornění.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc3e0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc3e0-120">Remarks</span></span>  
 <span data-ttu-id="bc3e0-121">Chcete-li získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu Nápověda.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="bc3e0-122">Další způsoby, jak získat informace o chybě nebo upozornění, najdete v tématu [ C# chyby kompilátoru](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc3e0-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="bc3e0-123">Pomocí [-warnaserror –](./warnaserror-compiler-option.md) považovat všechna upozornění za chyby.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-123">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="bc3e0-124">Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-124">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="bc3e0-125">**-w** je krátká forma **varování**.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bc3e0-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc3e0-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bc3e0-127">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bc3e0-128">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="bc3e0-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bc3e0-129">Upravte vlastnost **úroveň upozornění** .</span><span class="sxs-lookup"><span data-stu-id="bc3e0-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="bc3e0-130">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="bc3e0-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3e0-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc3e0-131">Example</span></span>  
 <span data-ttu-id="bc3e0-132">Kompilovat `in.cs` a mít jenom zobrazení upozornění úrovně 1 pro kompilátor:</span><span class="sxs-lookup"><span data-stu-id="bc3e0-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc3e0-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc3e0-133">See also</span></span>

- [<span data-ttu-id="bc3e0-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc3e0-134">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bc3e0-135">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="bc3e0-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
