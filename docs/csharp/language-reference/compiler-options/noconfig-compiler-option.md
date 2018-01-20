---
title: "-noconfig (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1004f70547ca3a841c59338a1344235132af3fa7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="10f63-102">-noconfig (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="10f63-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="10f63-103">**- Noconfig** říká kompilátoru nechcete kompilovat bez souboru csc.rsp, který je umístěn a načíst ze stejného adresáře jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="10f63-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10f63-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="10f63-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10f63-105">Remarks</span></span>  
 <span data-ttu-id="10f63-106">Soubor csc.rsp odkazuje všechna sestavení součástí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10f63-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="10f63-107">Skutečné odkazy, které zahrnuje vývojového prostředí sady Visual Studio .NET závisí na typu projektu.</span><span class="sxs-lookup"><span data-stu-id="10f63-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="10f63-108">Můžete upravit soubor csc.rsp a určit další kompilátoru možnosti, které mají být zahrnuty v každé kompilaci z příkazového řádku pomocí csc.exe (s výjimkou **- noconfig** možnost).</span><span class="sxs-lookup"><span data-stu-id="10f63-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="10f63-109">Kompilátor zpracovává možnosti předaný **csc** poslední příkaz.</span><span class="sxs-lookup"><span data-stu-id="10f63-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="10f63-110">Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="10f63-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="10f63-111">Pokud nechcete, aby kompilátoru vyhledejte a použijte nastavení v souboru csc.rsp, zadejte **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="10f63-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="10f63-112">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="10f63-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f63-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="10f63-113">See Also</span></span>  
 [<span data-ttu-id="10f63-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10f63-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="10f63-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="10f63-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
