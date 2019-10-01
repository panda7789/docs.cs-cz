---
title: '#Const – direktiva (Visual Basic)'
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
ms.openlocfilehash: 9b8d2da2158a8244b4533eb6ef49049949417216
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696855"
---
# <a name="const-directive"></a><span data-ttu-id="ff7fc-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="ff7fc-102">#Const Directive</span></span>
<span data-ttu-id="ff7fc-103">Definuje podmíněné konstanty kompilátoru pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff7fc-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ff7fc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ff7fc-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="ff7fc-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-106">Required.</span></span> <span data-ttu-id="ff7fc-107">Název konstanty, která je definována.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="ff7fc-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-108">Required.</span></span> <span data-ttu-id="ff7fc-109">Literál, jiné podmíněné konstanty kompilátoru nebo libovolná kombinace, která obsahuje všechny nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff7fc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff7fc-110">Remarks</span></span>  
 <span data-ttu-id="ff7fc-111">Podmíněné konstanty kompilátoru jsou vždy soukromé k souboru, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="ff7fc-112">Nemůžete vytvořit konstanty veřejného kompilátoru pomocí direktivy `#Const`; můžete je vytvořit pouze v uživatelském rozhraní nebo pomocí možnosti kompilátoru `/define`.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="ff7fc-113">V `expression` lze použít pouze podmíněné konstanty a literály kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="ff7fc-114">Použití standardní konstanty definované s `Const` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="ff7fc-115">Naopak můžete použít konstanty definované s klíčovým slovem `#Const` pouze pro podmíněnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="ff7fc-116">Konstanty mohou být také nedefinovány. v takovém případě mají hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff7fc-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff7fc-117">Example</span></span>  
 <span data-ttu-id="ff7fc-118">V tomto příkladu se používá direktiva `#Const`.</span><span class="sxs-lookup"><span data-stu-id="ff7fc-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ff7fc-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff7fc-119">See also</span></span>

- [<span data-ttu-id="ff7fc-120">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff7fc-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="ff7fc-121">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="ff7fc-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="ff7fc-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="ff7fc-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="ff7fc-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="ff7fc-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="ff7fc-124">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="ff7fc-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
