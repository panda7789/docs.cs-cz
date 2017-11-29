---
title: "@ (Možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4dc8c81a9afd60add4c2a62be6804a0f6446124
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="-c-compiler-options"></a><span data-ttu-id="2ec2d-102">@ (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="2ec2d-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="2ec2d-103">@ Možnost umožňuje zadat soubor, který obsahuje – možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec2d-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ec2d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ec2d-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="2ec2d-106">Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec2d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ec2d-107">Remarks</span></span>  
 <span data-ttu-id="2ec2d-108">Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem stejně, jako kdyby kdyby byly zadány na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="2ec2d-109">Chcete-li zadat více než jeden soubor odpovědi v kompilaci, zadejte možnost souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="2ec2d-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ec2d-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="2ec2d-111">V odpovědi můžete soubor, více – možnosti kompilátoru a soubory zdrojového kódu zobrazí na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="2ec2d-112">Specifikaci – možnost kompilátoru jeden musí být uvedena na jednom řádku (nemůže zahrnovat více řádků).</span><span class="sxs-lookup"><span data-stu-id="2ec2d-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="2ec2d-113">Soubory odezvy může mít komentáře, které začínají symbolem #.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="2ec2d-114">Určení možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="2ec2d-115">V tématu [sestavení z příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="2ec2d-116">Kompilátor zpracovává příkazy možností, jak se vyskytují.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="2ec2d-117">Argumenty příkazového řádku. proto můžete přepsat výše uvedených možností v souborech odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="2ec2d-118">Možnosti v souboru odpovědí naopak přepíše možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="2ec2d-119">C# poskytuje souboru csc.rsp, který se nachází ve stejném adresáři jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="2ec2d-120">V tématu [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Další informace o souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-120">See [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="2ec2d-121">Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji není možné změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="2ec2d-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec2d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ec2d-122">Example</span></span>  
 <span data-ttu-id="2ec2d-123">Následuje několik řádků z ukázkového souboru odpovědí:</span><span class="sxs-lookup"><span data-stu-id="2ec2d-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ec2d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ec2d-124">See Also</span></span>  
 [<span data-ttu-id="2ec2d-125">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="2ec2d-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
