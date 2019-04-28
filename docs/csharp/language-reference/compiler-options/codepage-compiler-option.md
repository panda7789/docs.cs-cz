---
title: -codepage (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662982"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="c6767-102">-codepage (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c6767-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="c6767-103">Tato možnost určuje, které znakovou stránku pro použití během kompilace, pokud se požadovaná stránka není aktuální výchozí znakovou stránku, která pro systém.</span><span class="sxs-lookup"><span data-stu-id="c6767-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6767-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6767-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="c6767-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c6767-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="c6767-106">Id stránky kód pro všechny soubory zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="c6767-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6767-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6767-107">Remarks</span></span>  
 <span data-ttu-id="c6767-108">Pokud kompilujete jeden nebo více souborů zdrojového kódu, které nebyly vytvořeny v počítači použít výchozí znakové stránky, můžete použít **- znaková stránka** možnost zadat znakovou stránku, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="c6767-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="c6767-109">**-codepage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="c6767-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="c6767-110">Pokud se stejnou znakovou stránku, která je v platnosti v počítači byly vytvořeny soubory zdrojového kódu nebo pokud soubory zdrojového kódu byly vytvořeny pomocí UNICODE nebo UTF-8, není nutné použít **- znaková stránka**.</span><span class="sxs-lookup"><span data-stu-id="c6767-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="c6767-111">Zobrazit [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informace o tom, jak najít kódu stránky jsou podporovány v systému.</span><span class="sxs-lookup"><span data-stu-id="c6767-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="c6767-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="c6767-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6767-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6767-113">See also</span></span>

- [<span data-ttu-id="c6767-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6767-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="c6767-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="c6767-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
