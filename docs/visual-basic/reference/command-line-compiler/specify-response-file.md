---
title: '@ (určení souboru odezvy)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 91cf1b5a55d16ab47a83fbd259dd1d83d8e9c31a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403093"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="ad67b-102">@ (Určení souboru odezvy) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad67b-102">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="ad67b-103">Určuje soubor, který obsahuje možnosti kompilátoru a soubory zdrojového kódu ke kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ad67b-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad67b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad67b-104">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="ad67b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ad67b-105">Arguments</span></span>

`response_file`  
<span data-ttu-id="ad67b-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ad67b-106">Required.</span></span> <span data-ttu-id="ad67b-107">Soubor se seznamem možností kompilátoru nebo souborů zdrojového kódu, které mají být zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="ad67b-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="ad67b-108">Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="ad67b-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad67b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad67b-109">Remarks</span></span>

<span data-ttu-id="ad67b-110">Kompilátor zpracovává možnosti kompilátoru a soubory zdrojového kódu zadané v souboru odpovědí, jako kdyby byly zadány v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ad67b-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="ad67b-111">Chcete-li v kompilaci zadat více než jeden soubor odpovědí, zadejte více možností souboru odpovědi, například následující.</span><span class="sxs-lookup"><span data-stu-id="ad67b-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="ad67b-112">V souboru odpovědí se může na jednom řádku objevit více možností kompilátoru a souborů zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ad67b-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="ad67b-113">Jedna specifikace možnosti kompilátoru se musí vyskytovat na jednom řádku (nemůže zabírat více řádků).</span><span class="sxs-lookup"><span data-stu-id="ad67b-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="ad67b-114">Soubory odpovědí mohou obsahovat komentáře, které začínají `#` symbolem.</span><span class="sxs-lookup"><span data-stu-id="ad67b-114">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="ad67b-115">Můžete kombinovat možnosti zadané v příkazovém řádku s možnostmi určenými v jednom nebo více souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ad67b-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="ad67b-116">Kompilátor zpracuje možnosti příkazu, jak je nalezne.</span><span class="sxs-lookup"><span data-stu-id="ad67b-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="ad67b-117">Proto argumenty příkazového řádku mohou přepsat dříve uvedené možnosti v souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ad67b-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="ad67b-118">Naopak možnosti v parametrech přepsání souboru odpovědí uvedených dříve na příkazovém řádku nebo v jiných souborech odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ad67b-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="ad67b-119">Visual Basic poskytuje soubor Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="ad67b-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="ad67b-120">Soubor Vbc. rsp je ve výchozím nastavení zahrnut, pokud se `-noconfig` nepoužívá možnost.</span><span class="sxs-lookup"><span data-stu-id="ad67b-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="ad67b-121">Další informace najdete v tématu [-config](noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="ad67b-121">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ad67b-122">Tato `@` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ad67b-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="ad67b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad67b-123">Example</span></span>

<span data-ttu-id="ad67b-124">Následující řádky jsou z ukázkového souboru odezvy.</span><span class="sxs-lookup"><span data-stu-id="ad67b-124">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="ad67b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad67b-125">Example</span></span>

<span data-ttu-id="ad67b-126">Následující příklad ukazuje, jak použít `@` možnost se souborem odpovědí s názvem `File1.rsp` .</span><span class="sxs-lookup"><span data-stu-id="ad67b-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="ad67b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad67b-127">See also</span></span>

- [<span data-ttu-id="ad67b-128">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ad67b-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ad67b-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="ad67b-129">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="ad67b-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ad67b-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
