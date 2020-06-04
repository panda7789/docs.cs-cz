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
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400523"
---
# <a name="-quiet"></a><span data-ttu-id="f70a8-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="f70a8-102">-quiet</span></span>

<span data-ttu-id="f70a8-103">Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.</span><span class="sxs-lookup"><span data-stu-id="f70a8-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="f70a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f70a8-104">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="f70a8-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f70a8-105">Remarks</span></span>

<span data-ttu-id="f70a8-106">Ve výchozím nastavení `-quiet` není platná.</span><span class="sxs-lookup"><span data-stu-id="f70a8-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="f70a8-107">Když kompilátor ohlásí chybu nebo upozornění související se syntaxí, vypíše také řádek ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f70a8-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="f70a8-108">Pro aplikace, které analyzují výstup kompilátoru, může být vhodnější, aby kompilátor vyoutput pouze text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="f70a8-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="f70a8-109">V následujícím příkladu `Module1` výstup obsahuje chybu, která zahrnuje zdrojový kód, pokud je zkompilován bez `-quiet` .</span><span class="sxs-lookup"><span data-stu-id="f70a8-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="f70a8-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="f70a8-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="f70a8-111">Kompilováno s `-quiet` , kompilátor výstupuje pouze následující:</span><span class="sxs-lookup"><span data-stu-id="f70a8-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="f70a8-112">Tato `-quiet` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f70a8-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="f70a8-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f70a8-113">Example</span></span>

<span data-ttu-id="f70a8-114">Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související s syntaxí:</span><span class="sxs-lookup"><span data-stu-id="f70a8-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="f70a8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f70a8-115">See also</span></span>

- [<span data-ttu-id="f70a8-116">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f70a8-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f70a8-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f70a8-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
