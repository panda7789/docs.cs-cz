---
title: /win32resource
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d839b1100b1ae76fbd4653ebc60c79db11b77685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="win32resource"></a><span data-ttu-id="0d0f0-102">/win32resource</span><span class="sxs-lookup"><span data-stu-id="0d0f0-102">/win32resource</span></span>
<span data-ttu-id="0d0f0-103">Vloží zdrojového souboru Win32 ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d0f0-104">Syntax</span></span>  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d0f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d0f0-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0d0f0-106">Název souboru prostředků pro přidání do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="0d0f0-107">Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0f0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d0f0-108">Remarks</span></span>  
 <span data-ttu-id="0d0f0-109">Můžete vytvořit zdrojového souboru Win32 s Microsoft Windows prostředků kompilátoru (RC).</span><span class="sxs-lookup"><span data-stu-id="0d0f0-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="0d0f0-110">Win32 prostředků může obsahovat verzi nebo informace o bitové mapy (ikona), která pomáhá identifikovat aplikace v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="0d0f0-111">Pokud nezadáte `/win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-111">If you do not specify `/win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="0d0f0-112">`/win32resource` a `/win32icon` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-112">The `/win32resource` and `/win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0d0f0-113">Najdete v části [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků, nebo [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-113">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d0f0-114">`/win32resource` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0d0f0-114">The `/win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0f0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d0f0-115">Example</span></span>  
 <span data-ttu-id="0d0f0-116">Následující kód zkompiluje `In.vb` a připojí zdrojového souboru Win32 `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="0d0f0-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d0f0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d0f0-117">See Also</span></span>  
 [<span data-ttu-id="0d0f0-118">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0d0f0-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0d0f0-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0d0f0-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
