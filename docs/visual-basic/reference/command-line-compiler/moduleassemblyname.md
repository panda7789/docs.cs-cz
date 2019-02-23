---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: f88a0001bb2ba55c0a3eac3ed208f14292d86734
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745661"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="ff464-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="ff464-102">-moduleassemblyname</span></span>
<span data-ttu-id="ff464-103">Určuje název sestavení, které bude tento modul součástí.</span><span class="sxs-lookup"><span data-stu-id="ff464-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff464-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff464-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff464-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ff464-105">Arguments</span></span>  
  
|<span data-ttu-id="ff464-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ff464-106">Term</span></span>|<span data-ttu-id="ff464-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ff464-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="ff464-108">Název sestavení, které bude tento modul součástí.</span><span class="sxs-lookup"><span data-stu-id="ff464-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff464-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff464-109">Remarks</span></span>  
 <span data-ttu-id="ff464-110">Procesy, které kompilátor `-moduleassemblyname` možnost pouze tehdy, pokud `-target:module` byla zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="ff464-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="ff464-111">To způsobí, že kompilátor vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="ff464-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="ff464-112">Modul vytvořený kompilátorem je platná pouze pro sestavení zadaným `-moduleassemblyname` možnost.</span><span class="sxs-lookup"><span data-stu-id="ff464-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="ff464-113">Pokud umístíte modulu v jiném sestavení, bude docházet k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="ff464-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="ff464-114">`-moduleassemblyname` Možnost je vyžadována, pouze v případě, že jsou splněny následující:</span><span class="sxs-lookup"><span data-stu-id="ff464-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="ff464-115">Datový typ v modulu potřebuje přístup k `Friend` typ v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff464-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="ff464-116">Odkazované sestavení má udělen Přátelský přístup sestavení k sestavení, do kterého bude sestaven modul.</span><span class="sxs-lookup"><span data-stu-id="ff464-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="ff464-117">Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="ff464-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="ff464-118">Další informace o přátelských sestavení naleznete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ff464-118">For more information about friend assemblies, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff464-119">`-moduleassemblyname` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ff464-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff464-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff464-120">See also</span></span>
- [<span data-ttu-id="ff464-121">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="ff464-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="ff464-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="ff464-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ff464-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff464-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="ff464-124">-main</span><span class="sxs-lookup"><span data-stu-id="ff464-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="ff464-125">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff464-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="ff464-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="ff464-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="ff464-127">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="ff464-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="ff464-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ff464-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ff464-129">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="ff464-129">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
