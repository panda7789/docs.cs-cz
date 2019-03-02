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
ms.openlocfilehash: c21223cc353b7a4614511aa97340c6bc5d61e70e
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200651"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="612fb-102">-definovat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="612fb-102">-define (Visual Basic)</span></span>
<span data-ttu-id="612fb-103">Definuje podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="612fb-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="612fb-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="612fb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="612fb-105">Arguments</span></span>  
  
|<span data-ttu-id="612fb-106">Termín</span><span class="sxs-lookup"><span data-stu-id="612fb-106">Term</span></span>|<span data-ttu-id="612fb-107">Definice</span><span class="sxs-lookup"><span data-stu-id="612fb-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="612fb-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="612fb-108">Required.</span></span> <span data-ttu-id="612fb-109">Symbol definovat.</span><span class="sxs-lookup"><span data-stu-id="612fb-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="612fb-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="612fb-110">Optional.</span></span> <span data-ttu-id="612fb-111">Hodnota pro přiřazení `symbol`.</span><span class="sxs-lookup"><span data-stu-id="612fb-111">The value to assign `symbol`.</span></span> <span data-ttu-id="612fb-112">Pokud `value` je řetězec, musí být uzavřen v pořadí zpětné lomítko a znak uvozovek (\\") místo uvozovek.</span><span class="sxs-lookup"><span data-stu-id="612fb-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="612fb-113">Pokud není zadána žádná hodnota, pak je provedena na hodnotu True.</span><span class="sxs-lookup"><span data-stu-id="612fb-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="612fb-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="612fb-114">Remarks</span></span>  
 <span data-ttu-id="612fb-115">`-define` Možnost má efekt se používá podobně jako `#Const` direktivy preprocesoru ve zdrojovém souboru, s výjimkou této konstanty definované pomocí `-define` jsou veřejné a použít na všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="612fb-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="612fb-116">Symboly, které jsou vytvořené pomocí této možnosti se můžete `#If`... `Then`... `#Else` direktivy podmíněné kompilace zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="612fb-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="612fb-117">`-d` je zkratka pro `-define`.</span><span class="sxs-lookup"><span data-stu-id="612fb-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="612fb-118">Můžete definovat více symbolů se `-define` s použitím čárky k oddělení definice symbolů.</span><span class="sxs-lookup"><span data-stu-id="612fb-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="612fb-119">Chcete-li nastavit / define v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="612fb-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="612fb-120">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="612fb-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="612fb-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="612fb-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="612fb-122">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="612fb-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="612fb-123">3.  Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="612fb-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="612fb-124">4.  Upravte hodnotu v **konstanty vlastní** pole.</span><span class="sxs-lookup"><span data-stu-id="612fb-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="612fb-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="612fb-125">Example</span></span>  
 <span data-ttu-id="612fb-126">Následující kód definuje a pak používá dva podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="612fb-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="612fb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="612fb-127">See also</span></span>
- [<span data-ttu-id="612fb-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="612fb-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="612fb-129">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="612fb-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="612fb-130">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="612fb-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="612fb-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="612fb-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
