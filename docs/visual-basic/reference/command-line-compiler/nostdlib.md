---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347915"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="b6727-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6727-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="b6727-103">Causes the compiler not to automatically reference the standard libraries.</span><span class="sxs-lookup"><span data-stu-id="b6727-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6727-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6727-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6727-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6727-105">Remarks</span></span>  
 <span data-ttu-id="b6727-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span><span class="sxs-lookup"><span data-stu-id="b6727-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="b6727-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="b6727-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6727-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span><span class="sxs-lookup"><span data-stu-id="b6727-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6727-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span><span class="sxs-lookup"><span data-stu-id="b6727-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6727-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6727-110">Example</span></span>  
 <span data-ttu-id="b6727-111">The following code compiles `T2.vb` without referencing the standard libraries.</span><span class="sxs-lookup"><span data-stu-id="b6727-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="b6727-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span><span class="sxs-lookup"><span data-stu-id="b6727-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6727-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6727-113">See also</span></span>

- [<span data-ttu-id="b6727-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="b6727-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="b6727-115">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="b6727-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b6727-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="b6727-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="b6727-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="b6727-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
