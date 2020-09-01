---
description: -unconfig (možnosti kompilátoru C#)
title: -unconfig (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 26d0680743ccc3af26a0e81eeec9cd2fc0d693af
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125225"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="a4d0f-103">-unconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a4d0f-103">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="a4d0f-104">Možnost **-inconfig** instruuje kompilátor, že není zkompilován se souborem CSc. rsp, který je umístěn v a načten ze stejného adresáře jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d0f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4d0f-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a4d0f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4d0f-106">Remarks</span></span>  
 <span data-ttu-id="a4d0f-107">Soubor csc. rsp odkazuje na všechna sestavení odeslaná pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-107">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="a4d0f-108">Skutečné odkazy, které obsahuje vývojové prostředí sady Visual Studio .NET, závisí na typu projektu.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="a4d0f-109">Můžete upravit soubor csc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace z příkazového řádku s csc.exe (kromě možnosti **--config** ).</span><span class="sxs-lookup"><span data-stu-id="a4d0f-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="a4d0f-110">Kompilátor zpracuje možnosti předané do příkazu **CSC** jako poslední.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="a4d0f-111">Proto všechny možnosti příkazového řádku přepisují nastavení stejné možnosti v souboru CSc. rsp.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="a4d0f-112">Pokud nechcete, aby kompilátor hledal a použil nastavení v souboru CSc. rsp, zadejte **-inconfig**.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="a4d0f-113">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="a4d0f-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d0f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4d0f-114">See also</span></span>

- [<span data-ttu-id="a4d0f-115">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a4d0f-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a4d0f-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a4d0f-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
