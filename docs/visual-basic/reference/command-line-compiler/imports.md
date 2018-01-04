---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="109f9-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="109f9-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="109f9-103">Obory názvů importuje ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="109f9-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="109f9-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="109f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="109f9-105">Arguments</span></span>  
  
|<span data-ttu-id="109f9-106">Termín</span><span class="sxs-lookup"><span data-stu-id="109f9-106">Term</span></span>|<span data-ttu-id="109f9-107">Definice</span><span class="sxs-lookup"><span data-stu-id="109f9-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="109f9-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="109f9-108">Required.</span></span> <span data-ttu-id="109f9-109">Čárkami oddělený seznam obory názvů určených k importu.</span><span class="sxs-lookup"><span data-stu-id="109f9-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="109f9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="109f9-110">Remarks</span></span>  
 <span data-ttu-id="109f9-111">`/imports` Možnost importuje obor názvů definované v rámci aktuální sadu zdrojových souborů nebo z všechny odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="109f9-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="109f9-112">Členy v oboru názvů zadaným `/imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="109f9-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="109f9-113">Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pomocí oboru názvů v souboru jednoho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="109f9-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="109f9-114">Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="109f9-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="109f9-115">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="109f9-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="109f9-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="109f9-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="109f9-117">2.  Klikněte **odkazy** kartě.</span><span class="sxs-lookup"><span data-stu-id="109f9-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="109f9-118">3.  Zadejte název oboru názvů do pole vedle položky **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="109f9-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="109f9-119">4.  Klikněte **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="109f9-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="109f9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="109f9-120">Example</span></span>  
 <span data-ttu-id="109f9-121">Následující kód zkompiluje při `/imports:system` je zadán.</span><span class="sxs-lookup"><span data-stu-id="109f9-121">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="109f9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="109f9-122">See Also</span></span>  
 [<span data-ttu-id="109f9-123">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="109f9-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="109f9-124">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="109f9-124">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="109f9-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="109f9-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
