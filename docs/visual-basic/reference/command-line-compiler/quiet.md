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
ms.openlocfilehash: 32f82eb428c1d3bc427a10b9ca7a1a5feb9e339a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816535"
---
# <a name="-quiet"></a><span data-ttu-id="0c126-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="0c126-102">-quiet</span></span>
<span data-ttu-id="0c126-103">Zabrání zobrazení kódu pro syntaxi související chyby a upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0c126-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c126-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c126-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c126-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c126-105">Remarks</span></span>  
 <span data-ttu-id="0c126-106">Ve výchozím nastavení `-quiet` není platná.</span><span class="sxs-lookup"><span data-stu-id="0c126-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="0c126-107">Pokud kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstup řádku ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="0c126-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="0c126-108">U aplikací, které parsovat výstup kompilátoru může být vhodnější pro kompilátor výstup jenom text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="0c126-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="0c126-109">V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="0c126-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0c126-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="0c126-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="0c126-111">Zkompilované s `-quiet`, kompilátor uloží jenom následující:</span><span class="sxs-lookup"><span data-stu-id="0c126-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="0c126-112">`-quiet` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0c126-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c126-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c126-113">Example</span></span>  
 <span data-ttu-id="0c126-114">Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související syntaxi:</span><span class="sxs-lookup"><span data-stu-id="0c126-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c126-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c126-115">See also</span></span>

- [<span data-ttu-id="0c126-116">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0c126-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0c126-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0c126-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
