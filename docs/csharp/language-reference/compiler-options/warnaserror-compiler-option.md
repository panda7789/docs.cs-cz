---
title: "-warnaserror (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28c2cdc26d32d98e617a0c4b8cd282d2fbc87f4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-c-compiler-options"></a><span data-ttu-id="574cc-102">/warnaserror (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="574cc-102">/warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="574cc-103">**/Warnaserror+** možnost zpracovává všech upozornění jako chyby</span><span class="sxs-lookup"><span data-stu-id="574cc-103">The **/warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="574cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="574cc-104">Syntax</span></span>  
  
```console  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="574cc-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="574cc-105">Remarks</span></span>  
 <span data-ttu-id="574cc-106">Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby a procesu sestavení je zastaveno (žádný výstup, které jsou vytvořené soubory).</span><span class="sxs-lookup"><span data-stu-id="574cc-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="574cc-107">Ve výchozím nastavení **/warnaserror-** je v platnosti, což způsobí, že upozornění nezabrání generování výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="574cc-107">By default, **/warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="574cc-108">**/ warnaserror**, což je stejný jako **/warnaserror+**, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="574cc-108">**/warnaserror**, which is the same as **/warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="574cc-109">Případně pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="574cc-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="574cc-110">Použití [/ warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) k určení úrovně upozornění, která má kompilátor zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="574cc-110">Use [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="574cc-111">Použití [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat některé upozornění.</span><span class="sxs-lookup"><span data-stu-id="574cc-111">Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="574cc-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="574cc-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="574cc-113">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="574cc-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="574cc-114">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="574cc-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="574cc-115">Změnit **považovat upozornění jako chyby** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="574cc-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
     <span data-ttu-id="574cc-116">Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="574cc-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="574cc-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="574cc-117">Example</span></span>  
 <span data-ttu-id="574cc-118">Kompilace `in.cs` kompilátor zobrazovat žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="574cc-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="574cc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="574cc-119">See Also</span></span>  
 [<span data-ttu-id="574cc-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="574cc-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="574cc-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="574cc-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
