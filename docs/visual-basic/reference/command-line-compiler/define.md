---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="7276c-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7276c-102">/define (Visual Basic)</span></span>
<span data-ttu-id="7276c-103">Definuje podmíněného kompilátoru konstanty.</span><span class="sxs-lookup"><span data-stu-id="7276c-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7276c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7276c-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7276c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7276c-105">Arguments</span></span>  
  
|<span data-ttu-id="7276c-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7276c-106">Term</span></span>|<span data-ttu-id="7276c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7276c-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="7276c-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7276c-108">Required.</span></span> <span data-ttu-id="7276c-109">Symbol, který se má definovat.</span><span class="sxs-lookup"><span data-stu-id="7276c-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="7276c-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7276c-110">Optional.</span></span> <span data-ttu-id="7276c-111">Hodnota pro přiřazení `symbol`.</span><span class="sxs-lookup"><span data-stu-id="7276c-111">The value to assign `symbol`.</span></span> <span data-ttu-id="7276c-112">Pokud `value` je řetězec, musí být uzavřena tak pro pořadí zpětné lomítko /-dvojité uvozovky (\\") namísto uvozovky.</span><span class="sxs-lookup"><span data-stu-id="7276c-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="7276c-113">Pokud není zadaná žádná hodnota, pak se provede na hodnotu True.</span><span class="sxs-lookup"><span data-stu-id="7276c-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7276c-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7276c-114">Remarks</span></span>  
 <span data-ttu-id="7276c-115">`/define` Má vliv podobný používání `#Const` direktivy preprocesoru zdrojový soubor, s výjimkou tohoto konstanty definovaný s `/define` jsou veřejné a platí pro všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="7276c-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="7276c-116">Můžete použít symboly, které jsou vytvořené pomocí této možnosti `#If`... `Then`... `#Else` direktiva k Podmíněná kompilace zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="7276c-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="7276c-117">`/d`je zkratka pro `/define`.</span><span class="sxs-lookup"><span data-stu-id="7276c-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="7276c-118">Můžete definovat více symbolů s `/define` oddělte čárkou oddělit definice symbolu.</span><span class="sxs-lookup"><span data-stu-id="7276c-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="7276c-119">Chcete-li nastavena / definovat v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7276c-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7276c-120">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7276c-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7276c-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7276c-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="7276c-122">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="7276c-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="7276c-123">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="7276c-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7276c-124">3.  Klikněte na tlačítko **rozšířené**.</span><span class="sxs-lookup"><span data-stu-id="7276c-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="7276c-125">4.  Změňte hodnotu v **vlastní konstanty** pole.</span><span class="sxs-lookup"><span data-stu-id="7276c-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7276c-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7276c-126">Example</span></span>  
 <span data-ttu-id="7276c-127">Následující kód definuje a pak používá dvě konstanty podmíněného kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7276c-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7276c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7276c-128">See Also</span></span>  
 [<span data-ttu-id="7276c-129">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7276c-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7276c-130">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="7276c-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="7276c-131">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="7276c-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="7276c-132">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7276c-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
