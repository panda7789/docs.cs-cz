---
title: '@ (Určení souboru odezvy) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639019"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="fb5c3-102">@ (Určení souboru odezvy) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb5c3-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="fb5c3-103">Určuje soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb5c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb5c3-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb5c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fb5c3-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="fb5c3-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-106">Required.</span></span> <span data-ttu-id="fb5c3-107">Soubor se seznamem – možnosti kompilátoru nebo soubory zdrojového kódu pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="fb5c3-108">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb5c3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb5c3-109">Remarks</span></span>  
 <span data-ttu-id="fb5c3-110">Kompilátor zpracovává možnosti kompilátoru a soubory zdrojového kódu jakoby kdyby byly zadány v příkazovém řádku zadané v souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="fb5c3-111">Chcete-li zadat více než jeden soubor odpovědí do kompilace, zadejte více možností soubor odpovědí, jako je následující.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="fb5c3-112">V odpovědi na soubor, více možností kompilátoru a soubory zdrojového kódu může zobrazit na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="fb5c3-113">Specifikace jediné-– možnost kompilátoru se musí nacházet na jednom řádku (nemůžou zahrnovat více řádků).</span><span class="sxs-lookup"><span data-stu-id="fb5c3-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="fb5c3-114">Soubory odpovědí může mít komentáře, které začínají `#` symbol.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="fb5c3-115">Můžete kombinovat možnosti zadané v příkazovém řádku pomocí volby zadané v jeden nebo více souborů odezvy.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="fb5c3-116">Kompilátor zpracovává možnosti příkazu při jejich výskytu.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="fb5c3-117">Argumenty příkazového řádku můžete přepsat, proto výše uvedených možností v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="fb5c3-118">Možnosti v souboru odpovědí a naopak, přepsat možnosti uvedené dříve v příkazovém řádku nebo v jiné soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="fb5c3-119">Visual Basic poskytuje soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="fb5c3-120">Soubor Vbc.rsp je zahrnuté ve výchozím nastavení, pokud `-noconfig` možnost se používá.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="fb5c3-121">Další informace najdete v tématu [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="fb5c3-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb5c3-122">`@` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb5c3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb5c3-123">Example</span></span>  
 <span data-ttu-id="fb5c3-124">Následující řádky jsou z ukázkového souboru odpovědí.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="fb5c3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb5c3-125">Example</span></span>  
 <span data-ttu-id="fb5c3-126">Následující příklad ukazuje způsob použití `@` možnost pomocí souboru odpovědí s názvem `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="fb5c3-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb5c3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb5c3-127">See also</span></span>

- [<span data-ttu-id="fb5c3-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="fb5c3-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fb5c3-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="fb5c3-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="fb5c3-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="fb5c3-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
