---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004973"
---
# <a name="-verbose"></a><span data-ttu-id="2d537-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="2d537-102">-verbose</span></span>
<span data-ttu-id="2d537-103">Způsobí, že kompilátor vyprodukuje Podrobné stavové a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d537-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d537-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d537-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d537-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2d537-105">Arguments</span></span>  
 <span data-ttu-id="2d537-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2d537-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2d537-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2d537-107">Optional.</span></span> <span data-ttu-id="2d537-108">Zadání `-verbose` je stejné jako určení `-verbose+`, což způsobí, že kompilátor vygeneruje podrobné zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d537-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="2d537-109">Výchozí hodnota pro tuto možnost je `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="2d537-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d537-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d537-110">Remarks</span></span>  
 <span data-ttu-id="2d537-111">Možnost `-verbose` zobrazí informace o celkovém počtu chyb vydaných kompilátorem, sestav, které sestavení načítá modul, a zobrazuje, které soubory jsou aktuálně kompilovány.</span><span class="sxs-lookup"><span data-stu-id="2d537-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d537-112">Možnost `-verbose` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2d537-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d537-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d537-113">Example</span></span>  
 <span data-ttu-id="2d537-114">Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazoval podrobné informace o stavu.</span><span class="sxs-lookup"><span data-stu-id="2d537-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d537-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d537-115">See also</span></span>

- [<span data-ttu-id="2d537-116">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2d537-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2d537-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2d537-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
