---
title: '#If...Then...#Else – direktivy'
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
ms.openlocfilehash: 40e93b718241c9819e3c0fd84595e76eb0c86472
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343816"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="25d94-102">#If...Then...#Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="25d94-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="25d94-103">Podmíněně zkompiluje vybrané bloky kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="25d94-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="25d94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25d94-104">Syntax</span></span>

```vb
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

## <a name="parts"></a><span data-ttu-id="25d94-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="25d94-105">Parts</span></span>

`expression`  
<span data-ttu-id="25d94-106">Vyžaduje se pro příkazy `#If` a `#ElseIf`, které jsou volitelné jinde.</span><span class="sxs-lookup"><span data-stu-id="25d94-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="25d94-107">Libovolný výraz, který se skládá výhradně z jedné nebo více podmíněných konstant kompilátoru, literálů a operátorů, které jsou vyhodnoceny jako `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="25d94-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="25d94-108">Vyžadováno pro blok příkazu `#If`, volitelně jinde.</span><span class="sxs-lookup"><span data-stu-id="25d94-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="25d94-109">Visual Basic řádky programu nebo direktivy kompilátoru, které jsou kompilovány, pokud je přidružený výraz vyhodnocen jako `True`.</span><span class="sxs-lookup"><span data-stu-id="25d94-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="25d94-110">Ukončí blok příkazu `#If`.</span><span class="sxs-lookup"><span data-stu-id="25d94-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="25d94-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25d94-111">Remarks</span></span>

<span data-ttu-id="25d94-112">Na povrchu se chování direktiv `#If...Then...#Else` zobrazí stejně jako u příkazů `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="25d94-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="25d94-113">Direktivy `#If...Then...#Else` však vyhodnotí, co je zkompilováno kompilátorem, zatímco příkazy `If...Then...Else` vyhodnocují podmínky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="25d94-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="25d94-114">Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="25d94-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="25d94-115">Slouží také k tomu, aby se zabránilo zobrazování kódu ladění ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="25d94-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="25d94-116">Kód vyloučený během podmíněné kompilace je zcela vynechán z finálního spustitelného souboru, takže nemá žádný vliv na velikost nebo výkon.</span><span class="sxs-lookup"><span data-stu-id="25d94-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="25d94-117">Bez ohledu na výsledek žádného vyhodnocení jsou všechny výrazy vyhodnocovány pomocí `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="25d94-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="25d94-118">Příkaz `Option Compare` neovlivňuje výrazy v příkazech `#If` a `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="25d94-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="25d94-119">Neexistuje žádný jednořádkový tvar `#If`, `#Else`, `#ElseIf`a direktivy `#End If`.</span><span class="sxs-lookup"><span data-stu-id="25d94-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="25d94-120">Žádný jiný kód se nemůže zobrazit na stejném řádku jako kterákoli ze direktiv.</span><span class="sxs-lookup"><span data-stu-id="25d94-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="25d94-121">Příkazy v bloku podmíněné kompilace musí být dokončeny pomocí logických příkazů.</span><span class="sxs-lookup"><span data-stu-id="25d94-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="25d94-122">Například nemůžete podmíněně kompilovat pouze atributy funkce, ale můžete podmíněně deklarovat funkci spolu s jejími atributy:</span><span class="sxs-lookup"><span data-stu-id="25d94-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="25d94-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="25d94-123">Example</span></span>

<span data-ttu-id="25d94-124">V tomto příkladu se používá konstrukce `#If...Then...#Else` k určení, zda se mají kompilovat určité příkazy.</span><span class="sxs-lookup"><span data-stu-id="25d94-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="25d94-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25d94-125">See also</span></span>

- [<span data-ttu-id="25d94-126">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="25d94-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="25d94-127">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="25d94-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="25d94-128">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="25d94-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
