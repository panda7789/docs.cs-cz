---
title: -noconfig (Možnosti kompilátoru Jazyka C#)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602735"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="f512f-102">-noconfig (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f512f-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="f512f-103">Možnost **-noconfig** říká kompilátoru, aby nekompiloval se souborem csc.rsp, který je umístěn a načten ze stejného adresáře jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="f512f-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f512f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f512f-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="f512f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f512f-105">Remarks</span></span>  
 <span data-ttu-id="f512f-106">Soubor csc.rsp odkazuje na všechna sestavení dodávaná s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f512f-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="f512f-107">Skutečné odkazy, které obsahuje vývojové prostředí Visual Studio .NET, závisí na typu projektu.</span><span class="sxs-lookup"><span data-stu-id="f512f-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="f512f-108">Můžete upravit soubor csc.rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace z příkazového řádku s csc.exe (kromě volby **-noconfig).**</span><span class="sxs-lookup"><span data-stu-id="f512f-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="f512f-109">Kompilátor zpracuje možnosti předané příkazu **csc** jako poslední.</span><span class="sxs-lookup"><span data-stu-id="f512f-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="f512f-110">Proto všechny možnosti na příkazovém řádku přepíše nastavení stejné volby v souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="f512f-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="f512f-111">Pokud nechcete, aby kompilátor vyhledává a používal nastavení v souboru csc.rsp, zadejte **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="f512f-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="f512f-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="f512f-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f512f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f512f-113">See also</span></span>

- [<span data-ttu-id="f512f-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f512f-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f512f-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f512f-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
