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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410007"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="1a71e-102">#If...Then...#Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="1a71e-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="1a71e-103">Podmíněně zkompiluje vybrané bloky kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1a71e-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a71e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a71e-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="1a71e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1a71e-105">Parts</span></span>

`expression`  
<span data-ttu-id="1a71e-106">Požadováno pro `#If` `#ElseIf` příkazy a, volitelně jinde.</span><span class="sxs-lookup"><span data-stu-id="1a71e-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="1a71e-107">Libovolný výraz, který obsahuje výhradně jednu nebo více podmíněné konstanty kompilátoru, literály a operátory, které jsou vyhodnoceny jako `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="1a71e-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="1a71e-108">Vyžadováno pro `#If` blok příkazu, volitelně jinde.</span><span class="sxs-lookup"><span data-stu-id="1a71e-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="1a71e-109">Visual Basic řádky programu nebo direktivy kompilátoru, které jsou kompilovány, pokud je přidružený výraz vyhodnocen jako `True` .</span><span class="sxs-lookup"><span data-stu-id="1a71e-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="1a71e-110">Ukončí `#If` blok příkazu.</span><span class="sxs-lookup"><span data-stu-id="1a71e-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a71e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a71e-111">Remarks</span></span>

<span data-ttu-id="1a71e-112">Na povrchu `#If...Then...#Else` se chování direktiv zobrazí stejně jako u `If...Then...Else` příkazů.</span><span class="sxs-lookup"><span data-stu-id="1a71e-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="1a71e-113">Nicméně `#If...Then...#Else` direktivy vyhodnotí, co je zkompilováno kompilátorem, zatímco `If...Then...Else` příkazy vyhodnotí podmínky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1a71e-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="1a71e-114">Podmíněná kompilace se obvykle používá ke kompilaci stejného programu pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="1a71e-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="1a71e-115">Slouží také k tomu, aby se zabránilo zobrazování kódu ladění ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="1a71e-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="1a71e-116">Kód vyloučený během podmíněné kompilace je zcela vynechán z finálního spustitelného souboru, takže nemá žádný vliv na velikost nebo výkon.</span><span class="sxs-lookup"><span data-stu-id="1a71e-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="1a71e-117">Bez ohledu na výsledek všech vyhodnocení jsou všechny výrazy vyhodnocovány pomocí `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="1a71e-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="1a71e-118">`Option Compare`Příkaz nemá vliv na výrazy v `#If` `#ElseIf` příkazech a.</span><span class="sxs-lookup"><span data-stu-id="1a71e-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="1a71e-119">Neexistuje žádný jednořádkový tvar `#If` `#Else` direktiv,, `#ElseIf` a `#End If` .</span><span class="sxs-lookup"><span data-stu-id="1a71e-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="1a71e-120">Žádný jiný kód se nemůže zobrazit na stejném řádku jako kterákoli ze direktiv.</span><span class="sxs-lookup"><span data-stu-id="1a71e-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="1a71e-121">Příkazy v bloku podmíněné kompilace musí být dokončeny pomocí logických příkazů.</span><span class="sxs-lookup"><span data-stu-id="1a71e-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="1a71e-122">Například nemůžete podmíněně kompilovat pouze atributy funkce, ale můžete podmíněně deklarovat funkci spolu s jejími atributy:</span><span class="sxs-lookup"><span data-stu-id="1a71e-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="1a71e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a71e-123">Example</span></span>

<span data-ttu-id="1a71e-124">V tomto příkladu je použita `#If...Then...#Else` konstrukce k určení, zda mají být zkompilovány určité příkazy.</span><span class="sxs-lookup"><span data-stu-id="1a71e-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1a71e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a71e-125">See also</span></span>

- [<span data-ttu-id="1a71e-126">#Const direktiva</span><span class="sxs-lookup"><span data-stu-id="1a71e-126">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="1a71e-127">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="1a71e-127">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="1a71e-128">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="1a71e-128">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
