---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045e621f0104c4c958d77d2443c1524b33410b7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650462"
---
# <a name="-win32icon"></a><span data-ttu-id="ccf92-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="ccf92-102">-win32icon</span></span>
<span data-ttu-id="ccf92-103">Vloží soubor .ico ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="ccf92-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="ccf92-104">Tento soubor .ico, který představuje výstupní soubor v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="ccf92-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf92-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccf92-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ccf92-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ccf92-106">Arguments</span></span>  
  
|<span data-ttu-id="ccf92-107">Termín</span><span class="sxs-lookup"><span data-stu-id="ccf92-107">Term</span></span>|<span data-ttu-id="ccf92-108">Definice</span><span class="sxs-lookup"><span data-stu-id="ccf92-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="ccf92-109">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="ccf92-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="ccf92-110">Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="ccf92-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccf92-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccf92-111">Remarks</span></span>  
 <span data-ttu-id="ccf92-112">Soubor .ico, který můžete vytvořit s Microsoft Windows prostředků kompilátoru (RC).</span><span class="sxs-lookup"><span data-stu-id="ccf92-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="ccf92-113">Kompilátor prostředků je vyvolán při kompilaci Visual C++ program; soubor .ico, který je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="ccf92-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="ccf92-114">`-win32icon` a `-win32resource` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="ccf92-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="ccf92-115">Najdete v části [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="ccf92-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="ccf92-116">V tématu [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res soubor naimportovat.</span><span class="sxs-lookup"><span data-stu-id="ccf92-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="ccf92-117">Chcete-li nastavit - win32icon v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ccf92-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="ccf92-118">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="ccf92-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ccf92-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ccf92-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ccf92-120">2.  Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="ccf92-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="ccf92-121">3.  Změňte hodnotu v **ikonu** pole.</span><span class="sxs-lookup"><span data-stu-id="ccf92-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ccf92-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccf92-122">Example</span></span>  
 <span data-ttu-id="ccf92-123">Následující kód zkompiluje `In.vb` a připojí soubor .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="ccf92-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccf92-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccf92-124">See Also</span></span>  
 [<span data-ttu-id="ccf92-125">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ccf92-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ccf92-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ccf92-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
