---
title: '#If... Then... #Else – direktivy (Visual Basic)'
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
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823386"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="e23a7-102">#If...Then...#Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="e23a7-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="e23a7-103">Podmíněně zkompiluje vybrané bloky kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e23a7-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e23a7-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="e23a7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e23a7-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="e23a7-106">Vyžaduje se pro `#If` a `#ElseIf` příkazy, volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="e23a7-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="e23a7-107">Libovolný výraz, který se skládá pouze z jedné nebo více podmíněné konstanty kompilátoru, literály a operátory, které vyhodnotí jako `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="e23a7-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="e23a7-108">Vyžaduje se pro `#If` příkaz blokovat, volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="e23a7-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="e23a7-109">Řádky programu jazyka Visual Basic nebo direktivy kompilátoru, které jsou kompilovány, pokud přidružený výraz je vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="e23a7-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="e23a7-110">Ukončuje `#If` blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="e23a7-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e23a7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e23a7-111">Remarks</span></span>  
 <span data-ttu-id="e23a7-112">Na ploše, chování `#If...Then...#Else` direktivy vypadá stejně jako u `If...Then...Else` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e23a7-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="e23a7-113">Ale `#If...Then...#Else` direktivy vyhodnotit, co je kompilovány pomocí kompilátoru, že `If...Then...Else` příkazy vyhodnotí podmínky za běhu.</span><span class="sxs-lookup"><span data-stu-id="e23a7-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="e23a7-114">Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="e23a7-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="e23a7-115">Používá se také aby se zabránilo ladění kódu povolí, spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e23a7-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="e23a7-116">Kód při podmíněné kompilace je zcela vynecháno z konečný spustitelný soubor, takže nemá žádný vliv na výkon nebo velikost.</span><span class="sxs-lookup"><span data-stu-id="e23a7-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="e23a7-117">Bez ohledu na výsledek jakékoli hodnocení, všechny výrazy jsou vyhodnocovány pomocí `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="e23a7-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="e23a7-118">`Option Compare` Příkazu nemá vliv na výrazy v `#If` a `#ElseIf` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e23a7-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e23a7-119">Žádné jedním řádkem formu `#If`, `#Else`, `#ElseIf`, a `#End If` direktivy existuje.</span><span class="sxs-lookup"><span data-stu-id="e23a7-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="e23a7-120">Žádný další kód se nemůže objevit na stejném řádku jako některý z direktivy.</span><span class="sxs-lookup"><span data-stu-id="e23a7-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="e23a7-121">Příkazy v rámci bloku podmíněné kompilace musí být úplná logické prohlášení.</span><span class="sxs-lookup"><span data-stu-id="e23a7-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="e23a7-122">Například nelze Podmíněná kompilace pouze atributy funkce, ale je možné deklarovat podmíněně funkce společně s jeho atributy:</span><span class="sxs-lookup"><span data-stu-id="e23a7-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="e23a7-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e23a7-123">Example</span></span>
 <span data-ttu-id="e23a7-124">V tomto příkladu `#If...Then...#Else` konstrukce k určení, jestli se má zkompilovat určité příkazy.</span><span class="sxs-lookup"><span data-stu-id="e23a7-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e23a7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e23a7-125">See also</span></span>

- [<span data-ttu-id="e23a7-126">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="e23a7-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="e23a7-127">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="e23a7-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="e23a7-128">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="e23a7-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
