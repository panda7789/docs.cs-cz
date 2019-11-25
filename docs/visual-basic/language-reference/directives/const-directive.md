---
title: '#Const – direktiva'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 278219edb1bb5d1c0bb015611d69cbe4ae70014b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343848"
---
# <a name="const-directive"></a><span data-ttu-id="1a266-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="1a266-102">#Const Directive</span></span>

<span data-ttu-id="1a266-103">Defines conditional compiler constants for Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1a266-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a266-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a266-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="1a266-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1a266-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="1a266-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1a266-106">Required.</span></span> <span data-ttu-id="1a266-107">Name of the constant being defined.</span><span class="sxs-lookup"><span data-stu-id="1a266-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="1a266-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1a266-108">Required.</span></span> <span data-ttu-id="1a266-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span><span class="sxs-lookup"><span data-stu-id="1a266-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a266-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a266-110">Remarks</span></span>  

 <span data-ttu-id="1a266-111">Conditional compiler constants are always private to the file in which they appear.</span><span class="sxs-lookup"><span data-stu-id="1a266-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="1a266-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span><span class="sxs-lookup"><span data-stu-id="1a266-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="1a266-113">You can use only conditional compiler constants and literals in `expression`.</span><span class="sxs-lookup"><span data-stu-id="1a266-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="1a266-114">Using a standard constant defined with `Const` causes an error.</span><span class="sxs-lookup"><span data-stu-id="1a266-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="1a266-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span><span class="sxs-lookup"><span data-stu-id="1a266-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="1a266-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1a266-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a266-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a266-117">Example</span></span>  

 <span data-ttu-id="1a266-118">This example uses the `#Const` directive.</span><span class="sxs-lookup"><span data-stu-id="1a266-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1a266-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a266-119">See also</span></span>

- [<span data-ttu-id="1a266-120">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a266-120">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="1a266-121">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="1a266-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="1a266-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="1a266-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="1a266-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="1a266-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="1a266-124">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="1a266-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
