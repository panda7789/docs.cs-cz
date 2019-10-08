---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005443"
---
# <a name="-noconfig"></a><span data-ttu-id="43b64-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="43b64-102">-noconfig</span></span>
<span data-ttu-id="43b64-103">Určuje, že by kompilátor neměl automaticky odkazovat na běžně používaná .NET Framework sestavení nebo importovat obory názvů `System` a `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="43b64-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43b64-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="43b64-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43b64-105">Remarks</span></span>  
 <span data-ttu-id="43b64-106">Možnost `-noconfig` říká kompilátoru, že není zkompilován se souborem Vbc. rsp, který je umístěn ve stejném adresáři jako soubor Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="43b64-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="43b64-107">Soubor Vbc. rsp odkazuje na běžně používané .NET Framework sestavení a importuje obory názvů `System` a `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="43b64-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="43b64-108">Kompilátor implicitně odkazuje na sestavení System. dll, pokud není zadána možnost `-nostdlib`.</span><span class="sxs-lookup"><span data-stu-id="43b64-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="43b64-109">Možnost `-nostdlib` instruuje kompilátor, že není zkompilován s Vbc. rsp nebo automaticky odkazuje na sestavení System. dll.</span><span class="sxs-lookup"><span data-stu-id="43b64-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43b64-110">Na sestavení knihovny mscorlib. dll a Microsoft. VisualBasic. dll jsou odkazy vždy odkazovány.</span><span class="sxs-lookup"><span data-stu-id="43b64-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="43b64-111">Můžete upravit soubor Vbc. rsp a zadat další možnosti kompilátoru, které by měly být zahrnuty do každé kompilace Vbc. exe (kromě při určení možnosti `-noconfig`).</span><span class="sxs-lookup"><span data-stu-id="43b64-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="43b64-112">Další informace naleznete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="43b64-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="43b64-113">Kompilátor zpracovává možnosti, které byly předány příkazu `vbc` jako poslední.</span><span class="sxs-lookup"><span data-stu-id="43b64-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="43b64-114">Proto jakékoli možnosti na příkazovém řádku přepisuje nastavení stejné možnosti v souboru Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="43b64-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43b64-115">Možnost `-noconfig` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="43b64-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b64-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43b64-116">See also</span></span>

- [<span data-ttu-id="43b64-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b64-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="43b64-118">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="43b64-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="43b64-119">@ (určení souboru odezvy)</span><span class="sxs-lookup"><span data-stu-id="43b64-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="43b64-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b64-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
