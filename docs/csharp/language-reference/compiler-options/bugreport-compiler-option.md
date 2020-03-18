---
title: -bugreport (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603078"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="01f95-102">-bugreport (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="01f95-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="01f95-103">Určuje, že informace o ladění by měly být umístěny do souboru pro pozdější analýzu.</span><span class="sxs-lookup"><span data-stu-id="01f95-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f95-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="01f95-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="01f95-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="01f95-106">Název souboru, který má obsahovat hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="01f95-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f95-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01f95-107">Remarks</span></span>  
 <span data-ttu-id="01f95-108">Možnost **-bugreport** určuje, že následující informace `file`by měly být umístěny v :</span><span class="sxs-lookup"><span data-stu-id="01f95-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="01f95-109">Kopie všech souborů zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="01f95-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="01f95-110">Seznam možností kompilátoru použitých v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="01f95-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="01f95-111">Informace o verzi kompilátoru, běhu a operačním systému.</span><span class="sxs-lookup"><span data-stu-id="01f95-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="01f95-112">Odkazovaná sestavení a moduly uložené jako šestnáctkové číslice s výjimkou sestavení, která jsou dodávána s rozhraním .NET Framework a SadM SDK.</span><span class="sxs-lookup"><span data-stu-id="01f95-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="01f95-113">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="01f95-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="01f95-114">Popis problému, ke kterému budete vyzváni.</span><span class="sxs-lookup"><span data-stu-id="01f95-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="01f95-115">Popis toho, jak si myslíte, že by měl být problém opraven, k jakému budete vyzváni.</span><span class="sxs-lookup"><span data-stu-id="01f95-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="01f95-116">Pokud je tato možnost použita s **-errorreport:prompt** nebo **-errorreport:send**, budou informace v souboru odeslány společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="01f95-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="01f95-117">Vzhledem k tomu, že kopie `file`všech souborů zdrojového kódu bude umístěna do aplikace , můžete chtít reprodukovat podezřelou vadu kódu v co nejkratším možném programu.</span><span class="sxs-lookup"><span data-stu-id="01f95-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="01f95-118">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="01f95-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="01f95-119">Všimněte si, že obsah generovaného souboru vystavit zdrojový kód, který by mohl mít za následek neúmyslné zpřístupnění informací.</span><span class="sxs-lookup"><span data-stu-id="01f95-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f95-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="01f95-120">See also</span></span>

- [<span data-ttu-id="01f95-121">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01f95-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="01f95-122">-errorreport (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="01f95-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="01f95-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="01f95-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
