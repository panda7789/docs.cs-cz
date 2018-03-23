---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b91bf8efa6fabd21d257e51062dc881ab288f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="3e940-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e940-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="3e940-103">Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je součástí zadaná verze jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e940-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e940-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e940-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e940-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e940-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="3e940-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="3e940-106">Required.</span></span> <span data-ttu-id="3e940-107">Jazyková verze, která mají být použity během kompilace.</span><span class="sxs-lookup"><span data-stu-id="3e940-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="3e940-108">Platné hodnoty jsou `9`, `9.0`, `10`, a `10.0`.</span><span class="sxs-lookup"><span data-stu-id="3e940-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e940-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e940-109">Remarks</span></span>  
 <span data-ttu-id="3e940-110">`-langversion` Možnost určuje, jaké syntaxe kompilátor přijímá.</span><span class="sxs-lookup"><span data-stu-id="3e940-110">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="3e940-111">Například pokud jste určili, zda je verze jazyka 9.0, kompilátor generuje chyby syntaxe, která je platná pouze ve verzi 10.0 a novější.</span><span class="sxs-lookup"><span data-stu-id="3e940-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="3e940-112">Tuto možnost můžete použít při vývoji aplikací tento cíl různé verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e940-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="3e940-113">Například pokud cílíte na rozhraní .NET Framework 3.5, můžete použít tuto možnost k zajištění nepoužívejte syntaxe z jazyková verze 10.0.</span><span class="sxs-lookup"><span data-stu-id="3e940-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="3e940-114">Můžete nastavit `-langversion` přímo jen pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3e940-114">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="3e940-115">Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="3e940-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e940-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e940-116">Example</span></span>  
 <span data-ttu-id="3e940-117">Následující kód zkompiluje `sample.vb` pro 9.0 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e940-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e940-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e940-118">See Also</span></span>  
 [<span data-ttu-id="3e940-119">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="3e940-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3e940-120">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3e940-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="3e940-121">Cílení na konkrétní verzi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e940-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
