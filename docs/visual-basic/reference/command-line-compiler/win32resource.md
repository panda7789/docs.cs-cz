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
ms.openlocfilehash: d8f9c9aac87fd71b61a5413386582ae660efd903
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593070"
---
# <a name="-win32resource"></a><span data-ttu-id="039ad-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="039ad-102">-win32resource</span></span>
<span data-ttu-id="039ad-103">Vloží soubor prostředku Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="039ad-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="039ad-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="039ad-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="039ad-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="039ad-106">Název souboru prostředků pro přidání do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="039ad-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="039ad-107">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="039ad-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="039ad-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="039ad-108">Remarks</span></span>  
 <span data-ttu-id="039ad-109">Soubor prostředků Win32 lze vytvořit s Microsoft Windows Resource kompilátor (RC).</span><span class="sxs-lookup"><span data-stu-id="039ad-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="039ad-110">Prostředek systému Win32 mohou obsahovat verzi nebo rastrový obrázek (ikona) informace, které pomáhá identifikovat aplikaci v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="039ad-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="039ad-111">Pokud nezadáte `-win32resource`, kompilátor generuje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="039ad-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="039ad-112">`-win32resource` a `-win32icon` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="039ad-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="039ad-113">Zobrazit [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkázání na soubor prostředků rozhraní .NET Framework nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit soubor prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="039ad-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="039ad-114">`-win32resource` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="039ad-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="039ad-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="039ad-115">Example</span></span>  
 <span data-ttu-id="039ad-116">Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="039ad-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="039ad-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="039ad-117">See also</span></span>

- [<span data-ttu-id="039ad-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="039ad-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="039ad-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="039ad-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
