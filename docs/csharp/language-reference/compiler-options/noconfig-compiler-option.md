---
title: -unconfig (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602735"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="69735-102">-unconfig (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="69735-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="69735-103">Možnost **-inconfig** říká kompilátoru, že není zkompilován se souborem CSc. rsp, který je umístěn v a načten ze stejného adresáře jako soubor csc. exe.</span><span class="sxs-lookup"><span data-stu-id="69735-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69735-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69735-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="69735-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69735-105">Remarks</span></span>  
 <span data-ttu-id="69735-106">Soubor csc. rsp odkazuje na všechna sestavení odeslaná pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69735-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="69735-107">Skutečné odkazy, které obsahuje vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.</span><span class="sxs-lookup"><span data-stu-id="69735-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="69735-108">Můžete upravit soubor csc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty v každé kompilaci z příkazového řádku pomocí CSc. exe (kromě možnosti **---config** ).</span><span class="sxs-lookup"><span data-stu-id="69735-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="69735-109">Kompilátor zpracuje možnosti předané do příkazu **CSC** jako poslední.</span><span class="sxs-lookup"><span data-stu-id="69735-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="69735-110">Proto všechny možnosti příkazového řádku přepisují nastavení stejné možnosti v souboru CSc. rsp.</span><span class="sxs-lookup"><span data-stu-id="69735-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="69735-111">Pokud nechcete, aby kompilátor hledal a použil nastavení v souboru CSc. rsp, zadejte **-inconfig**.</span><span class="sxs-lookup"><span data-stu-id="69735-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="69735-112">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="69735-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69735-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69735-113">See also</span></span>

- [<span data-ttu-id="69735-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="69735-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="69735-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="69735-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
