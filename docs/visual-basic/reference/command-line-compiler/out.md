---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 75f3ee7f24112f911803732ccb8d39eeafa95e3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400510"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="63378-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63378-102">-out (Visual Basic)</span></span>
<span data-ttu-id="63378-103">Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="63378-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63378-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63378-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="63378-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="63378-105">Arguments</span></span>  
  
|<span data-ttu-id="63378-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="63378-106">Term</span></span>|<span data-ttu-id="63378-107">Definice</span><span class="sxs-lookup"><span data-stu-id="63378-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="63378-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="63378-108">Required.</span></span> <span data-ttu-id="63378-109">Název výstupního souboru, který kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="63378-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="63378-110">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="63378-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63378-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63378-111">Remarks</span></span>  
 <span data-ttu-id="63378-112">Zadejte úplný název a příponu souboru, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="63378-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="63378-113">Pokud to neuděláte, soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje `Sub Main` proceduru, a soubor. dll převezme svůj název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="63378-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="63378-114">Pokud zadáte název souboru bez přípony. exe nebo. dll, kompilátor pro vás automaticky přidá rozšíření v závislosti na hodnotě zadané pro `-target` možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="63378-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="63378-115">Nastavení v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63378-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="63378-116">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="63378-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="63378-117">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="63378-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="63378-118">2. klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="63378-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="63378-119">3. upravte hodnotu v poli **název sestavení** .</span><span class="sxs-lookup"><span data-stu-id="63378-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63378-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="63378-120">Example</span></span>  
 <span data-ttu-id="63378-121">Následující kód zkompiluje `T2.vb` a vytvoří výstupní soubor `T2.exe` .</span><span class="sxs-lookup"><span data-stu-id="63378-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="63378-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="63378-122">See also</span></span>

- [<span data-ttu-id="63378-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="63378-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="63378-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63378-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="63378-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="63378-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
