---
description: -codepage (možnosti kompilátoru C#)
title: -codepage (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 4c812314ed9c1abcd7d2f34b2281140175621312
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125953"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="33ee0-103">-codepage (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="33ee0-103">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="33ee0-104">Tato možnost určuje, která znaková stránka se má použít při kompilaci, pokud požadovaná stránka není aktuální výchozí znakovou stránkou pro systém.</span><span class="sxs-lookup"><span data-stu-id="33ee0-104">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ee0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33ee0-105">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="33ee0-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="33ee0-106">Arguments</span></span>  
 `id`  
 <span data-ttu-id="33ee0-107">ID kódové stránky, která se má použít pro všechny soubory zdrojového kódu v kompilaci</span><span class="sxs-lookup"><span data-stu-id="33ee0-107">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33ee0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33ee0-108">Remarks</span></span>  
 <span data-ttu-id="33ee0-109">Kompilátor se nejprve pokusí interpretovat všechny zdrojové soubory jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="33ee0-109">The compiler will first attempt to interpret all source files as UTF-8.</span></span> <span data-ttu-id="33ee0-110">Pokud jsou soubory zdrojového kódu v kódování jiné než UTF-8 a používají jiné znaky než 7 bitů znaků ASCII, použijte možnost **-codepage** a určete, která znaková stránka má být použita.</span><span class="sxs-lookup"><span data-stu-id="33ee0-110">If your source code files are in an encoding other than UTF-8 and use characters other than 7-bit ASCII characters, use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="33ee0-111">**-znaková stránka** se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.</span><span class="sxs-lookup"><span data-stu-id="33ee0-111">**-codepage** applies to all source code files in your compilation.</span></span>  

 <span data-ttu-id="33ee0-112">V tématu [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) najdete informace o tom, jak najít znakové stránky, které jsou v systému podporovány.</span><span class="sxs-lookup"><span data-stu-id="33ee0-112">See [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="33ee0-113">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="33ee0-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ee0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="33ee0-114">See also</span></span>

- [<span data-ttu-id="33ee0-115">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="33ee0-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="33ee0-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="33ee0-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
