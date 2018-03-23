---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="57e67-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e67-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="57e67-103">Způsobí, že kompilátor není odkazovat automaticky standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="57e67-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57e67-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="57e67-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57e67-105">Remarks</span></span>  
 <span data-ttu-id="57e67-106">`-nostdlib` Odebráno automatické odkaz na sestavení System.dll a zabrání čtení souboru Vbc.rsp kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="57e67-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="57e67-107">Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe, odkazuje na běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="57e67-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57e67-108">Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.</span><span class="sxs-lookup"><span data-stu-id="57e67-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57e67-109">`-nostdlib` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="57e67-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e67-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="57e67-110">Example</span></span>  
 <span data-ttu-id="57e67-111">Následující kód zkompiluje `T2.vb` bez odkazující na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="57e67-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="57e67-112">Je nutné nastavit `_MYTYPE` konstanty podmíněné kompilace řetězec "Prázdný" Odebrat `My` objektu.</span><span class="sxs-lookup"><span data-stu-id="57e67-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="57e67-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="57e67-113">See Also</span></span>  
 [<span data-ttu-id="57e67-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="57e67-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="57e67-115">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="57e67-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="57e67-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="57e67-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="57e67-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="57e67-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
