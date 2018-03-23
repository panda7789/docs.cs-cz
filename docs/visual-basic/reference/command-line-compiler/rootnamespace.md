---
title: -rootnamespace
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45dce293549674e7e6aac2714e1a7a569719c597
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-rootnamespace"></a><span data-ttu-id="ea3ab-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="ea3ab-102">-rootnamespace</span></span>
<span data-ttu-id="ea3ab-103">Určuje obor názvů pro všechny deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea3ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea3ab-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="ea3ab-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ea3ab-105">Arguments</span></span>  
  
|<span data-ttu-id="ea3ab-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ea3ab-106">Term</span></span>|<span data-ttu-id="ea3ab-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ea3ab-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="ea3ab-108">Název oboru názvů, do kterého chcete uzavřete všechny deklarace typu pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea3ab-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea3ab-109">Remarks</span></span>  
 <span data-ttu-id="ea3ab-110">Pokud používáte Visual Studio spustitelný soubor (Devenv.exe) k sestavení projektu vytvořeny v integrovaném vývojovém prostředí sady Visual Studio, použijte `-rootnamespace` zadat hodnotu <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="ea3ab-111">V tématu [příkazového řádku DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) Další informace.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="ea3ab-112">Použijte modul common language runtime MSIL Disassembler (`Ildasm.exe`) Chcete-li zobrazit názvy oborů názvů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="ea3ab-113">Chcete-li nastavit - rootnamespace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea3ab-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ea3ab-114">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ea3ab-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ea3ab-116">2.  Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="ea3ab-117">3.  Změňte hodnotu v **kořenové Namespace** pole.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ea3ab-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea3ab-118">Example</span></span>  
 <span data-ttu-id="ea3ab-119">Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu do oboru názvů `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="ea3ab-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea3ab-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea3ab-120">See Also</span></span>  
 [<span data-ttu-id="ea3ab-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="ea3ab-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ea3ab-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="ea3ab-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="ea3ab-123">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ea3ab-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
