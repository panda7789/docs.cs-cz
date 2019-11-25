---
title: '@ (Určení souboru odezvy)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: c578495bbba0efee79f02da284c7feffb8c12fab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348554"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="15edf-102">@ (Určení souboru odezvy) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15edf-102">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="15edf-103">Specifies a file that contains compiler options and source-code files to compile.</span><span class="sxs-lookup"><span data-stu-id="15edf-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="15edf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15edf-104">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="15edf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="15edf-105">Arguments</span></span>

`response_file`  
<span data-ttu-id="15edf-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="15edf-106">Required.</span></span> <span data-ttu-id="15edf-107">A file that lists compiler options or source-code files to compile.</span><span class="sxs-lookup"><span data-stu-id="15edf-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="15edf-108">Enclose the file name in quotation marks (" ") if it contains a space.</span><span class="sxs-lookup"><span data-stu-id="15edf-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="15edf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15edf-109">Remarks</span></span>

<span data-ttu-id="15edf-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span><span class="sxs-lookup"><span data-stu-id="15edf-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="15edf-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span><span class="sxs-lookup"><span data-stu-id="15edf-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="15edf-112">In a response file, multiple compiler options and source-code files can appear on one line.</span><span class="sxs-lookup"><span data-stu-id="15edf-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="15edf-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span><span class="sxs-lookup"><span data-stu-id="15edf-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="15edf-114">Response files can have comments that begin with the `#` symbol.</span><span class="sxs-lookup"><span data-stu-id="15edf-114">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="15edf-115">You can combine options specified on the command line with options specified in one or more response files.</span><span class="sxs-lookup"><span data-stu-id="15edf-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="15edf-116">The compiler processes the command options as it encounters them.</span><span class="sxs-lookup"><span data-stu-id="15edf-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="15edf-117">Therefore, command-line arguments can override previously listed options in response files.</span><span class="sxs-lookup"><span data-stu-id="15edf-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="15edf-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span><span class="sxs-lookup"><span data-stu-id="15edf-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="15edf-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span><span class="sxs-lookup"><span data-stu-id="15edf-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="15edf-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span><span class="sxs-lookup"><span data-stu-id="15edf-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="15edf-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="15edf-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="15edf-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span><span class="sxs-lookup"><span data-stu-id="15edf-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="15edf-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="15edf-123">Example</span></span>

<span data-ttu-id="15edf-124">The following lines are from a sample response file.</span><span class="sxs-lookup"><span data-stu-id="15edf-124">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="15edf-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="15edf-125">Example</span></span>

<span data-ttu-id="15edf-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="15edf-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="15edf-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15edf-127">See also</span></span>

- [<span data-ttu-id="15edf-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="15edf-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="15edf-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="15edf-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="15edf-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="15edf-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
