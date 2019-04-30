---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: b0279c5ac658c7d0749f62066abbd705d0a271af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793897"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="0ccd2-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="0ccd2-102">-moduleassemblyname</span></span>
<span data-ttu-id="0ccd2-103">Určuje název sestavení, které bude tento modul součástí.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ccd2-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ccd2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ccd2-105">Arguments</span></span>  
  
|<span data-ttu-id="0ccd2-106">Termín</span><span class="sxs-lookup"><span data-stu-id="0ccd2-106">Term</span></span>|<span data-ttu-id="0ccd2-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0ccd2-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="0ccd2-108">Název sestavení, které bude tento modul součástí.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ccd2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ccd2-109">Remarks</span></span>  
 <span data-ttu-id="0ccd2-110">Procesy, které kompilátor `-moduleassemblyname` možnost pouze tehdy, pokud `-target:module` byla zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="0ccd2-111">To způsobí, že kompilátor vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="0ccd2-112">Modul vytvořený kompilátorem je platná pouze pro sestavení zadaným `-moduleassemblyname` možnost.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="0ccd2-113">Pokud umístíte modulu v jiném sestavení, bude docházet k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="0ccd2-114">`-moduleassemblyname` Možnost je vyžadována, pouze v případě, že jsou splněny následující:</span><span class="sxs-lookup"><span data-stu-id="0ccd2-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="0ccd2-115">Datový typ v modulu potřebuje přístup k `Friend` typ v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="0ccd2-116">Odkazované sestavení má udělen Přátelský přístup sestavení k sestavení, do kterého bude sestaven modul.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="0ccd2-117">Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="0ccd2-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="0ccd2-118">Další informace o přátelských sestavení naleznete v tématu [přátelských sestavení](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0ccd2-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ccd2-119">`-moduleassemblyname` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0ccd2-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccd2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ccd2-120">See also</span></span>

- [<span data-ttu-id="0ccd2-121">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="0ccd2-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="0ccd2-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0ccd2-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0ccd2-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ccd2-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="0ccd2-124">-main</span><span class="sxs-lookup"><span data-stu-id="0ccd2-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="0ccd2-125">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ccd2-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="0ccd2-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="0ccd2-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="0ccd2-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="0ccd2-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="0ccd2-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0ccd2-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="0ccd2-129">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="0ccd2-129">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
