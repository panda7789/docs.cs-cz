---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: fd0875f09bf3ba7211ede500aa0da45f8b7cd2c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344766"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="94d0f-102">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94d0f-102">-define (Visual Basic)</span></span>
<span data-ttu-id="94d0f-103">Defines conditional compiler constants.</span><span class="sxs-lookup"><span data-stu-id="94d0f-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d0f-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="94d0f-105">or</span><span class="sxs-lookup"><span data-stu-id="94d0f-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="94d0f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="94d0f-106">Arguments</span></span>  
  
|<span data-ttu-id="94d0f-107">Termín</span><span class="sxs-lookup"><span data-stu-id="94d0f-107">Term</span></span>|<span data-ttu-id="94d0f-108">Definice</span><span class="sxs-lookup"><span data-stu-id="94d0f-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="94d0f-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="94d0f-109">Required.</span></span> <span data-ttu-id="94d0f-110">The symbol to define.</span><span class="sxs-lookup"><span data-stu-id="94d0f-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="94d0f-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="94d0f-111">Optional.</span></span> <span data-ttu-id="94d0f-112">The value to assign `symbol`.</span><span class="sxs-lookup"><span data-stu-id="94d0f-112">The value to assign `symbol`.</span></span> <span data-ttu-id="94d0f-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span><span class="sxs-lookup"><span data-stu-id="94d0f-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="94d0f-114">If no value is specified, then it is taken to be True.</span><span class="sxs-lookup"><span data-stu-id="94d0f-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94d0f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94d0f-115">Remarks</span></span>  
 <span data-ttu-id="94d0f-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span><span class="sxs-lookup"><span data-stu-id="94d0f-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="94d0f-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span><span class="sxs-lookup"><span data-stu-id="94d0f-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="94d0f-118">`-d` is the short form of `-define`.</span><span class="sxs-lookup"><span data-stu-id="94d0f-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="94d0f-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span><span class="sxs-lookup"><span data-stu-id="94d0f-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="94d0f-120">To set /define in the Visual Studio integrated development environment</span><span class="sxs-lookup"><span data-stu-id="94d0f-120">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="94d0f-121">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="94d0f-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="94d0f-122">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="94d0f-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="94d0f-123">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="94d0f-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="94d0f-124">3.  Click **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="94d0f-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="94d0f-125">4.  Modify the value in the **Custom Constants** box.</span><span class="sxs-lookup"><span data-stu-id="94d0f-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="94d0f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="94d0f-126">Example</span></span>  
 <span data-ttu-id="94d0f-127">The following code defines and then uses two conditional compiler constants.</span><span class="sxs-lookup"><span data-stu-id="94d0f-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="94d0f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94d0f-128">See also</span></span>

- [<span data-ttu-id="94d0f-129">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="94d0f-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="94d0f-130">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="94d0f-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="94d0f-131">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="94d0f-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="94d0f-132">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="94d0f-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
