---
title: "@ (Určení souboru odezvy) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ced258713983ded06fa70cb65d56071b41cdc75b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="849e8-102">@ (Určení souboru odezvy) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="849e8-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="849e8-103">Určuje soubor, který obsahuje – možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="849e8-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="849e8-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="849e8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="849e8-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="849e8-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="849e8-106">Required.</span></span> <span data-ttu-id="849e8-107">Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="849e8-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="849e8-108">Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="849e8-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="849e8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="849e8-109">Remarks</span></span>  
 <span data-ttu-id="849e8-110">Kompilátor zpracovává – možnosti kompilátoru a soubory zdrojového kódu zadané v souboru odpovědí, jako kdyby kdyby byly zadány na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="849e8-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="849e8-111">Zadat více než jeden soubor odpovědi v kompilaci, zadejte více možnosti soubor odpovědí, podobně jako tento.</span><span class="sxs-lookup"><span data-stu-id="849e8-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="849e8-112">V odpovědi můžete soubor, více – možnosti kompilátoru a soubory zdrojového kódu zobrazí na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="849e8-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="849e8-113">Specifikace jednoho-– možnost kompilátoru musí být uvedena na jednom řádku (nemůže zahrnovat více řádků).</span><span class="sxs-lookup"><span data-stu-id="849e8-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="849e8-114">Soubory odezvy může mít komentáře, které začínají `#` symbol.</span><span class="sxs-lookup"><span data-stu-id="849e8-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="849e8-115">Zkombinováním možností na příkazovém řádku s možností v jeden nebo více souborů odpovědi.</span><span class="sxs-lookup"><span data-stu-id="849e8-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="849e8-116">Kompilátor zpracovává možností příkazového řádku při jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="849e8-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="849e8-117">Proto argumenty příkazového řádku můžete přepsat výše uvedených možností v souborech odpovědi.</span><span class="sxs-lookup"><span data-stu-id="849e8-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="849e8-118">Naopak možnosti v souboru odpovědí přepsat možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědi.</span><span class="sxs-lookup"><span data-stu-id="849e8-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="849e8-119">Visual Basic poskytuje Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="849e8-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="849e8-120">Soubor Vbc.rsp je zahrnutá ve výchozím nastavení, pokud `/noconfig` možnost se používá.</span><span class="sxs-lookup"><span data-stu-id="849e8-120">The Vbc.rsp file is included by default, unless the `/noconfig` option is used.</span></span> <span data-ttu-id="849e8-121">Další informace najdete v tématu [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="849e8-121">For more information, see [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="849e8-122">`@` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="849e8-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="849e8-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="849e8-123">Example</span></span>  
 <span data-ttu-id="849e8-124">Následující řádky představují z ukázkového souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="849e8-124">The following lines are from a sample response file.</span></span>  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="849e8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="849e8-125">Example</span></span>  
 <span data-ttu-id="849e8-126">Následující příklad ukazuje, jak používat `@` možnost pomocí souboru odpovědí s názvem `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="849e8-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```  
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="849e8-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="849e8-127">See Also</span></span>  
 [<span data-ttu-id="849e8-128">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="849e8-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="849e8-129">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="849e8-129">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="849e8-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="849e8-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
