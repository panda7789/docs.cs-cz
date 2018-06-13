---
title: '##Const – direktiva'
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
ms.openlocfilehash: a3b3318f6b44f7d1798e08195be5aeb920b61c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588064"
---
# <a name="const-directive"></a><span data-ttu-id="c5a8b-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="c5a8b-102">#Const Directive</span></span>
<span data-ttu-id="c5a8b-103">Definuje konstanty podmíněného kompilátoru jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5a8b-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c5a8b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c5a8b-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="c5a8b-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-106">Required.</span></span> <span data-ttu-id="c5a8b-107">Název konstanta definovaný.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="c5a8b-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-108">Required.</span></span> <span data-ttu-id="c5a8b-109">Literál, ostatní konstanta podmíněného kompilátoru nebo libovolnou kombinaci, která zahrnuje některé nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5a8b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5a8b-110">Remarks</span></span>  
 <span data-ttu-id="c5a8b-111">Konstanty podmíněného kompilátoru jsou vždy privátní do souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="c5a8b-112">Nelze vytvořit veřejný kompilátoru konstanty pomocí `#Const` direktivy; můžete vytvořit pouze v uživatelském rozhraní nebo pomocí `/define` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="c5a8b-113">Můžete použít pouze konstanty podmíněného kompilátoru a literály v `expression`.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="c5a8b-114">Pomocí standardní konstanta definovaný s `Const` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="c5a8b-115">Naopak můžete použít konstanty definovaný s `#Const` – klíčové slovo pouze pro Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="c5a8b-116">Konstanty můžete také být undefined, v takovém případě budou mít hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5a8b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5a8b-117">Example</span></span>  
 <span data-ttu-id="c5a8b-118">Tento příklad používá `#Const` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="c5a8b-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c5a8b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5a8b-119">See Also</span></span>  
 [<span data-ttu-id="c5a8b-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5a8b-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="c5a8b-121">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="c5a8b-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="c5a8b-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="c5a8b-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="c5a8b-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="c5a8b-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="c5a8b-124">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="c5a8b-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
