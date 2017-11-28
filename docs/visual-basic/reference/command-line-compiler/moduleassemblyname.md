---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a><span data-ttu-id="57008-102">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="57008-102">/moduleassemblyname</span></span>
<span data-ttu-id="57008-103">Určuje název sestavení, které tento modul bude součástí.</span><span class="sxs-lookup"><span data-stu-id="57008-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57008-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57008-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="57008-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="57008-105">Arguments</span></span>  
  
|<span data-ttu-id="57008-106">Termín</span><span class="sxs-lookup"><span data-stu-id="57008-106">Term</span></span>|<span data-ttu-id="57008-107">Definice</span><span class="sxs-lookup"><span data-stu-id="57008-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="57008-108">Název sestavení, které tento modul bude součástí.</span><span class="sxs-lookup"><span data-stu-id="57008-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57008-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57008-109">Remarks</span></span>  
 <span data-ttu-id="57008-110">Procesy kompilátoru `/moduleassemblyname` možnost jenom Pokud `/target:module` byla zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="57008-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="57008-111">To způsobí, že kompilátor Vytvořte modul.</span><span class="sxs-lookup"><span data-stu-id="57008-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="57008-112">Modul vytvořené kompilátor je platná pouze pro sestavení zadaným `/moduleassemblyname` možnost.</span><span class="sxs-lookup"><span data-stu-id="57008-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="57008-113">Pokud jste modul v jiném sestavení, dojde k chybám běhu.</span><span class="sxs-lookup"><span data-stu-id="57008-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="57008-114">`/moduleassemblyname` Možnost je nutný pouze v případě, že jsou pravdivé následující výroky:</span><span class="sxs-lookup"><span data-stu-id="57008-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="57008-115">Datový typ v modulu potřebuje přístup k `Friend` typu v odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="57008-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="57008-116">Odkazované sestavení udělil přístup přátelských sestavení do sestavení, do které budou vytvořeny v modulu.</span><span class="sxs-lookup"><span data-stu-id="57008-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="57008-117">Další informace o vytváření modulu najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="57008-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="57008-118">Další informace o přátelských sestavení najdete v tématu [přátelských sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="57008-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57008-119">`/moduleassemblyname` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57008-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57008-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="57008-120">See Also</span></span>  
 [<span data-ttu-id="57008-121">Postupy: vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="57008-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="57008-122">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="57008-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="57008-123">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57008-123">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="57008-124">/ main</span><span class="sxs-lookup"><span data-stu-id="57008-124">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="57008-125">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57008-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="57008-126">/ addmodule</span><span class="sxs-lookup"><span data-stu-id="57008-126">/addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="57008-127">Sestavení a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="57008-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="57008-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="57008-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="57008-129">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="57008-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
