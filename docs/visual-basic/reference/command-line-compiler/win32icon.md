---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e494e4e6fcbf91a7ab90b6922bc7bb4ace236b8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498632"
---
# <a name="-win32icon"></a><span data-ttu-id="100c1-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="100c1-102">-win32icon</span></span>
<span data-ttu-id="100c1-103">Vloží soubor .ico do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="100c1-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="100c1-104">Tento soubor .ico, který představuje výstupní soubor v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="100c1-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="100c1-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="100c1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="100c1-106">Arguments</span></span>  
  
|<span data-ttu-id="100c1-107">Termín</span><span class="sxs-lookup"><span data-stu-id="100c1-107">Term</span></span>|<span data-ttu-id="100c1-108">Definice</span><span class="sxs-lookup"><span data-stu-id="100c1-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="100c1-109">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="100c1-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="100c1-110">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="100c1-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="100c1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="100c1-111">Remarks</span></span>  
 <span data-ttu-id="100c1-112">Můžete vytvořit soubor .ico s Microsoft Windows Resource kompilátor (RC).</span><span class="sxs-lookup"><span data-stu-id="100c1-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="100c1-113">Nástroj resource compiler je vyvolán při kompilaci programu v jazyce Visual C++; soubor .ico je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="100c1-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="100c1-114">`-win32icon` a `-win32resource` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="100c1-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="100c1-115">Naleznete v tématu [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) na odkaz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="100c1-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="100c1-116">Zobrazit [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) importovat soubor .res.</span><span class="sxs-lookup"><span data-stu-id="100c1-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="100c1-117">Chcete-li nastavit - win32icon v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="100c1-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="100c1-118">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="100c1-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="100c1-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="100c1-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="100c1-120">2.  Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="100c1-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="100c1-121">3.  Upravte hodnotu v **ikonu** pole.</span><span class="sxs-lookup"><span data-stu-id="100c1-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="100c1-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="100c1-122">Example</span></span>  
 <span data-ttu-id="100c1-123">Následující kód zkompiluje `In.vb` a připojí soubor .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="100c1-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="100c1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="100c1-124">See also</span></span>
- [<span data-ttu-id="100c1-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="100c1-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="100c1-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="100c1-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
