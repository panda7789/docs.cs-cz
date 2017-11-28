---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d98a9f3cadc42021c302915cfc5b058b41e11ec6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="out-visual-basic"></a><span data-ttu-id="527ef-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="527ef-102">/out (Visual Basic)</span></span>
<span data-ttu-id="527ef-103">Určuje název souboru výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="527ef-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="527ef-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="527ef-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="527ef-105">Arguments</span></span>  
  
|<span data-ttu-id="527ef-106">Termín</span><span class="sxs-lookup"><span data-stu-id="527ef-106">Term</span></span>|<span data-ttu-id="527ef-107">Definice</span><span class="sxs-lookup"><span data-stu-id="527ef-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="527ef-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="527ef-108">Required.</span></span> <span data-ttu-id="527ef-109">Název výstupního souboru kompilátoru vytvoří.</span><span class="sxs-lookup"><span data-stu-id="527ef-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="527ef-110">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="527ef-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="527ef-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="527ef-111">Remarks</span></span>  
 <span data-ttu-id="527ef-112">Zadejte úplný název a příponu souboru pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="527ef-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="527ef-113">Pokud ho použít nechcete, soubor .exe trvá její název ze zdrojového kódu soubor obsahující `Sub Main` postupu a soubor .dll vezme její název ze první soubor zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="527ef-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="527ef-114">Pokud zadáte název souboru bez přípony .exe nebo .dll, kompilátor automaticky přidá rozšíření, v závislosti na zadaná hodnota parametru `/target` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="527ef-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="527ef-115">Chcete-li nastavit/out v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="527ef-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="527ef-116">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="527ef-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="527ef-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="527ef-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="527ef-118">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="527ef-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="527ef-119">2.  Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="527ef-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="527ef-120">3.  Změňte hodnotu v **název sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="527ef-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="527ef-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="527ef-121">Example</span></span>  
 <span data-ttu-id="527ef-122">Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="527ef-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="527ef-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="527ef-123">See Also</span></span>  
 [<span data-ttu-id="527ef-124">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="527ef-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="527ef-125">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="527ef-125">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="527ef-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="527ef-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
