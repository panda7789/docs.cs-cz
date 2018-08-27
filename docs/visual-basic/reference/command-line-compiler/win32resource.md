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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac495e10be2ec1534dc9d9081aef369773d93e17
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933048"
---
# <a name="-win32resource"></a><span data-ttu-id="a823a-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="a823a-102">-win32resource</span></span>
<span data-ttu-id="a823a-103">Vloží soubor prostředku Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="a823a-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a823a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a823a-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="a823a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a823a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a823a-106">Název souboru prostředků pro přidání do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="a823a-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="a823a-107">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="a823a-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a823a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a823a-108">Remarks</span></span>  
 <span data-ttu-id="a823a-109">Soubor prostředků Win32 lze vytvořit s Microsoft Windows Resource kompilátor (RC).</span><span class="sxs-lookup"><span data-stu-id="a823a-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="a823a-110">Prostředek systému Win32 mohou obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomáhá identifikovat aplikaci v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="a823a-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="a823a-111">Pokud nezadáte `-win32resource`, kompilátor generuje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="a823a-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="a823a-112">`-win32resource` a `-win32icon` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="a823a-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="a823a-113">Naleznete v tématu [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) na odkaz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="a823a-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a823a-114">`-win32resource` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a823a-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a823a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a823a-115">Example</span></span>  
 <span data-ttu-id="a823a-116">Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="a823a-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a823a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a823a-117">See Also</span></span>  
 [<span data-ttu-id="a823a-118">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a823a-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a823a-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a823a-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
