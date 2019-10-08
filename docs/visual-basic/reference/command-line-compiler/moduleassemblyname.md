---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 5b26e36346858d95526f5d5ce7d4645bea1dbe05
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005476"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="f8356-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="f8356-102">-moduleassemblyname</span></span>
<span data-ttu-id="f8356-103">Určuje název sestavení, jehož součástí bude tento modul.</span><span class="sxs-lookup"><span data-stu-id="f8356-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8356-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8356-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8356-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f8356-105">Arguments</span></span>  
  
|<span data-ttu-id="f8356-106">Termín</span><span class="sxs-lookup"><span data-stu-id="f8356-106">Term</span></span>|<span data-ttu-id="f8356-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f8356-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="f8356-108">Název sestavení, jehož součástí bude tento modul.</span><span class="sxs-lookup"><span data-stu-id="f8356-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8356-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8356-109">Remarks</span></span>  
 <span data-ttu-id="f8356-110">Kompilátor zpracovává možnost `-moduleassemblyname` pouze v případě, že byla zadána možnost `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="f8356-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="f8356-111">Způsobí to, že kompilátor vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="f8356-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="f8356-112">Modul vytvořený kompilátorem je platný pouze pro sestavení zadané s možností `-moduleassemblyname`.</span><span class="sxs-lookup"><span data-stu-id="f8356-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="f8356-113">Pokud umístíte modul do jiného sestavení, dojde k chybám za běhu.</span><span class="sxs-lookup"><span data-stu-id="f8356-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="f8356-114">Možnost `-moduleassemblyname` je nutná pouze v případě, že jsou splněny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="f8356-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="f8356-115">Datový typ v modulu potřebuje přístup k typu `Friend` v odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8356-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="f8356-116">Odkazované sestavení udělilo přístup přítel k sestavení, do kterého bude modul sestaven.</span><span class="sxs-lookup"><span data-stu-id="f8356-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="f8356-117">Další informace o vytváření modulu naleznete v tématu [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="f8356-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="f8356-118">Další informace o Friend sestaveních naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="f8356-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8356-119">Možnost `-moduleassemblyname` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f8356-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8356-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8356-120">See also</span></span>

- [<span data-ttu-id="f8356-121">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="f8356-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="f8356-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f8356-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f8356-123">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8356-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f8356-124">-main</span><span class="sxs-lookup"><span data-stu-id="f8356-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="f8356-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8356-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="f8356-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="f8356-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="f8356-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="f8356-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="f8356-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f8356-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="f8356-129">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="f8356-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
