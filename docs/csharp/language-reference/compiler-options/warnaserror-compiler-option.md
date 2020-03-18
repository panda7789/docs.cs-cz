---
title: -warnaserror (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503477"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="4e4da-102">-warnaserror (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="4e4da-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="4e4da-103">Možnost **-warnaserror+** považuje všechna upozornění za chyby.</span><span class="sxs-lookup"><span data-stu-id="4e4da-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e4da-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e4da-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e4da-105">Remarks</span></span>  
 <span data-ttu-id="4e4da-106">Všechny zprávy, které by obvykle být hlášeny jako upozornění jsou místo toho hlášeny jako chyby a proces sestavení je zastaven (jsou vytvořeny žádné výstupní soubory).</span><span class="sxs-lookup"><span data-stu-id="4e4da-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="4e4da-107">Ve výchozím nastavení **-warnaserror-** je v platnosti, což způsobí, že upozornění nezabrání generování výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="4e4da-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="4e4da-108">**-warnaserror**, který je stejný jako **-warnaserror+**, způsobí, že upozornění považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="4e4da-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="4e4da-109">Volitelně pokud chcete, aby pouze několik konkrétních upozornění bylo považováno za chyby, můžete zadat seznam čísel upozornění oddělených čárkami, který bude považován za chyby.</span><span class="sxs-lookup"><span data-stu-id="4e4da-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="4e4da-110">Sadu všech upozornění nullability lze zadat s **nullable zkratka.**</span><span class="sxs-lookup"><span data-stu-id="4e4da-110">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="4e4da-111">Pomocí [-warn](./warn-compiler-option.md) určete úroveň upozornění, kterou má kompilátor zobrazit.</span><span class="sxs-lookup"><span data-stu-id="4e4da-111">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="4e4da-112">Pomocí [funkce -nowarn](./nowarn-compiler-option.md) můžete zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="4e4da-112">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4e4da-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e4da-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4e4da-114">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="4e4da-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4e4da-115">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="4e4da-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="4e4da-116">Upravte **vlastnost Považovat upozornění za chyby.**</span><span class="sxs-lookup"><span data-stu-id="4e4da-116">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="4e4da-117">Chcete-li tuto možnost kompilátoru nastavit programově, přečtěte si téma <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="4e4da-117">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e4da-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e4da-118">Example</span></span>  
 <span data-ttu-id="4e4da-119">Kompilace `in.cs` a mít kompilátor zobrazit žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="4e4da-119">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e4da-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e4da-120">See also</span></span>

- [<span data-ttu-id="4e4da-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e4da-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4e4da-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4e4da-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
