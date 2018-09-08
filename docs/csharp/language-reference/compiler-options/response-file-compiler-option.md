---
title: '@ (Možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: f342f26ee8abe29e6c5a1477469c8b7292cd702e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201501"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="a5042-102">@ (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a5042-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="a5042-103">@ – Možnost umožňují určit soubor obsahující možnosti kompilátoru a soubory zdrojového kódu pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a5042-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5042-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5042-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5042-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5042-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="a5042-106">Soubor se seznamem – možnosti kompilátoru nebo souborů se zdrojovým kódem, chcete-li zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="a5042-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5042-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5042-107">Remarks</span></span>  
 <span data-ttu-id="a5042-108">Možnosti kompilátoru a soubory zdrojového kódu budou zpracovány kompilátorem tak, jako kdyby kdyby byly zadány v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a5042-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="a5042-109">Pokud chcete zadat více než jeden soubor odpovědí do kompilace, zadejte více možnosti soubor odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a5042-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="a5042-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a5042-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="a5042-111">V odpovědi na soubor, více možností kompilátoru a soubory zdrojového kódu může zobrazit na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="a5042-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="a5042-112">Specifikace jediné kompilátoru možnost se musí nacházet na jednom řádku (nemůžou zahrnovat více řádků).</span><span class="sxs-lookup"><span data-stu-id="a5042-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="a5042-113">Soubory odpovědí může mít komentáře, které začínají symbolem #.</span><span class="sxs-lookup"><span data-stu-id="a5042-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="a5042-114">Určení možností kompilátoru ze souboru odpovědí je stejně jako vydávání těchto příkazů na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a5042-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="a5042-115">Zobrazit [sestavení z příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="a5042-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="a5042-116">Kompilátor zpracovává možnosti příkazu v průběhu jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="a5042-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="a5042-117">Argumenty příkazového řádku můžete přepsat, proto výše uvedených možností v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="a5042-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="a5042-118">Možnosti v souboru odpovědí a naopak, přepíše možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="a5042-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="a5042-119">C# obsahuje soubor csc.rsp, který je umístěn ve stejném adresáři jako soubor csc.exe.</span><span class="sxs-lookup"><span data-stu-id="a5042-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="a5042-120">Zobrazit [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Další informace o souboru csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a5042-120">See [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="a5042-121">Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio ani ji není možné změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="a5042-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5042-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5042-122">Example</span></span>  
 <span data-ttu-id="a5042-123">Následují po zadání několika řádků z ukázkového souboru odpovědí:</span><span class="sxs-lookup"><span data-stu-id="a5042-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5042-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5042-124">See Also</span></span>  

- [<span data-ttu-id="a5042-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a5042-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
