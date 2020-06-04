---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403054"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="d4229-102">-Utf8Output – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4229-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="d4229-103">Zobrazí výstup kompilátoru pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d4229-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4229-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4229-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4229-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d4229-105">Arguments</span></span>  
 <span data-ttu-id="d4229-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="d4229-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d4229-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d4229-107">Optional.</span></span> <span data-ttu-id="d4229-108">Výchozí hodnota pro tuto možnost je `-utf8output-` , což znamená, že výstup kompilátoru nepoužívá kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d4229-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="d4229-109">Určení `-utf8output` je stejné jako zadání `-utf8output+` .</span><span class="sxs-lookup"><span data-stu-id="d4229-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4229-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4229-110">Remarks</span></span>  
 <span data-ttu-id="d4229-111">V některých mezinárodních konfiguracích nelze výstup kompilátoru v konzole zobrazit správně.</span><span class="sxs-lookup"><span data-stu-id="d4229-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="d4229-112">V takových situacích použijte `-utf8output` a přesměrujte výstup kompilátoru do souboru.</span><span class="sxs-lookup"><span data-stu-id="d4229-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4229-113">Tato `-utf8output` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d4229-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4229-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4229-114">Example</span></span>  
 <span data-ttu-id="d4229-115">Následující kód zkompiluje `In.vb` a nasměruje kompilátor pro zobrazení výstupu pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d4229-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4229-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4229-116">See also</span></span>

- [<span data-ttu-id="d4229-117">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d4229-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d4229-118">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d4229-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
