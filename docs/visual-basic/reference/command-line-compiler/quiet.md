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
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788840"
---
# <a name="-quiet"></a><span data-ttu-id="aae27-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="aae27-102">-quiet</span></span>

<span data-ttu-id="aae27-103">Zabrání zobrazení kódu pro syntaxi související chyby a upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="aae27-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="aae27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aae27-104">Syntax</span></span>

```
-quiet
```

## <a name="remarks"></a><span data-ttu-id="aae27-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aae27-105">Remarks</span></span>

<span data-ttu-id="aae27-106">Ve výchozím nastavení `-quiet` není platná.</span><span class="sxs-lookup"><span data-stu-id="aae27-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="aae27-107">Pokud kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstup řádku ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="aae27-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="aae27-108">U aplikací, které parsovat výstup kompilátoru může být vhodnější pro kompilátor výstup jenom text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="aae27-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="aae27-109">V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="aae27-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="aae27-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="aae27-110">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="aae27-111">Zkompilované s `-quiet`, kompilátor uloží jenom následující:</span><span class="sxs-lookup"><span data-stu-id="aae27-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="aae27-112">`-quiet` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="aae27-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="aae27-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="aae27-113">Example</span></span>

<span data-ttu-id="aae27-114">Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související syntaxi:</span><span class="sxs-lookup"><span data-stu-id="aae27-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="aae27-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aae27-115">See also</span></span>

- [<span data-ttu-id="aae27-116">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="aae27-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="aae27-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="aae27-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
