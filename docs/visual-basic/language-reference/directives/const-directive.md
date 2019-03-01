---
title: '##Const – direktiva (Visual Basic)'
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
ms.openlocfilehash: fb937a5a9d4688730085829350cb20172db50e97
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967045"
---
# <a name="const-directive"></a><span data-ttu-id="9eb1f-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="9eb1f-102">#Const Directive</span></span>
<span data-ttu-id="9eb1f-103">Definuje podmíněné konstanty kompilátoru v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eb1f-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9eb1f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9eb1f-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="9eb1f-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-106">Required.</span></span> <span data-ttu-id="9eb1f-107">Název je definována konstanta.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="9eb1f-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-108">Required.</span></span> <span data-ttu-id="9eb1f-109">Literál, jiné Konstanta podmíněné kompilátoru nebo libovolnou kombinaci, která zahrnuje některé nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eb1f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9eb1f-110">Remarks</span></span>  
 <span data-ttu-id="9eb1f-111">Podmíněné konstanty kompilátoru jsou vždycky soukromé vzhledem k souboru, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="9eb1f-112">Nelze vytvořit konstantu kompilátoru veřejné pomocí `#Const` direktiv; můžete je vytvořit pouze v uživatelském rozhraní nebo se `/define` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="9eb1f-113">Můžete použít jenom podmíněné konstanty kompilátoru a literály v `expression`.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="9eb1f-114">Pomocí standardní konstanta definovaná s `Const` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="9eb1f-115">Naopak, můžete použít konstanty definované pomocí `#Const` – klíčové slovo pouze pro podmíněnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="9eb1f-116">Konstanty lze také také definovat, v takovém případě mají hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb1f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="9eb1f-117">Example</span></span>  
 <span data-ttu-id="9eb1f-118">V tomto příkladu `#Const` směrnice.</span><span class="sxs-lookup"><span data-stu-id="9eb1f-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9eb1f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9eb1f-119">See also</span></span>
- [<span data-ttu-id="9eb1f-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9eb1f-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="9eb1f-121">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="9eb1f-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="9eb1f-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="9eb1f-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="9eb1f-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="9eb1f-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="9eb1f-124">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="9eb1f-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
