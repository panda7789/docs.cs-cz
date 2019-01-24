---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: ff4b1729f1b9fb1d698b4b5b1e3711ce3d27b4db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655553"
---
# <a name="-rootnamespace"></a><span data-ttu-id="d87a8-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="d87a8-102">-rootnamespace</span></span>
<span data-ttu-id="d87a8-103">Určuje obor názvů pro všechny deklarace typů.</span><span class="sxs-lookup"><span data-stu-id="d87a8-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d87a8-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="d87a8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d87a8-105">Arguments</span></span>  
  
|<span data-ttu-id="d87a8-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d87a8-106">Term</span></span>|<span data-ttu-id="d87a8-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d87a8-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="d87a8-108">Název oboru názvů, ve kterém chcete uzavřít všechny deklarace typů pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="d87a8-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d87a8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d87a8-109">Remarks</span></span>  
 <span data-ttu-id="d87a8-110">Pokud používáte spustitelného souboru (Devenv.exe) sady Visual Studio ke kompilaci projektu vytvořeného v integrovaném vývojovém prostředí sady Visual Studio, použijte `-rootnamespace` k určení hodnoty <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d87a8-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="d87a8-111">Zobrazit [přepínače příkazového řádku nástroje Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Další informace.</span><span class="sxs-lookup"><span data-stu-id="d87a8-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="d87a8-112">Použít modul common language runtime MSIL Disassembler (`Ildasm.exe`) Chcete-li zobrazit názvy oborů názvů do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d87a8-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="d87a8-113">Chcete-li nastavit - rootnamespace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d87a8-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d87a8-114">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="d87a8-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d87a8-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d87a8-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d87a8-116">2.  Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="d87a8-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d87a8-117">3.  Upravte hodnotu v **kořenové Namespace** pole.</span><span class="sxs-lookup"><span data-stu-id="d87a8-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d87a8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d87a8-118">Example</span></span>  
 <span data-ttu-id="d87a8-119">Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typů v oboru názvů `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="d87a8-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d87a8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d87a8-120">See also</span></span>

- [<span data-ttu-id="d87a8-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d87a8-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d87a8-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="d87a8-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="d87a8-123">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d87a8-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
