---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: b619505f6e87efd1c3b18e1bed2862d3467984a7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041086"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="4525d-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4525d-102">-out (Visual Basic)</span></span>
<span data-ttu-id="4525d-103">Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="4525d-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4525d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4525d-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4525d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4525d-105">Arguments</span></span>  
  
|<span data-ttu-id="4525d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="4525d-106">Term</span></span>|<span data-ttu-id="4525d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="4525d-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="4525d-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4525d-108">Required.</span></span> <span data-ttu-id="4525d-109">Název výstupního souboru, který kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="4525d-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="4525d-110">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="4525d-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4525d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4525d-111">Remarks</span></span>  
 <span data-ttu-id="4525d-112">Zadejte úplný název a příponu souboru k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="4525d-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="4525d-113">Pokud ho nevidíte, trvá tento soubor .exe její název ze soubor obsahující zdrojový kód `Sub Main` postupu a soubor .dll trvá jeho název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4525d-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="4525d-114">Pokud zadáte název souboru bez přípony .exe nebo .dll, kompilátor automaticky přidá rozšíření, v závislosti na hodnotě zadané pro `-target` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4525d-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="4525d-115">Chcete-li nastavit - out v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4525d-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4525d-116">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="4525d-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4525d-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4525d-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="4525d-118">2.  Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="4525d-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="4525d-119">3.  Upravte hodnotu v **název sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="4525d-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4525d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="4525d-120">Example</span></span>  
 <span data-ttu-id="4525d-121">Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="4525d-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="4525d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4525d-122">See Also</span></span>  
 [<span data-ttu-id="4525d-123">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4525d-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4525d-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4525d-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="4525d-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="4525d-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
