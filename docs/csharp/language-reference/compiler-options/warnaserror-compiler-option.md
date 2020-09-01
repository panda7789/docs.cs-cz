---
description: -warnaserror – (možnosti kompilátoru C#)
title: -warnaserror – (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 3ccd4546402dbc8e5d9245af6411ba2d831d4959
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127240"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="ebc59-103">-warnaserror – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ebc59-103">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="ebc59-104">Parametr **-warnaserror – +** zpracovává všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="ebc59-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc59-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebc59-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ebc59-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebc59-106">Remarks</span></span>  
 <span data-ttu-id="ebc59-107">Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby a proces sestavení se zastaví (nejsou sestaveny žádné výstupní soubory).</span><span class="sxs-lookup"><span data-stu-id="ebc59-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="ebc59-108">Ve výchozím nastavení je **-warnaserror –-** v platnosti, což způsobí, že upozornění nebrání generování výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="ebc59-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="ebc59-109">**-warnaserror –**, který je stejný jako **-warnaserror – +**, způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="ebc59-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="ebc59-110">Případně, pokud chcete, aby bylo možné považovat jenom několik specifických upozornění jako chyby, můžete zadat čárkami oddělený seznam čísel upozornění, které se budou považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="ebc59-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="ebc59-111">Sada všech upozornění s hodnotou null se dá zadat s zkráceným **připouštějící hodnotu null** .</span><span class="sxs-lookup"><span data-stu-id="ebc59-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="ebc59-112">Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="ebc59-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="ebc59-113">Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="ebc59-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ebc59-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ebc59-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ebc59-115">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="ebc59-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ebc59-116">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="ebc59-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ebc59-117">Upravte vlastnost **považovat upozornění jako chybu** .</span><span class="sxs-lookup"><span data-stu-id="ebc59-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="ebc59-118">Chcete-li nastavit tuto možnost kompilátoru programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors> .</span><span class="sxs-lookup"><span data-stu-id="ebc59-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebc59-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebc59-119">Example</span></span>  
 <span data-ttu-id="ebc59-120">Kompilovat `in.cs` a nechat kompilátor zobrazovat žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="ebc59-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebc59-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebc59-121">See also</span></span>

- [<span data-ttu-id="ebc59-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ebc59-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ebc59-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ebc59-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
