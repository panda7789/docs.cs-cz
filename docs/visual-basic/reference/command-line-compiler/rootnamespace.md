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
ms.openlocfilehash: b6a2f3ba0772d8f8c8c6a762a1be01703d21b778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403132"
---
# <a name="-rootnamespace"></a><span data-ttu-id="0c222-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0c222-102">-rootnamespace</span></span>
<span data-ttu-id="0c222-103">Určuje obor názvů pro všechny deklarace typů.</span><span class="sxs-lookup"><span data-stu-id="0c222-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c222-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c222-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c222-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0c222-105">Arguments</span></span>  
  
|<span data-ttu-id="0c222-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="0c222-106">Term</span></span>|<span data-ttu-id="0c222-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0c222-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="0c222-108">Název oboru názvů, do kterého mají být uzavřeny všechny deklarace typu pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="0c222-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c222-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c222-109">Remarks</span></span>  
 <span data-ttu-id="0c222-110">Použijete-li spustitelný soubor sady Visual Studio (devenv. exe) ke kompilaci projektu vytvořeného v integrovaném vývojovém prostředí sady Visual Studio, použijte `-rootnamespace` k určení hodnoty <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0c222-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="0c222-111">Další informace najdete v tématu [přepínače příkazového řádku devenv](/visualstudio/ide/reference/devenv-command-line-switches) .</span><span class="sxs-lookup"><span data-stu-id="0c222-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="0c222-112">Použijte modul common language runtime MSIL Disassembler ( `Ildasm.exe` ) pro zobrazení názvů oborů názvů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0c222-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="0c222-113">Nastavení-RootNamespace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0c222-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0c222-114">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="0c222-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0c222-115">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0c222-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0c222-116">2. klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="0c222-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="0c222-117">3. upravte hodnotu v poli **kořenový obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="0c222-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c222-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c222-118">Example</span></span>  
 <span data-ttu-id="0c222-119">Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu v oboru názvů `mynamespace` .</span><span class="sxs-lookup"><span data-stu-id="0c222-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c222-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c222-120">See also</span></span>

- [<span data-ttu-id="0c222-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0c222-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0c222-122">Ildasm. exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="0c222-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="0c222-123">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0c222-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
