---
title: /nostdlib (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d76563a5b3d439495899e07ce2df59c0acd75e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nostdlib-visual-basic"></a><span data-ttu-id="53c79-102">/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53c79-102">/nostdlib (Visual Basic)</span></span>
<span data-ttu-id="53c79-103">Způsobí, že kompilátor není odkazovat automaticky standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="53c79-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53c79-104">Syntax</span></span>  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="53c79-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53c79-105">Remarks</span></span>  
 <span data-ttu-id="53c79-106">`/nostdlib` Odebráno automatické odkaz na sestavení System.dll a zabrání čtení souboru Vbc.rsp kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="53c79-106">The `/nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="53c79-107">Soubor Vbc.rsp – který se nachází ve stejném adresáři jako soubor Vbc.exe – odkazuje běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="53c79-107">The Vbc.rsp file—which is located in the same directory as the Vbc.exe file—references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53c79-108">Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.</span><span class="sxs-lookup"><span data-stu-id="53c79-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53c79-109">`/nostdlib` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="53c79-109">The `/nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53c79-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c79-110">Example</span></span>  
 <span data-ttu-id="53c79-111">Následující kód zkompiluje `T2.vb` bez odkazující na standardní knihovny.</span><span class="sxs-lookup"><span data-stu-id="53c79-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="53c79-112">Je nutné nastavit `_MYTYPE` konstanty podmíněné kompilace řetězec "Prázdný" Odebrat `My` objektu.</span><span class="sxs-lookup"><span data-stu-id="53c79-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="53c79-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="53c79-113">See Also</span></span>  
 [<span data-ttu-id="53c79-114">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="53c79-114">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="53c79-115">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="53c79-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="53c79-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="53c79-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="53c79-117">Přizpůsobení výběru objektů jsou k dispozici v mé</span><span class="sxs-lookup"><span data-stu-id="53c79-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
