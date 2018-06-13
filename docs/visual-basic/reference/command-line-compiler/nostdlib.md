---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652715"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="ddcf3-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddcf3-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="ddcf3-103">Způsobí, že kompilátor není odkazovat automaticky standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcf3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddcf3-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="ddcf3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddcf3-105">Remarks</span></span>  
 <span data-ttu-id="ddcf3-106">`-nostdlib` Odebráno automatické odkaz na sestavení System.dll a zabrání čtení souboru Vbc.rsp kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="ddcf3-107">Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe, odkazuje na běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddcf3-108">Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddcf3-109">`-nostdlib` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcf3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddcf3-110">Example</span></span>  
 <span data-ttu-id="ddcf3-111">Následující kód zkompiluje `T2.vb` bez odkazující na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="ddcf3-112">Je nutné nastavit `_MYTYPE` konstanty podmíněné kompilace řetězec "Prázdný" Odebrat `My` objektu.</span><span class="sxs-lookup"><span data-stu-id="ddcf3-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddcf3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddcf3-113">See Also</span></span>  
 [<span data-ttu-id="ddcf3-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="ddcf3-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="ddcf3-115">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ddcf3-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ddcf3-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ddcf3-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ddcf3-117">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="ddcf3-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
