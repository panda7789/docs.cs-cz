---
title: -warnaserror (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662254"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="5b565-102">-warnaserror (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5b565-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="5b565-103">**- Warnaserror +** možnost zpracuje všechna upozornění jako chyby</span><span class="sxs-lookup"><span data-stu-id="5b565-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b565-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b565-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b565-105">Remarks</span></span>  
 <span data-ttu-id="5b565-106">Všechny zprávy, které by obvykle hlášeny jako varování jsou hlášeny jako chyby a proces sestavení je zastavení (žádné výstupní soubory jsou vytvořeny).</span><span class="sxs-lookup"><span data-stu-id="5b565-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="5b565-107">Ve výchozím nastavení **- warnaserror –** je v platnosti, což způsobí, že upozornění nezabrání generování výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="5b565-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="5b565-108">**-warnaserror**, což je stejná jako **- warnaserror +**, způsobí upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="5b565-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="5b565-109">Pokud chcete pouze několik specifická upozornění budou považována za chyby, můžete volitelně zadat čárkou oddělený seznam čísel upozornění pro nakládání s chybami.</span><span class="sxs-lookup"><span data-stu-id="5b565-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="5b565-110">Použití [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) k určení úrovně upozornění, která má kompilátor pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5b565-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="5b565-111">Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="5b565-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5b565-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5b565-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5b565-113">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="5b565-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="5b565-114">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="5b565-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="5b565-115">Upravit **zpracovávat upozornění jako chyby** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b565-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="5b565-116">Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="5b565-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b565-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b565-117">Example</span></span>  
 <span data-ttu-id="5b565-118">Kompilace `in.cs` kompilátor zobrazovat žádné upozornění:</span><span class="sxs-lookup"><span data-stu-id="5b565-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b565-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b565-119">See also</span></span>

- [<span data-ttu-id="5b565-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b565-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="5b565-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="5b565-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
