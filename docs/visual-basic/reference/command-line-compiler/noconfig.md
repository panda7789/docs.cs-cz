---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401937"
---
# <a name="-noconfig"></a><span data-ttu-id="5545a-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="5545a-102">-noconfig</span></span>
<span data-ttu-id="5545a-103">Určuje, že by kompilátor neměl automaticky odkazovat na běžně používaná .NET Framework sestavení nebo importovat `System` `Microsoft.VisualBasic` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="5545a-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5545a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5545a-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="5545a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5545a-105">Remarks</span></span>  
 <span data-ttu-id="5545a-106">`-noconfig`Možnost instruuje kompilátor, že není zkompilován se souborem Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="5545a-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="5545a-107">Soubor Vbc. rsp odkazuje na běžně používaná .NET Framework sestavení a importuje `System` `Microsoft.VisualBasic` obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="5545a-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="5545a-108">Kompilátor implicitně odkazuje na sestavení System. dll, pokud `-nostdlib` není zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="5545a-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="5545a-109">`-nostdlib`Možnost instruuje kompilátor, že není zkompilován s Vbc. rsp nebo automaticky odkazuje na sestavení System. dll.</span><span class="sxs-lookup"><span data-stu-id="5545a-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5545a-110">Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.</span><span class="sxs-lookup"><span data-stu-id="5545a-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="5545a-111">Můžete upravit soubor Vbc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace Vbc. exe (kromě při určení `-noconfig` Možnosti).</span><span class="sxs-lookup"><span data-stu-id="5545a-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="5545a-112">Další informace naleznete v tématu [@ (určení souboru odezvy)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="5545a-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="5545a-113">Kompilátor zpracovává možnosti předané `vbc` příkazu jako poslední.</span><span class="sxs-lookup"><span data-stu-id="5545a-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="5545a-114">Proto jakékoli možnosti na příkazovém řádku přepisuje nastavení stejné možnosti v souboru Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="5545a-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5545a-115">Tato `-noconfig` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5545a-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5545a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5545a-116">See also</span></span>

- [<span data-ttu-id="5545a-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5545a-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="5545a-118">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5545a-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5545a-119">@ (určení souboru odezvy)</span><span class="sxs-lookup"><span data-stu-id="5545a-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="5545a-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5545a-120">-reference (Visual Basic)</span></span>](reference.md)
