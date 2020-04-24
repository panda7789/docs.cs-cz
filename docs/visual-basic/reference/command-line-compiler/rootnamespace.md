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
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005206"
---
# <a name="-rootnamespace"></a><span data-ttu-id="39926-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="39926-102">-rootnamespace</span></span>
<span data-ttu-id="39926-103">Určuje obor názvů pro všechny deklarace typů.</span><span class="sxs-lookup"><span data-stu-id="39926-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39926-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39926-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="39926-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="39926-105">Arguments</span></span>  
  
|<span data-ttu-id="39926-106">Označení</span><span class="sxs-lookup"><span data-stu-id="39926-106">Term</span></span>|<span data-ttu-id="39926-107">Definice</span><span class="sxs-lookup"><span data-stu-id="39926-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="39926-108">Název oboru názvů, do kterého mají být uzavřeny všechny deklarace typu pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="39926-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39926-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39926-109">Remarks</span></span>  
 <span data-ttu-id="39926-110">Použijete-li spustitelný soubor sady Visual Studio (devenv. exe) ke kompilaci projektu vytvořeného v integrovaném vývojovém prostředí sady Visual `-rootnamespace` Studio, použijte k určení hodnoty <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="39926-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="39926-111">Další informace najdete v tématu [přepínače příkazového řádku devenv](/visualstudio/ide/reference/devenv-command-line-switches) .</span><span class="sxs-lookup"><span data-stu-id="39926-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="39926-112">Použijte modul common language runtime MSIL Disassembler (`Ildasm.exe`) pro zobrazení názvů oborů názvů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="39926-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="39926-113">Nastavení-RootNamespace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39926-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="39926-114">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="39926-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="39926-115">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="39926-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="39926-116">2. klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="39926-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="39926-117">3. upravte hodnotu v poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="39926-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39926-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="39926-118">Example</span></span>  
 <span data-ttu-id="39926-119">Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu v oboru názvů `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="39926-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="39926-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="39926-120">See also</span></span>

- [<span data-ttu-id="39926-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="39926-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="39926-122">Ildasm. exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="39926-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="39926-123">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="39926-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
