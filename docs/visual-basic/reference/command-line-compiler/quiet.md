---
title: /quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b816cadb9d805d57a14e9b5df553654dd8167af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="quiet"></a><span data-ttu-id="a06d6-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="a06d6-102">/quiet</span></span>
<span data-ttu-id="a06d6-103">Zabrání zobrazení kódu syntaxe související chyby a upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a06d6-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a06d6-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="a06d6-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a06d6-105">Remarks</span></span>  
 <span data-ttu-id="a06d6-106">Ve výchozím nastavení `/quiet` není funkční.</span><span class="sxs-lookup"><span data-stu-id="a06d6-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="a06d6-107">Když kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstupy řádku ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a06d6-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="a06d6-108">Pro aplikace, které analyzovat výstupu kompilátoru může být pohodlnější kompilátor pro výstup jenom text diagnostiky.</span><span class="sxs-lookup"><span data-stu-id="a06d6-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="a06d6-109">V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `/quiet`.</span><span class="sxs-lookup"><span data-stu-id="a06d6-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a06d6-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a06d6-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="a06d6-111">Kompilované s `/quiet`, kompilátor výstupy jenom následující:</span><span class="sxs-lookup"><span data-stu-id="a06d6-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="a06d6-112">`/quiet` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a06d6-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a06d6-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a06d6-113">Example</span></span>  
 <span data-ttu-id="a06d6-114">Následující kód zkompiluje `T2.vb` a nezobrazí kód pro diagnostiku související syntaxe kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="a06d6-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a06d6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a06d6-115">See Also</span></span>  
 [<span data-ttu-id="a06d6-116">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a06d6-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a06d6-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a06d6-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
