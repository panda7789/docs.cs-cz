---
title: "#<a name=\"ifthenelse-directives\"></a>If... Then... #Else – direktivy"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="7a854-102">#If...Then...#Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="7a854-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="7a854-103">Podmíněná zkompiluje vybrané bloky kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a854-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a854-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="7a854-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7a854-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="7a854-106">Vyžaduje se pro `#If` a `#ElseIf` příkazy, volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="7a854-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="7a854-107">Jakýkoli výraz tvořené výhradně jeden nebo více podmíněného kompilátoru konstanty, literály a operátory, které se vyhodnocuje `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="7a854-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="7a854-108">Vyžaduje se pro `#If` příkaz blok volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="7a854-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="7a854-109">Řádky programu jazyka Visual Basic nebo direktivy kompilátoru, které jsou kompilovány, pokud je výsledkem přidružený výraz `True`.</span><span class="sxs-lookup"><span data-stu-id="7a854-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="7a854-110">Ukončí `#If` příkaz bloku.</span><span class="sxs-lookup"><span data-stu-id="7a854-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a854-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a854-111">Remarks</span></span>  
 <span data-ttu-id="7a854-112">Na ploše, chování `#If...Then...#Else` direktivy zobrazuje stejně jako u `If...Then...Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="7a854-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="7a854-113">Ale `#If...Then...#Else` direktivy vyhodnotit zkompilují kompilátoru, zatímco `If...Then...Else` příkazy vyhodnocení podmínky za běhu.</span><span class="sxs-lookup"><span data-stu-id="7a854-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="7a854-114">Podmíněná kompilace se obvykle používá ke kompilaci stejný program pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="7a854-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="7a854-115">Také se používá při prevenci ladění kódu ze storu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="7a854-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="7a854-116">Vyloučené během Podmíněná kompilace kódu je úplně vynechaný konečné spustitelný soubor, takže ho nemá žádný vliv na výkon nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="7a854-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="7a854-117">Bez ohledu na výsledek žádné vyhodnocení všechny výrazy vyhodnocují se pomocí `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="7a854-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="7a854-118">`Option Compare` Příkaz nemá vliv na výrazy v `#If` a `#ElseIf` příkazy.</span><span class="sxs-lookup"><span data-stu-id="7a854-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a854-119">Žádné jeden řádek formu `#If`, `#Else`, `#ElseIf`, a `#End If` direktivy existuje.</span><span class="sxs-lookup"><span data-stu-id="7a854-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="7a854-120">Žádný jiný kód, můžete zobrazit na stejném řádku jako kterákoli ze direktivy.</span><span class="sxs-lookup"><span data-stu-id="7a854-120">No other code can appear on the same line as any of the directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a854-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a854-121">Example</span></span>  
 <span data-ttu-id="7a854-122">Tento příklad používá `#If...Then...#Else` konstrukce k určení, zda se pro kompilaci určité příkazy.</span><span class="sxs-lookup"><span data-stu-id="7a854-122">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7a854-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a854-123">See Also</span></span>  
 [<span data-ttu-id="7a854-124">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="7a854-124">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="7a854-125">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="7a854-125">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="7a854-126">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="7a854-126">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
