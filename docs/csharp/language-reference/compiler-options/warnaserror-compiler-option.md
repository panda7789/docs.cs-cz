---
title: "-warnaserror (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a341fe9760d7fdb0e4df7046cf356e550b4adb9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="531c5-102">-warnaserror (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="531c5-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="531c5-103">**- Warnaserror +** možnost zpracovává všech upozornění jako chyby</span><span class="sxs-lookup"><span data-stu-id="531c5-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="531c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="531c5-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="531c5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="531c5-105">Remarks</span></span>  
 <span data-ttu-id="531c5-106">Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby a procesu sestavení je zastaveno (žádný výstup, které jsou vytvořené soubory).</span><span class="sxs-lookup"><span data-stu-id="531c5-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="531c5-107">Ve výchozím nastavení **- warnaserror –** je v platnosti, což způsobí, že upozornění nezabrání generování výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="531c5-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="531c5-108">**-warnaserror**, což je stejný jako **- warnaserror +**, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="531c5-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="531c5-109">Případně pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="531c5-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="531c5-110">Použití [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) k určení úrovně upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="531c5-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="531c5-111">Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat některé upozornění.</span><span class="sxs-lookup"><span data-stu-id="531c5-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="531c5-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="531c5-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="531c5-113">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="531c5-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="531c5-114">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="531c5-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="531c5-115">Změnit **považovat upozornění jako chyby** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="531c5-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="531c5-116">Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="531c5-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="531c5-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="531c5-117">Example</span></span>  
 <span data-ttu-id="531c5-118">Kompilace `in.cs` kompilátor zobrazovat žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="531c5-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="531c5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="531c5-119">See Also</span></span>  
 [<span data-ttu-id="531c5-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="531c5-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="531c5-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="531c5-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
