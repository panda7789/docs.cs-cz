---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716652"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="a47c9-102">-Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a47c9-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="a47c9-103">Importuje obory názvů z určeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a47c9-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a47c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a47c9-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="a47c9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a47c9-105">Arguments</span></span>  
  
|<span data-ttu-id="a47c9-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a47c9-106">Term</span></span>|<span data-ttu-id="a47c9-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a47c9-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="a47c9-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a47c9-108">Required.</span></span> <span data-ttu-id="a47c9-109">Seznam oborů názvů oddělených čárkami, které se mají importovat</span><span class="sxs-lookup"><span data-stu-id="a47c9-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a47c9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a47c9-110">Remarks</span></span>  
 <span data-ttu-id="a47c9-111">Možnost `-imports` naimportuje libovolný obor názvů definovaný v aktuální sadě zdrojových souborů nebo z libovolného odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a47c9-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="a47c9-112">Členy v oboru názvů určeném pomocí `-imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a47c9-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="a47c9-113">Použijte [příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k použití oboru názvů v jednom souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a47c9-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="a47c9-114">Nastavení – importy v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a47c9-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="a47c9-115">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="a47c9-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a47c9-116">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a47c9-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="a47c9-117">2. klikněte na kartu **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="a47c9-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="a47c9-118">3. Zadejte název oboru názvů do pole vedle tlačítka **Přidat import uživatele** .</span><span class="sxs-lookup"><span data-stu-id="a47c9-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="a47c9-119">4. klikněte na tlačítko **Přidat import uživatele** .</span><span class="sxs-lookup"><span data-stu-id="a47c9-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a47c9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="a47c9-120">Example</span></span>  
 <span data-ttu-id="a47c9-121">Při zadání `-imports:system.globalization` je zkompilován následující kód.</span><span class="sxs-lookup"><span data-stu-id="a47c9-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="a47c9-122">Bez něho, úspěšná kompilace vyžaduje, aby byl příkaz `Imports System.Globalization` zahrnut na začátku souboru zdrojového kódu nebo aby byla vlastnost plně kvalifikovaná jako `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="a47c9-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="a47c9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a47c9-123">See also</span></span>

- [<span data-ttu-id="a47c9-124">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a47c9-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a47c9-125">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="a47c9-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="a47c9-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a47c9-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
