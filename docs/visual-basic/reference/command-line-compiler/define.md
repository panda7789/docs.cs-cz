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
ms.openlocfilehash: d0a483e7a3c9e9863db39e89d655cf172c1e8c81
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834306"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="dbfc5-102">-definovat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbfc5-102">-define (Visual Basic)</span></span>
<span data-ttu-id="dbfc5-103">Definuje podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbfc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbfc5-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dbfc5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dbfc5-105">Arguments</span></span>  
  
|<span data-ttu-id="dbfc5-106">Termín</span><span class="sxs-lookup"><span data-stu-id="dbfc5-106">Term</span></span>|<span data-ttu-id="dbfc5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="dbfc5-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="dbfc5-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-108">Required.</span></span> <span data-ttu-id="dbfc5-109">Symbol definovat.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="dbfc5-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-110">Optional.</span></span> <span data-ttu-id="dbfc5-111">Hodnota pro přiřazení `symbol`.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-111">The value to assign `symbol`.</span></span> <span data-ttu-id="dbfc5-112">Pokud `value` je řetězec, musí být uzavřen v pořadí zpětné lomítko a znak uvozovek (\\") místo uvozovek.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="dbfc5-113">Pokud není zadána žádná hodnota, pak je provedena na hodnotu True.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbfc5-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbfc5-114">Remarks</span></span>  
 <span data-ttu-id="dbfc5-115">`-define` Možnost má efekt se používá podobně jako `#Const` direktivy preprocesoru ve zdrojovém souboru, s výjimkou této konstanty definované pomocí `-define` jsou veřejné a použít na všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="dbfc5-116">Symboly, které jsou vytvořené pomocí této možnosti se můžete `#If`... `Then`... `#Else` direktivy podmíněné kompilace zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="dbfc5-117">`-d` je zkratka pro `-define`.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="dbfc5-118">Můžete definovat více symbolů se `-define` s použitím čárky k oddělení definice symbolů.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="dbfc5-119">Chcete-li nastavit / define v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbfc5-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="dbfc5-120">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dbfc5-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="dbfc5-122">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dbfc5-123">3.  Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="dbfc5-124">4.  Upravte hodnotu v **konstanty vlastní** pole.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dbfc5-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbfc5-125">Example</span></span>  
 <span data-ttu-id="dbfc5-126">Následující kód definuje a pak používá dva podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="dbfc5-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="dbfc5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbfc5-127">See also</span></span>

- [<span data-ttu-id="dbfc5-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="dbfc5-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dbfc5-129">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="dbfc5-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="dbfc5-130">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="dbfc5-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="dbfc5-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="dbfc5-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
