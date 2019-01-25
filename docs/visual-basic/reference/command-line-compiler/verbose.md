---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 7a5dd305d1cc40e57d0f07f383151dc1a965bdda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513916"
---
# <a name="-verbose"></a><span data-ttu-id="c158b-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="c158b-102">-verbose</span></span>
<span data-ttu-id="c158b-103">Způsobí, že kompilátor vytvoří podrobné zprávy o stavu a chyba.</span><span class="sxs-lookup"><span data-stu-id="c158b-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c158b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c158b-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c158b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c158b-105">Arguments</span></span>  
 <span data-ttu-id="c158b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c158b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c158b-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c158b-107">Optional.</span></span> <span data-ttu-id="c158b-108">Určení `-verbose` je stejné jako zadání `-verbose+`, což způsobí, že kompilátor generuje podrobné zprávy.</span><span class="sxs-lookup"><span data-stu-id="c158b-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="c158b-109">Výchozí hodnota pro tuto možnost je `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="c158b-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c158b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c158b-110">Remarks</span></span>  
 <span data-ttu-id="c158b-111">`-verbose` Možnost zobrazí informace o celkový počet chyb, které jsou vydány kompilátorem, sestavy, která sestavení jsou načítány modulem a zobrazí soubory, které jsou aktuálně kompilován.</span><span class="sxs-lookup"><span data-stu-id="c158b-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c158b-112">`-verbose` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c158b-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c158b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c158b-113">Example</span></span>  
 <span data-ttu-id="c158b-114">Následující kód zkompiluje `In.vb` a instruuje kompilátor, aby zobrazení podrobné stavové informace.</span><span class="sxs-lookup"><span data-stu-id="c158b-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c158b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c158b-115">See also</span></span>
- [<span data-ttu-id="c158b-116">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="c158b-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c158b-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c158b-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
