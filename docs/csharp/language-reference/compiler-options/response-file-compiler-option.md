---
title: '@ (Možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202909"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="348c5-102">@ (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="348c5-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="348c5-103">Možnost @ umožňuje zadat soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="348c5-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="348c5-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="348c5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="348c5-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="348c5-106">Soubor, který obsahuje seznam možností kompilátoru nebo souborů zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="348c5-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="348c5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="348c5-107">Remarks</span></span>  
 <span data-ttu-id="348c5-108">Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně jako v případě, že byly zadány na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="348c5-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="348c5-109">Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="348c5-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="348c5-110">Například:</span><span class="sxs-lookup"><span data-stu-id="348c5-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="348c5-111">V souboru odpovědí se na jednom řádku může objevit více možností kompilátoru a souborů zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="348c5-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="348c5-112">Na jednom řádku se musí objevit jedna specifikace možnosti kompilátoru (nelze přehoupnout více řádků).</span><span class="sxs-lookup"><span data-stu-id="348c5-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="348c5-113">Soubory odpovědí mohou mít komentáře, které začínají symbolem # .</span><span class="sxs-lookup"><span data-stu-id="348c5-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="348c5-114">Určení možností kompilátoru ze souboru odpovědí je stejné jako vydávání těchto příkazů na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="348c5-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="348c5-115">Další informace naleznete [v tématu Vytváření z příkazového řádku.](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="348c5-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="348c5-116">Kompilátor zpracuje možnosti příkazu tak, jak jsou zjištěny.</span><span class="sxs-lookup"><span data-stu-id="348c5-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="348c5-117">Argumenty příkazového řádku proto mohou přepsat dříve uvedené možnosti v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="348c5-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="348c5-118">Naopak možnosti v souboru odpovědí přepíší možnosti uvedené dříve na příkazovém řádku nebo v jiných souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="348c5-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="348c5-119">C# poskytuje soubor csc.rsp, který je umístěn ve stejném adresáři jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="348c5-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="348c5-120">Viz [-noconfig](./noconfig-compiler-option.md) pro více informací o csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="348c5-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="348c5-121">Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji nelze programově změnit.</span><span class="sxs-lookup"><span data-stu-id="348c5-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="348c5-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="348c5-122">Example</span></span>  
 <span data-ttu-id="348c5-123">Následuje několik řádků z ukázkového souboru odpovědí:</span><span class="sxs-lookup"><span data-stu-id="348c5-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="348c5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="348c5-124">See also</span></span>

- [<span data-ttu-id="348c5-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="348c5-125">C# Compiler Options</span></span>](./index.md)
