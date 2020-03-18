---
title: -codepage (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173754"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="e9a01-102">-codepage (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="e9a01-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="e9a01-103">Tato možnost určuje, kterou znakovou stránku použít během kompilace, pokud požadovaná stránka není aktuální výchozí znakovou stránkou systému.</span><span class="sxs-lookup"><span data-stu-id="e9a01-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9a01-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9a01-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e9a01-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="e9a01-106">Id znakové stránky, která má být používána pro všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="e9a01-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a01-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9a01-107">Remarks</span></span>  
 <span data-ttu-id="e9a01-108">Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e9a01-108">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="e9a01-109">Pokud jsou soubory zdrojového kódu v jiném kódování než UTF-8 a používají jiné znaky než 7bitové znaky ASCII, použijte možnost **-codepage** k určení, která znaková stránka má být použita.</span><span class="sxs-lookup"><span data-stu-id="e9a01-109">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="e9a01-110">**-codepage** se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.</span><span class="sxs-lookup"><span data-stu-id="e9a01-110">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="e9a01-111">Informace o tom, jak zjistit, které znakové stránky jsou ve vašem systému podporované, najdete v tématu [GetCPInfo.](/windows/desktop/api/winnls/nf-winnls-getcpinfo)</span><span class="sxs-lookup"><span data-stu-id="e9a01-111">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="e9a01-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="e9a01-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a01-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a01-113">See also</span></span>

- [<span data-ttu-id="e9a01-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9a01-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e9a01-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e9a01-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
