---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="edc07-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="edc07-102">/rootnamespace</span></span>
<span data-ttu-id="edc07-103">Určuje obor názvů pro všechny deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="edc07-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edc07-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="edc07-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="edc07-105">Arguments</span></span>  
  
|<span data-ttu-id="edc07-106">Termín</span><span class="sxs-lookup"><span data-stu-id="edc07-106">Term</span></span>|<span data-ttu-id="edc07-107">Definice</span><span class="sxs-lookup"><span data-stu-id="edc07-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="edc07-108">Název oboru názvů, do kterého chcete uzavřete všechny deklarace typu pro aktuální projekt.</span><span class="sxs-lookup"><span data-stu-id="edc07-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edc07-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edc07-109">Remarks</span></span>  
 <span data-ttu-id="edc07-110">Pokud používáte Visual Studio spustitelný soubor (Devenv.exe) k sestavení projektu vytvořeny v integrovaném vývojovém prostředí sady Visual Studio, použijte `/rootnamespace` zadat hodnotu <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="edc07-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="edc07-111">V tématu [příkazového řádku DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) Další informace.</span><span class="sxs-lookup"><span data-stu-id="edc07-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="edc07-112">Použijte modul common language runtime MSIL Disassembler (`Ildasm.exe`) Chcete-li zobrazit názvy oborů názvů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="edc07-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="edc07-113">Chcete-li nastavit/RootNamespace v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="edc07-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="edc07-114">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="edc07-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="edc07-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="edc07-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="edc07-116">2.  Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="edc07-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="edc07-117">3.  Změňte hodnotu v **kořenové Namespace** pole.</span><span class="sxs-lookup"><span data-stu-id="edc07-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="edc07-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="edc07-118">Example</span></span>  
 <span data-ttu-id="edc07-119">Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu do oboru názvů `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="edc07-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="edc07-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="edc07-120">See Also</span></span>  
 [<span data-ttu-id="edc07-121">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="edc07-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="edc07-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="edc07-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="edc07-123">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="edc07-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
