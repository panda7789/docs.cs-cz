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
ms.openlocfilehash: e67fe05507c8cb3edd7f46cad19211ba11e3b054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652393"
---
# <a name="-quiet"></a><span data-ttu-id="f5ba7-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="f5ba7-102">-quiet</span></span>
<span data-ttu-id="f5ba7-103">Zabrání zobrazení kódu syntaxe související chyby a upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5ba7-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5ba7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5ba7-105">Remarks</span></span>  
 <span data-ttu-id="f5ba7-106">Ve výchozím nastavení `-quiet` není funkční.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="f5ba7-107">Když kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstupy řádku ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="f5ba7-108">Pro aplikace, které analyzovat výstupu kompilátoru může být pohodlnější kompilátor pro výstup jenom text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="f5ba7-109">V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `-quiet`.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f5ba7-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="f5ba7-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="f5ba7-111">Kompilované s `-quiet`, kompilátor výstupy jenom následující:</span><span class="sxs-lookup"><span data-stu-id="f5ba7-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="f5ba7-112">`-quiet` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f5ba7-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5ba7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5ba7-113">Example</span></span>  
 <span data-ttu-id="f5ba7-114">Následující kód zkompiluje `T2.vb` a nezobrazí kód pro diagnostiku související syntaxe kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="f5ba7-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5ba7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5ba7-115">See Also</span></span>  
 [<span data-ttu-id="f5ba7-116">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f5ba7-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f5ba7-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f5ba7-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
