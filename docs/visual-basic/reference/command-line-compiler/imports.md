---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 075eeccc7d80943d2757a97b9a355bbea3ef9d4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833604"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="1ebd8-102">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ebd8-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="1ebd8-103">Obory názvů importuje ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ebd8-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ebd8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ebd8-105">Arguments</span></span>  
  
|<span data-ttu-id="1ebd8-106">Termín</span><span class="sxs-lookup"><span data-stu-id="1ebd8-106">Term</span></span>|<span data-ttu-id="1ebd8-107">Definice</span><span class="sxs-lookup"><span data-stu-id="1ebd8-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="1ebd8-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-108">Required.</span></span> <span data-ttu-id="1ebd8-109">Čárkami oddělený seznam oborů názvů, které se mají naimportovat.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ebd8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ebd8-110">Remarks</span></span>  
 <span data-ttu-id="1ebd8-111">`-imports` Možnost importuje libovolný obor názvů definovaných v rámci aktuální sadu zdrojových souborů nebo ze všech odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="1ebd8-112">Členové v oboru názvů zadaným `-imports` jsou k dispozici pro všechny soubory zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="1ebd8-113">Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro použití oboru názvů v souboru jednoho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="1ebd8-114">Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ebd8-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1ebd8-115">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1ebd8-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1ebd8-117">2.  Klikněte na tlačítko **odkazy** kartu.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="1ebd8-118">3.  Zadejte název oboru názvů v seznamu vedle možnosti **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="1ebd8-119">4.  Klikněte na tlačítko **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ebd8-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ebd8-120">Example</span></span>  
 <span data-ttu-id="1ebd8-121">Následující kód zkompiluje, kdy `/imports:system.globalization` je zadán.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="1ebd8-122">Bez něho úspěšné kompilace vyžaduje buď `Imports System.Globalization` příkazem být zahrnuty na začátku souboru se zdrojovým kódem, nebo jako plně kvalifikovat vlastnost `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="1ebd8-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="1ebd8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-123">See also</span></span>

- [<span data-ttu-id="1ebd8-124">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="1ebd8-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1ebd8-125">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="1ebd8-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="1ebd8-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1ebd8-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
