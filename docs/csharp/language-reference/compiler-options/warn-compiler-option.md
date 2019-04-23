---
title: -warn (možnosti kompilátoru C#)
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
ms.openlocfilehash: 17dd992edbec5ce444b53ed42b2b486282618672
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315800"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="c8516-102">-warn (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c8516-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="c8516-103">**-Warn** určuje úroveň upozornění kompilátoru k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c8516-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8516-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8516-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8516-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="c8516-106">Úroveň pro upozornění, které má být zobrazen pro kompilace: Nižší číslice zobrazit pouze vysokou závažností upozornění; vyšší čísla popisují další varování.</span><span class="sxs-lookup"><span data-stu-id="c8516-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="c8516-107">Platné hodnoty jsou 0-4:</span><span class="sxs-lookup"><span data-stu-id="c8516-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="c8516-108">Úroveň upozornění</span><span class="sxs-lookup"><span data-stu-id="c8516-108">Warning level</span></span>|<span data-ttu-id="c8516-109">Význam</span><span class="sxs-lookup"><span data-stu-id="c8516-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="c8516-110">0</span><span class="sxs-lookup"><span data-stu-id="c8516-110">0</span></span>|<span data-ttu-id="c8516-111">Vypne emise všechny zprávy upozornění.</span><span class="sxs-lookup"><span data-stu-id="c8516-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="c8516-112">1</span><span class="sxs-lookup"><span data-stu-id="c8516-112">1</span></span>|<span data-ttu-id="c8516-113">Zobrazuje závažná upozornění.</span><span class="sxs-lookup"><span data-stu-id="c8516-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="c8516-114">2</span><span class="sxs-lookup"><span data-stu-id="c8516-114">2</span></span>|<span data-ttu-id="c8516-115">Zobrazí upozornění úrovně 1 a některé, méně závažných upozornění, jako jsou třeba upozornění o skrývání členů třídy.</span><span class="sxs-lookup"><span data-stu-id="c8516-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="c8516-116">3</span><span class="sxs-lookup"><span data-stu-id="c8516-116">3</span></span>|<span data-ttu-id="c8516-117">Zobrazí upozornění úrovně 2 a některé, méně závažných upozornění, jako jsou třeba upozornění, která se vždycky vyhodnotí výrazy `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c8516-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="c8516-118">4 (výchozí)</span><span class="sxs-lookup"><span data-stu-id="c8516-118">4 (the default)</span></span>|<span data-ttu-id="c8516-119">Zobrazí všechna upozornění úrovně 3 a informační upozornění.</span><span class="sxs-lookup"><span data-stu-id="c8516-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8516-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8516-120">Remarks</span></span>  
 <span data-ttu-id="c8516-121">Pokud chcete získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="c8516-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="c8516-122">Další způsoby, jak získat informace o chybě nebo upozornění, najdete v části [chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8516-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="c8516-123">Použití [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) považovat všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="c8516-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="c8516-124">Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="c8516-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="c8516-125">**-w** je zkratka pro **-warn**.</span><span class="sxs-lookup"><span data-stu-id="c8516-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8516-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8516-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c8516-127">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="c8516-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c8516-128">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="c8516-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="c8516-129">Upravit **úroveň pro upozornění** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8516-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="c8516-130">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8516-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8516-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8516-131">Example</span></span>  
 <span data-ttu-id="c8516-132">Kompilace `in.cs` kompilátor zobrazí pouze upozornění úrovně 1:</span><span class="sxs-lookup"><span data-stu-id="c8516-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8516-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8516-133">See also</span></span>

- [<span data-ttu-id="c8516-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8516-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="c8516-135">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="c8516-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
