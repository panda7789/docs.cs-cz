---
title: -bugreport (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 6e4674acd2a5edbbffd2babf130d2078019ab9b7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517000"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="0e547-102">-bugreport (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0e547-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="0e547-103">Určuje, že informace o ladění by měly být umístěny v souboru pro pozdější analýzu.</span><span class="sxs-lookup"><span data-stu-id="0e547-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e547-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e547-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e547-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0e547-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="0e547-106">Název souboru, který má obsahovat hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="0e547-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e547-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e547-107">Remarks</span></span>  
 <span data-ttu-id="0e547-108">**- Bugreport** možnost určuje, že tyto informace mají být umístěny v `file`:</span><span class="sxs-lookup"><span data-stu-id="0e547-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="0e547-109">Kopírování všech souborů zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="0e547-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="0e547-110">Seznam možností kompilátoru použita při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="0e547-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="0e547-111">Informace o verzi kompilátoru, běhu a operačního systému.</span><span class="sxs-lookup"><span data-stu-id="0e547-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="0e547-112">Odkazovaná sestavení a modulů, které jsou uloženy jako šestnáctkové číslice, s výjimkou sestavení, které se dodávají pomocí rozhraní .NET Framework a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0e547-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="0e547-113">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="0e547-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="0e547-114">Popis problému, který zobrazí se výzva k zadání.</span><span class="sxs-lookup"><span data-stu-id="0e547-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="0e547-115">Popis jak domníváte, že problém je třeba stanovit, která vám zobrazí výzva k zadání.</span><span class="sxs-lookup"><span data-stu-id="0e547-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="0e547-116">Pokud tato možnost se používá s **- errorreport: řádku** nebo **- errorreport: Odeslat**, informace v souboru se odešlou do Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="0e547-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="0e547-117">Vzhledem k tomu, že kopie všech souborů zdrojového kódu budou umístěny v `file`, můžete chtít reprodukovat v nejkratší možné aplikaci podezřelý kód.</span><span class="sxs-lookup"><span data-stu-id="0e547-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="0e547-118">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="0e547-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="0e547-119">Všimněte si, že obsah generovaný soubor vystavit zdrojový kód, který může dojít k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="0e547-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e547-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e547-120">See Also</span></span>  

- [<span data-ttu-id="0e547-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0e547-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="0e547-122">-errorreport (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0e547-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
- [<span data-ttu-id="0e547-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0e547-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
