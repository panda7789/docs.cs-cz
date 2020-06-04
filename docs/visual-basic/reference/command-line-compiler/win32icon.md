---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414282"
---
# <a name="-win32icon"></a><span data-ttu-id="6fe03-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="6fe03-102">-win32icon</span></span>
<span data-ttu-id="6fe03-103">Vloží soubor. ico do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="6fe03-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="6fe03-104">Tento soubor. ico představuje výstupní soubor v **Průzkumníkovi souborů**.</span><span class="sxs-lookup"><span data-stu-id="6fe03-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe03-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fe03-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6fe03-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6fe03-106">Arguments</span></span>  
  
|<span data-ttu-id="6fe03-107">Pojem</span><span class="sxs-lookup"><span data-stu-id="6fe03-107">Term</span></span>|<span data-ttu-id="6fe03-108">Definice</span><span class="sxs-lookup"><span data-stu-id="6fe03-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="6fe03-109">Soubor. ico, který se má přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="6fe03-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="6fe03-110">Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="6fe03-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fe03-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fe03-111">Remarks</span></span>  
 <span data-ttu-id="6fe03-112">Soubor. ico můžete vytvořit pomocí kompilátoru Microsoft Windows Resource Compiler (RC).</span><span class="sxs-lookup"><span data-stu-id="6fe03-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="6fe03-113">Kompilátor prostředků je vyvolán při kompilování Visual C++ programu; soubor. ico je vytvořen ze souboru. rc.</span><span class="sxs-lookup"><span data-stu-id="6fe03-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="6fe03-114">`-win32icon`Možnosti a `-win32resource` se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="6fe03-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="6fe03-115">Viz [-linkresource – (Visual Basic)](linkresource.md) pro odkazování na soubor prostředků .NET Framework nebo [prostředku (Visual Basic)](resource.md) pro připojení souboru prostředků .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6fe03-115">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="6fe03-116">Viz [– Win32Resource](win32resource.md) pro import souboru. res.</span><span class="sxs-lookup"><span data-stu-id="6fe03-116">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="6fe03-117">Nastavení-win32icon v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6fe03-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="6fe03-118">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="6fe03-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6fe03-119">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6fe03-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6fe03-120">2. klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="6fe03-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="6fe03-121">3. upravte hodnotu v poli s **ikonami** .</span><span class="sxs-lookup"><span data-stu-id="6fe03-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6fe03-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fe03-122">Example</span></span>  
 <span data-ttu-id="6fe03-123">Následující kód zkompiluje `In.vb` a připojí soubor. ico, `Rf.ico` .</span><span class="sxs-lookup"><span data-stu-id="6fe03-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fe03-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fe03-124">See also</span></span>

- [<span data-ttu-id="6fe03-125">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6fe03-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6fe03-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6fe03-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
