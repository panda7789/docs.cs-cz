---
title: -noconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528573"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="a9a5b-102">-noconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a9a5b-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="a9a5b-103">**- Noconfig** přikáže kompilátoru, aby kompilovat s csc.rsp soubor, který je umístěn a načten ze stejného adresáře jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9a5b-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9a5b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9a5b-105">Remarks</span></span>  
 <span data-ttu-id="a9a5b-106">Soubor csc.rsp odkazuje na všechna sestavení, které jsou součástí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="a9a5b-107">Skutečné odkazy, které zahrnují vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="a9a5b-108">Můžete upravit soubor csc.rsp a určit další možnosti kompilátoru, které by měl být součástí každé kompilaci z příkazového řádku pomocí csc.exe (s výjimkou **- noconfig** možnost).</span><span class="sxs-lookup"><span data-stu-id="a9a5b-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="a9a5b-109">Kompilátor zpracovává možnosti předané **csc** poslední příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="a9a5b-110">Proto všechny možnost na příkazovém řádku přepíše nastavení stejná možnost v souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="a9a5b-111">Pokud nechcete, aby kompilátor hledal a použijte nastavení v souboru csc.rsp, zadejte **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="a9a5b-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="a9a5b-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a5b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9a5b-113">See also</span></span>

- [<span data-ttu-id="a9a5b-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9a5b-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a9a5b-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a9a5b-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
