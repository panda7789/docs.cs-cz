---
description: -bugreport – (možnosti kompilátoru C#)
title: -bugreport – (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2c358b2dda400f6077ffb5ba1dfc8e6e1127fa52
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125992"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="083e9-103">-bugreport – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="083e9-103">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="083e9-104">Určuje, že informace o ladění by měly být umístěny do souboru pro pozdější analýzu.</span><span class="sxs-lookup"><span data-stu-id="083e9-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="083e9-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="083e9-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="083e9-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="083e9-107">Název souboru, který má obsahovat zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="083e9-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="083e9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="083e9-108">Remarks</span></span>  
 <span data-ttu-id="083e9-109">Možnost **-bugreport –** určuje, že se mají umístit následující informace `file` :</span><span class="sxs-lookup"><span data-stu-id="083e9-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="083e9-110">Kopie všech souborů zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="083e9-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="083e9-111">Seznam možností kompilátoru použitých v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="083e9-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="083e9-112">Informace o verzi kompilátoru, době běhu a operačním systému.</span><span class="sxs-lookup"><span data-stu-id="083e9-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="083e9-113">Odkazovaná sestavení a moduly uložené jako šestnáctkové číslice, s výjimkou sestavení, která jsou dodávána s .NET Framework a sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="083e9-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="083e9-114">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="083e9-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="083e9-115">Popis problému, ke kterému se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="083e9-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="083e9-116">Popis toho, jak si myslíte problém, by měl být opravený, na který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="083e9-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="083e9-117">Pokud se tato možnost používá s parametrem **-errorreport: prompt** nebo **-errorreport: Send**, informace v souboru se odešlou společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="083e9-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="083e9-118">Vzhledem k tomu, že se kopie všech souborů zdrojového kódu umístí do `file` , může být vhodné reprodukce podezřelého kódu reprodukována v co nejkratším možném programu.</span><span class="sxs-lookup"><span data-stu-id="083e9-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="083e9-119">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="083e9-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="083e9-120">Všimněte si, že obsah generovaného souboru zveřejňuje zdrojový kód, který by mohl vést k neúmyslnému zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="083e9-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083e9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="083e9-121">See also</span></span>

- [<span data-ttu-id="083e9-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="083e9-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="083e9-123">-errorreport (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="083e9-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="083e9-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="083e9-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
