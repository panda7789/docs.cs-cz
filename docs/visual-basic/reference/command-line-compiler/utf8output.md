---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 5cdc60888cd872940afc1b03febd879bb6d87c2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350839"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="6766f-102">-Utf8Output – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6766f-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="6766f-103">Zobrazí výstup kompilátoru pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6766f-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6766f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6766f-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6766f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6766f-105">Arguments</span></span>  
 <span data-ttu-id="6766f-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="6766f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="6766f-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6766f-107">Optional.</span></span> <span data-ttu-id="6766f-108">Výchozí hodnota pro tuto možnost je `-utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6766f-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="6766f-109">Určení `-utf8output` je stejné jako zadání `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="6766f-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6766f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6766f-110">Remarks</span></span>  
 <span data-ttu-id="6766f-111">V některých mezinárodních konfiguracích nelze výstup kompilátoru v konzole zobrazit správně.</span><span class="sxs-lookup"><span data-stu-id="6766f-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="6766f-112">V takových situacích použijte `-utf8output` a přesměrujte výstup kompilátoru do souboru.</span><span class="sxs-lookup"><span data-stu-id="6766f-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6766f-113">Tato `-utf8output` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6766f-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6766f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6766f-114">Example</span></span>  
 <span data-ttu-id="6766f-115">Následující kód zkompiluje `In.vb` a nasměruje kompilátor pro zobrazení výstupu pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="6766f-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6766f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6766f-116">See also</span></span>

- [<span data-ttu-id="6766f-117">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6766f-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6766f-118">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6766f-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
