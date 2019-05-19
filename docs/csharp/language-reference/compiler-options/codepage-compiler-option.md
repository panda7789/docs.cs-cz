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
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876930"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="07f79-102">-codepage (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="07f79-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="07f79-103">Tato možnost určuje, které znakovou stránku pro použití během kompilace, pokud se požadovaná stránka není aktuální výchozí znakovou stránku, která pro systém.</span><span class="sxs-lookup"><span data-stu-id="07f79-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07f79-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="07f79-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="07f79-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="07f79-106">Id stránky kód pro všechny soubory zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="07f79-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07f79-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07f79-107">Remarks</span></span>  
 <span data-ttu-id="07f79-108">Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="07f79-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="07f79-109">Pokud soubory zdrojového kódu jsou v kódování jiné než v kódování UTF-8 a použijte jiné znaky než 7bitových znaků ASCII, použijte **- znaková stránka** možnost zadat znakovou stránku, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="07f79-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="07f79-110">**-codepage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="07f79-110">**-codepage** applies to all source code files in your compilation.</span></span>  
    
 <span data-ttu-id="07f79-111">Zobrazit [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informace o tom, jak najít kódu stránky jsou podporovány v systému.</span><span class="sxs-lookup"><span data-stu-id="07f79-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="07f79-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="07f79-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f79-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07f79-113">See also</span></span>

- [<span data-ttu-id="07f79-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07f79-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="07f79-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="07f79-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
