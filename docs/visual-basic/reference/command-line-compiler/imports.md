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
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="bcc60-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc60-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="bcc60-103">Obory názvů importuje ze zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcc60-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcc60-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bcc60-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bcc60-105">Arguments</span></span>  
  
|<span data-ttu-id="bcc60-106">Termín</span><span class="sxs-lookup"><span data-stu-id="bcc60-106">Term</span></span>|<span data-ttu-id="bcc60-107">Definice</span><span class="sxs-lookup"><span data-stu-id="bcc60-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="bcc60-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bcc60-108">Required.</span></span> <span data-ttu-id="bcc60-109">Čárkami oddělený seznam obory názvů určených k importu.</span><span class="sxs-lookup"><span data-stu-id="bcc60-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc60-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcc60-110">Remarks</span></span>  
 <span data-ttu-id="bcc60-111">`/imports` Možnost importuje obor názvů definované v rámci aktuální sadu zdrojových souborů nebo z všechny odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcc60-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="bcc60-112">Členy v oboru názvů zadaným `/imports` jsou k dispozici pro všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="bcc60-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="bcc60-113">Použít [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pomocí oboru názvů v souboru jednoho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="bcc60-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="bcc60-114">Chcete-li nastavit/importuje v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bcc60-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bcc60-115">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="bcc60-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bcc60-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="bcc60-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="bcc60-117">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="bcc60-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="bcc60-118">2.  Klikněte **odkazy** kartě.</span><span class="sxs-lookup"><span data-stu-id="bcc60-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="bcc60-119">3.  Zadejte název oboru názvů do pole vedle položky **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bcc60-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="bcc60-120">4.  Klikněte **přidat Import uživatelů** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bcc60-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bcc60-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcc60-121">Example</span></span>  
 <span data-ttu-id="bcc60-122">Následující kód zkompiluje při `/imports:system` je zadán.</span><span class="sxs-lookup"><span data-stu-id="bcc60-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bcc60-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcc60-123">See Also</span></span>  
 [<span data-ttu-id="bcc60-124">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bcc60-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bcc60-125">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="bcc60-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="bcc60-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="bcc60-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
