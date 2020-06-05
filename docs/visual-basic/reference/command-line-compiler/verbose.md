---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403028"
---
# <a name="-verbose"></a><span data-ttu-id="85a71-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="85a71-102">-verbose</span></span>
<span data-ttu-id="85a71-103">Způsobí, že kompilátor vyprodukuje Podrobné stavové a chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="85a71-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85a71-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="85a71-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="85a71-105">Arguments</span></span>  
 <span data-ttu-id="85a71-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="85a71-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="85a71-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="85a71-107">Optional.</span></span> <span data-ttu-id="85a71-108">Určení `-verbose` je stejné jako při zadání `-verbose+` , což způsobí, že kompilátor vygeneruje podrobné zprávy.</span><span class="sxs-lookup"><span data-stu-id="85a71-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="85a71-109">Výchozí hodnota pro tuto možnost je `-verbose-` .</span><span class="sxs-lookup"><span data-stu-id="85a71-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85a71-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85a71-110">Remarks</span></span>  
 <span data-ttu-id="85a71-111">`-verbose`Možnost zobrazí informace o celkovém počtu chyb vydaných kompilátorem, sestav, které sestavení načítá modul, a zobrazuje, které soubory jsou aktuálně kompilovány.</span><span class="sxs-lookup"><span data-stu-id="85a71-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85a71-112">Tato `-verbose` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="85a71-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85a71-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="85a71-113">Example</span></span>  
 <span data-ttu-id="85a71-114">Následující kód zkompiluje `In.vb` a nasměruje kompilátor pro zobrazení podrobných informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="85a71-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="85a71-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="85a71-115">See also</span></span>

- [<span data-ttu-id="85a71-116">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="85a71-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="85a71-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="85a71-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
