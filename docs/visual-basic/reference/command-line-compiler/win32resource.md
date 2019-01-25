---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 05dcaa18d799912d1b92685338a269a050db3f1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703481"
---
# <a name="-win32resource"></a><span data-ttu-id="0a187-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="0a187-102">-win32resource</span></span>
<span data-ttu-id="0a187-103">Vloží soubor prostředku Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0a187-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a187-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a187-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0a187-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0a187-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0a187-106">Název souboru prostředků pro přidání do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0a187-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="0a187-107">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="0a187-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a187-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a187-108">Remarks</span></span>  
 <span data-ttu-id="0a187-109">Soubor prostředků Win32 lze vytvořit s Microsoft Windows Resource kompilátor (RC).</span><span class="sxs-lookup"><span data-stu-id="0a187-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="0a187-110">Prostředek systému Win32 mohou obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomáhá identifikovat aplikaci v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="0a187-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="0a187-111">Pokud nezadáte `-win32resource`, kompilátor generuje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a187-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="0a187-112">`-win32resource` a `-win32icon` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="0a187-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0a187-113">Naleznete v tématu [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) na odkaz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="0a187-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a187-114">`-win32resource` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0a187-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a187-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a187-115">Example</span></span>  
 <span data-ttu-id="0a187-116">Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="0a187-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a187-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a187-117">See also</span></span>
- [<span data-ttu-id="0a187-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0a187-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0a187-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0a187-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
