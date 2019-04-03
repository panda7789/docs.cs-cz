---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e36e9187ab8c9c2b4950a66ff8ff3fc93adbd9c4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821475"
---
# <a name="-win32icon"></a><span data-ttu-id="fed3a-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="fed3a-102">-win32icon</span></span>
<span data-ttu-id="fed3a-103">Vloží soubor .ico do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="fed3a-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="fed3a-104">Tento soubor .ico, který představuje výstupní soubor v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="fed3a-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed3a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fed3a-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="fed3a-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="fed3a-106">Arguments</span></span>  
  
|<span data-ttu-id="fed3a-107">Termín</span><span class="sxs-lookup"><span data-stu-id="fed3a-107">Term</span></span>|<span data-ttu-id="fed3a-108">Definice</span><span class="sxs-lookup"><span data-stu-id="fed3a-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="fed3a-109">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="fed3a-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="fed3a-110">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="fed3a-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fed3a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fed3a-111">Remarks</span></span>  
 <span data-ttu-id="fed3a-112">Můžete vytvořit soubor .ico s Microsoft Windows Resource kompilátor (RC).</span><span class="sxs-lookup"><span data-stu-id="fed3a-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="fed3a-113">Nástroj resource compiler je vyvolán při kompilaci programu v jazyce Visual C++; soubor .ico je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="fed3a-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="fed3a-114">`-win32icon` a `-win32resource` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="fed3a-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="fed3a-115">Naleznete v tématu [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) na odkaz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="fed3a-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="fed3a-116">Zobrazit [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) importovat soubor .res.</span><span class="sxs-lookup"><span data-stu-id="fed3a-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="fed3a-117">Chcete-li nastavit - win32icon v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fed3a-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="fed3a-118">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="fed3a-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fed3a-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fed3a-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fed3a-120">2.  Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="fed3a-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="fed3a-121">3.  Upravte hodnotu v **ikonu** pole.</span><span class="sxs-lookup"><span data-stu-id="fed3a-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fed3a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="fed3a-122">Example</span></span>  
 <span data-ttu-id="fed3a-123">Následující kód zkompiluje `In.vb` a připojí soubor .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="fed3a-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fed3a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fed3a-124">See also</span></span>

- [<span data-ttu-id="fed3a-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="fed3a-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fed3a-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="fed3a-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
