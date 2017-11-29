---
title: "-codepage (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37f40312f1218b8e666eae7cb2de6c768ee32108
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="codepage-c-compiler-options"></a><span data-ttu-id="bbca5-102">/codepage (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="bbca5-102">/codepage (C# Compiler Options)</span></span>
<span data-ttu-id="bbca5-103">Tato možnost určuje, které znakovou stránku pro použití během kompilace, pokud se požadovaná stránka není aktuální výchozí znaková stránka pro systém.</span><span class="sxs-lookup"><span data-stu-id="bbca5-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbca5-104">Syntax</span></span>  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="bbca5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bbca5-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="bbca5-106">Id znaková stránka pro všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="bbca5-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbca5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbca5-107">Remarks</span></span>  
 <span data-ttu-id="bbca5-108">Pokud je jeden nebo více soubory zdrojového kódu, které nebyly vytvořeny používat výchozí znakovou stránku ve vašem počítači, můžete použít **/CODEPAGE** možnost zadat znakovou stránku, která má být použita.</span><span class="sxs-lookup"><span data-stu-id="bbca5-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **/codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="bbca5-109">**/ codePage** se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="bbca5-109">**/codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="bbca5-110">Pokud soubory zdrojového kódu, které byly vytvořeny pomocí stejné znakové stránky, která je umístěna ve vašem počítači nebo pokud soubory zdrojového kódu se vytvořily s UNICODE nebo UTF-8, není nutné použít **/CODEPAGE**.</span><span class="sxs-lookup"><span data-stu-id="bbca5-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **/codepage**.</span></span>  
  
 <span data-ttu-id="bbca5-111">V tématu [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) informace o tom, jak najít které kódu stránky jsou podporovány v systému.</span><span class="sxs-lookup"><span data-stu-id="bbca5-111">See [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="bbca5-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="bbca5-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbca5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbca5-113">See Also</span></span>  
 [<span data-ttu-id="bbca5-114">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="bbca5-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="bbca5-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="bbca5-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
