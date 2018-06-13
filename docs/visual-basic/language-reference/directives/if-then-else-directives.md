---
title: '#If... Then... #Else – direktivy'
ms.date: 04/11/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591078"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="c1823-102">#If...Then...#Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="c1823-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="c1823-103">Podmíněná zkompiluje vybrané bloky kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1823-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1823-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1823-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="c1823-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c1823-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="c1823-106">Vyžaduje se pro `#If` a `#ElseIf` příkazy, volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="c1823-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="c1823-107">Jakýkoli výraz tvořené výhradně jeden nebo více podmíněného kompilátoru konstanty, literály a operátory, které se vyhodnocuje `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="c1823-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="c1823-108">Vyžaduje se pro `#If` příkaz blok volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="c1823-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="c1823-109">Řádky programu jazyka Visual Basic nebo direktivy kompilátoru, které jsou kompilovány, pokud je výsledkem přidružený výraz `True`.</span><span class="sxs-lookup"><span data-stu-id="c1823-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="c1823-110">Ukončí `#If` příkaz bloku.</span><span class="sxs-lookup"><span data-stu-id="c1823-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1823-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1823-111">Remarks</span></span>  
 <span data-ttu-id="c1823-112">Na ploše, chování `#If...Then...#Else` direktivy zobrazuje stejně jako u `If...Then...Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c1823-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="c1823-113">Ale `#If...Then...#Else` direktivy vyhodnotit zkompilují kompilátoru, zatímco `If...Then...Else` příkazy vyhodnocení podmínky za běhu.</span><span class="sxs-lookup"><span data-stu-id="c1823-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="c1823-114">Podmíněná kompilace se obvykle používá ke kompilaci stejný program pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="c1823-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="c1823-115">Také se používá při prevenci ladění kódu ze storu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="c1823-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="c1823-116">Vyloučené během Podmíněná kompilace kódu je úplně vynechaný konečné spustitelný soubor, takže ho nemá žádný vliv na výkon nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="c1823-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="c1823-117">Bez ohledu na výsledek žádné vyhodnocení všechny výrazy vyhodnocují se pomocí `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="c1823-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="c1823-118">`Option Compare` Příkaz nemá vliv na výrazy v `#If` a `#ElseIf` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c1823-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1823-119">Žádné jeden řádek formu `#If`, `#Else`, `#ElseIf`, a `#End If` direktivy existuje.</span><span class="sxs-lookup"><span data-stu-id="c1823-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="c1823-120">Žádný jiný kód, můžete zobrazit na stejném řádku jako kterákoli ze direktivy.</span><span class="sxs-lookup"><span data-stu-id="c1823-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="c1823-121">Příkazy v bloku Podmíněná kompilace musí být úplný logické příkazy.</span><span class="sxs-lookup"><span data-stu-id="c1823-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="c1823-122">Například nelze Podmíněná kompilace pouze atributy, funkce, ale můžou podmíněně deklarovat funkce společně s jeho atributy:</span><span class="sxs-lookup"><span data-stu-id="c1823-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="c1823-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1823-123">Example</span></span>
 <span data-ttu-id="c1823-124">Tento příklad používá `#If...Then...#Else` konstrukce k určení, zda se pro kompilaci určité příkazy.</span><span class="sxs-lookup"><span data-stu-id="c1823-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c1823-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1823-125">See Also</span></span>  
[<span data-ttu-id="c1823-126">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="c1823-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="c1823-127">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="c1823-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="c1823-128">[Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="c1823-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


