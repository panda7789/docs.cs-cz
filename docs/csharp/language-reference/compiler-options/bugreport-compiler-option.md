---
title: "-bugreport (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1341383d48a28966a0873f3124cdc3567ec3f76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bugreport-c-compiler-options"></a><span data-ttu-id="f1bbe-102">/bugreport (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f1bbe-102">/bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="f1bbe-103">Určuje, že informace o ladění mají být umístěny v souboru pro pozdější analýzu.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1bbe-104">Syntax</span></span>  
  
```console  
/bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1bbe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1bbe-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="f1bbe-106">Název souboru, který má obsahovat sestavy chyb.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1bbe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1bbe-107">Remarks</span></span>  
 <span data-ttu-id="f1bbe-108">**/Bugreport** možnost určuje, že tyto informace mají být umístěny v `file`:</span><span class="sxs-lookup"><span data-stu-id="f1bbe-108">The **/bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="f1bbe-109">Kopírovat všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="f1bbe-110">Seznam možností kompilátoru použita při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="f1bbe-111">Informace o verzi o kompilátoru, běhu a operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="f1bbe-112">Odkazovaná sestavení a moduly, které jsou uloženy jako šestnáctkové číslice, s výjimkou sestavení, které jsou dodávány pomocí rozhraní .NET Framework a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="f1bbe-113">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="f1bbe-114">Popis problému, který jste vyzváni k.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="f1bbe-115">Popis jak domníváte, že problém je třeba stanovit, které jste vyzváni k.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="f1bbe-116">Pokud tato možnost se používá s **/errorreport:prompt** nebo **/errorreport:send**, informace v souboru budou odeslány společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-116">If this option is used with **/errorreport:prompt** or **/errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="f1bbe-117">Protože kopii všechny soubory zdrojového kódu budou umístěny v `file`, můžete chtít reprodukovat možného kód do nejkratší programu.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="f1bbe-118">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="f1bbe-119">Všimněte si, že obsah vygenerovaný soubor vystavit zdrojový kód, který by mohl vést k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="f1bbe-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bbe-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1bbe-120">See Also</span></span>  
 [<span data-ttu-id="f1bbe-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="f1bbe-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="f1bbe-122">/ errorreport (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f1bbe-122">/errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [<span data-ttu-id="f1bbe-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f1bbe-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
