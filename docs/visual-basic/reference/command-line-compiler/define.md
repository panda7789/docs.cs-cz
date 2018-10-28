---
title: -definovat (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 4cab6bc968275bc12af4365fd3da5e3b5ff417f2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195174"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="89102-102">-definovat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89102-102">-define (Visual Basic)</span></span>
<span data-ttu-id="89102-103">Definuje podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="89102-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89102-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89102-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="89102-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="89102-105">Arguments</span></span>  
  
|<span data-ttu-id="89102-106">Termín</span><span class="sxs-lookup"><span data-stu-id="89102-106">Term</span></span>|<span data-ttu-id="89102-107">Definice</span><span class="sxs-lookup"><span data-stu-id="89102-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="89102-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="89102-108">Required.</span></span> <span data-ttu-id="89102-109">Symbol definovat.</span><span class="sxs-lookup"><span data-stu-id="89102-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="89102-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="89102-110">Optional.</span></span> <span data-ttu-id="89102-111">Hodnota pro přiřazení `symbol`.</span><span class="sxs-lookup"><span data-stu-id="89102-111">The value to assign `symbol`.</span></span> <span data-ttu-id="89102-112">Pokud `value` je řetězec, musí být uzavřen v pořadí zpětné lomítko a znak uvozovek (\\") místo uvozovek.</span><span class="sxs-lookup"><span data-stu-id="89102-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="89102-113">Pokud není zadána žádná hodnota, pak je provedena na hodnotu True.</span><span class="sxs-lookup"><span data-stu-id="89102-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89102-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89102-114">Remarks</span></span>  
 <span data-ttu-id="89102-115">`-define` Možnost má efekt se používá podobně jako `#Const` direktivy preprocesoru ve zdrojovém souboru, s výjimkou této konstanty definované pomocí `-define` jsou veřejné a použít na všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="89102-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="89102-116">Symboly, které jsou vytvořené pomocí této možnosti se můžete `#If`... `Then`... `#Else` direktivy podmíněné kompilace zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="89102-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="89102-117">`-d` je zkratka pro `-define`.</span><span class="sxs-lookup"><span data-stu-id="89102-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="89102-118">Můžete definovat více symbolů se `-define` s použitím čárky k oddělení definice symbolů.</span><span class="sxs-lookup"><span data-stu-id="89102-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="89102-119">Chcete-li nastavit / define v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89102-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="89102-120">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="89102-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="89102-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="89102-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="89102-122">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="89102-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="89102-123">3.  Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="89102-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="89102-124">4.  Upravte hodnotu v **konstanty vlastní** pole.</span><span class="sxs-lookup"><span data-stu-id="89102-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89102-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="89102-125">Example</span></span>  
 <span data-ttu-id="89102-126">Následující kód definuje a pak používá dva podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="89102-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="89102-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="89102-127">See Also</span></span>  
 [<span data-ttu-id="89102-128">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89102-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="89102-129">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="89102-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="89102-130">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="89102-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="89102-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="89102-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
