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
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202909"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="73b0a-102">@ (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="73b0a-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="73b0a-103">Možnost @ umožňuje zadat soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="73b0a-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73b0a-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="73b0a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73b0a-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="73b0a-106">Soubor se seznamem možností kompilátoru nebo souborů zdrojového kódu, které mají být zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="73b0a-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73b0a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73b0a-107">Remarks</span></span>  
 <span data-ttu-id="73b0a-108">Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně, jako kdyby byly zadány v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="73b0a-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="73b0a-109">Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odezvy.</span><span class="sxs-lookup"><span data-stu-id="73b0a-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="73b0a-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73b0a-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="73b0a-111">V souboru odpovědí se může na jednom řádku objevit více možností kompilátoru a souborů zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="73b0a-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="73b0a-112">Jedna specifikace možnosti kompilátoru se musí vyskytovat na jednom řádku (nemůže zasahovat do více řádků).</span><span class="sxs-lookup"><span data-stu-id="73b0a-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="73b0a-113">Soubory odpovědí můžou obsahovat komentáře, které začínají symbolem #.</span><span class="sxs-lookup"><span data-stu-id="73b0a-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="73b0a-114">Zadání možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="73b0a-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="73b0a-115">Další informace naleznete v tématu sestavování [z příkazového řádku](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .</span><span class="sxs-lookup"><span data-stu-id="73b0a-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="73b0a-116">Kompilátor zpracuje možnosti příkazu, jak jsou zjištěny.</span><span class="sxs-lookup"><span data-stu-id="73b0a-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="73b0a-117">Proto argumenty příkazového řádku mohou přepsat dříve uvedené možnosti v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="73b0a-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="73b0a-118">Naopak možnosti v souboru odpovědí budou přepisovat možnosti uvedené dříve na příkazovém řádku nebo v jiných souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="73b0a-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="73b0a-119">C#poskytuje soubor csc. rsp, který je umístěn ve stejném adresáři jako soubor csc. exe.</span><span class="sxs-lookup"><span data-stu-id="73b0a-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="73b0a-120">Další informace o souboru CSc. rsp najdete v článku o [konfiguraci](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="73b0a-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="73b0a-121">Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.</span><span class="sxs-lookup"><span data-stu-id="73b0a-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73b0a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="73b0a-122">Example</span></span>  
 <span data-ttu-id="73b0a-123">Následuje několik řádků z ukázkového souboru odezvy:</span><span class="sxs-lookup"><span data-stu-id="73b0a-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="73b0a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73b0a-124">See also</span></span>

- [<span data-ttu-id="73b0a-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73b0a-125">C# Compiler Options</span></span>](./index.md)
