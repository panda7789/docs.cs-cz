---
title: -warnaserror – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606247"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="61f3c-102">-warnaserror – (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="61f3c-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="61f3c-103">Parametr **-warnaserror – +** zpracovává všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="61f3c-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61f3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61f3c-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="61f3c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61f3c-105">Remarks</span></span>  
 <span data-ttu-id="61f3c-106">Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby a proces sestavení se zastaví (nejsou sestaveny žádné výstupní soubory).</span><span class="sxs-lookup"><span data-stu-id="61f3c-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="61f3c-107">Ve výchozím nastavení je **-warnaserror –-** v platnosti, což způsobí, že upozornění nebrání generování výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="61f3c-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="61f3c-108">**-warnaserror –** , který je stejný jako **-warnaserror – +** , způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="61f3c-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="61f3c-109">Případně, pokud chcete, aby bylo možné považovat jenom několik specifických upozornění jako chyby, můžete zadat čárkami oddělený seznam čísel upozornění, které se budou považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="61f3c-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="61f3c-110">Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="61f3c-110">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="61f3c-111">Pomocí [-Upozornění](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="61f3c-111">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="61f3c-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="61f3c-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="61f3c-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="61f3c-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="61f3c-114">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="61f3c-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="61f3c-115">Upravte vlastnost **považovat upozornění jako chybu** .</span><span class="sxs-lookup"><span data-stu-id="61f3c-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="61f3c-116">Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>, přečtěte si téma.</span><span class="sxs-lookup"><span data-stu-id="61f3c-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61f3c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="61f3c-117">Example</span></span>  
 <span data-ttu-id="61f3c-118">Kompilovat `in.cs` a nechat kompilátor zobrazovat žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="61f3c-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="61f3c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61f3c-119">See also</span></span>

- [<span data-ttu-id="61f3c-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61f3c-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="61f3c-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="61f3c-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
