---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: e84ad094c2c7600535871b291d4dd535e667d8af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579573"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="5c1cb-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c1cb-102">-out (Visual Basic)</span></span>
<span data-ttu-id="5c1cb-103">Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c1cb-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="5c1cb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5c1cb-105">Arguments</span></span>  
  
|<span data-ttu-id="5c1cb-106">Termín</span><span class="sxs-lookup"><span data-stu-id="5c1cb-106">Term</span></span>|<span data-ttu-id="5c1cb-107">Definice</span><span class="sxs-lookup"><span data-stu-id="5c1cb-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="5c1cb-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-108">Required.</span></span> <span data-ttu-id="5c1cb-109">Název výstupního souboru, který kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="5c1cb-110">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="5c1cb-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c1cb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c1cb-111">Remarks</span></span>  
 <span data-ttu-id="5c1cb-112">Zadejte úplný název a příponu souboru k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="5c1cb-113">Pokud ho nevidíte, trvá tento soubor .exe její název ze soubor obsahující zdrojový kód `Sub Main` postupu a soubor .dll trvá jeho název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="5c1cb-114">Pokud zadáte název souboru bez přípony .exe nebo .dll, kompilátor automaticky přidá rozšíření, v závislosti na hodnotě zadané pro `-target` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="5c1cb-115">Chcete-li nastavit - out v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c1cb-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="5c1cb-116">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5c1cb-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="5c1cb-118">2.  Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="5c1cb-119">3.  Upravte hodnotu v **název sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5c1cb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c1cb-120">Example</span></span>  
 <span data-ttu-id="5c1cb-121">Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="5c1cb-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c1cb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c1cb-122">See also</span></span>
- [<span data-ttu-id="5c1cb-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="5c1cb-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5c1cb-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c1cb-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="5c1cb-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5c1cb-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
