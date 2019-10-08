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
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004960"
---
# <a name="-win32resource"></a><span data-ttu-id="9ef62-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="9ef62-102">-win32resource</span></span>
<span data-ttu-id="9ef62-103">Vloží soubor prostředků Win32 do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9ef62-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ef62-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ef62-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9ef62-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9ef62-106">Název souboru prostředků, který se má přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9ef62-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="9ef62-107">Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="9ef62-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ef62-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ef62-108">Remarks</span></span>  
 <span data-ttu-id="9ef62-109">Soubor prostředků Win32 můžete vytvořit pomocí kompilátoru Microsoft Windows Resource Compiler (RC).</span><span class="sxs-lookup"><span data-stu-id="9ef62-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="9ef62-110">Prostředek Win32 může obsahovat informace o verzi nebo bitmapě (ikona), které pomáhají identifikovat vaši aplikaci v **Průzkumníkovi souborů**.</span><span class="sxs-lookup"><span data-stu-id="9ef62-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="9ef62-111">Pokud nezadáte `-win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ef62-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="9ef62-112">Možnosti `-win32resource` a `-win32icon` se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="9ef62-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="9ef62-113">Viz [-linkresource – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pro odkazování na soubor prostředků .NET Framework nebo [prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pro připojení souboru prostředků .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ef62-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ef62-114">Možnost `-win32resource` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef62-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ef62-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ef62-115">Example</span></span>  
 <span data-ttu-id="9ef62-116">Následující kód zkompiluje `In.vb` a připojí soubor prostředků Win32 `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="9ef62-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ef62-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ef62-117">See also</span></span>

- [<span data-ttu-id="9ef62-118">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="9ef62-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9ef62-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="9ef62-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
