---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005280"
---
# <a name="-quiet"></a><span data-ttu-id="a6f24-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="a6f24-102">-quiet</span></span>

<span data-ttu-id="a6f24-103">Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.</span><span class="sxs-lookup"><span data-stu-id="a6f24-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6f24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6f24-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="a6f24-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6f24-105">Remarks</span></span>

<span data-ttu-id="a6f24-106">Ve výchozím nastavení není `-quiet` v platnosti.</span><span class="sxs-lookup"><span data-stu-id="a6f24-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="a6f24-107">Když kompilátor ohlásí chybu nebo upozornění související se syntaxí, vypíše také řádek ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a6f24-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="a6f24-108">Pro aplikace, které analyzují výstup kompilátoru, může být vhodnější, aby kompilátor vyoutput pouze text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="a6f24-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="a6f24-109">V následujícím příkladu `Module1` výstupy chyby, která obsahuje zdrojový kód při kompilaci bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="a6f24-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="a6f24-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a6f24-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="a6f24-111">Kompilováno s `-quiet`, kompilátor výstupuje pouze následující:</span><span class="sxs-lookup"><span data-stu-id="a6f24-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="a6f24-112">Možnost `-quiet` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a6f24-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a6f24-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6f24-113">Example</span></span>

<span data-ttu-id="a6f24-114">Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související s syntaxí:</span><span class="sxs-lookup"><span data-stu-id="a6f24-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a6f24-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6f24-115">See also</span></span>

- [<span data-ttu-id="a6f24-116">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a6f24-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a6f24-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a6f24-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
