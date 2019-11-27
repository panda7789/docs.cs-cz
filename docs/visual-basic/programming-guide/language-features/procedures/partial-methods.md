---
title: Částečné metody
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352626"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="177f5-102">Částečné metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="177f5-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="177f5-103">Částečné metody umožňují vývojářům vkládat vlastní logiku do kódu.</span><span class="sxs-lookup"><span data-stu-id="177f5-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="177f5-104">Kód je obvykle součástí třídy generované návrhářem.</span><span class="sxs-lookup"><span data-stu-id="177f5-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="177f5-105">Částečné metody jsou definovány v částečné třídě, která je vytvořena generátorem kódu, a obvykle slouží k poskytnutí oznámení o tom, že došlo ke změně nějakého typu.</span><span class="sxs-lookup"><span data-stu-id="177f5-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="177f5-106">Umožňují vývojářům zadat vlastní chování v reakci na změnu.</span><span class="sxs-lookup"><span data-stu-id="177f5-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="177f5-107">Návrhář generátoru kódu definuje pouze signaturu metody a jedno nebo více volání metody.</span><span class="sxs-lookup"><span data-stu-id="177f5-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="177f5-108">Vývojáři pak mohou poskytnout implementace pro metodu, pokud chtějí přizpůsobit chování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="177f5-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="177f5-109">Není-li k dispozici žádná implementace, volání metody jsou odebrána kompilátorem, což má za následek žádné další nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="177f5-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="177f5-110">Deklarace</span><span class="sxs-lookup"><span data-stu-id="177f5-110">Declaration</span></span>  
 <span data-ttu-id="177f5-111">Vygenerovaný kód označuje definici částečné metody umístěním klíčového slova `Partial` na začátku řádku podpisu.</span><span class="sxs-lookup"><span data-stu-id="177f5-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="177f5-112">Definice musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="177f5-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="177f5-113">Metoda musí být `Sub`, nikoli `Function`.</span><span class="sxs-lookup"><span data-stu-id="177f5-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="177f5-114">Tělo metody musí být ponecháno prázdné.</span><span class="sxs-lookup"><span data-stu-id="177f5-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="177f5-115">Modifikátor přístupu musí být `Private`.</span><span class="sxs-lookup"><span data-stu-id="177f5-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="177f5-116">Implementace</span><span class="sxs-lookup"><span data-stu-id="177f5-116">Implementation</span></span>  
 <span data-ttu-id="177f5-117">Implementace se skládá hlavně z vyplnění těla částečné metody.</span><span class="sxs-lookup"><span data-stu-id="177f5-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="177f5-118">Implementace je obvykle v samostatné částečné třídě z definice a je zapsána vývojářem, který chce zvětšit generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="177f5-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="177f5-119">Předchozí příklad duplikuje signaturu v deklaraci přesně, ale je možné variace.</span><span class="sxs-lookup"><span data-stu-id="177f5-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="177f5-120">Konkrétně lze přidat jiné modifikátory, například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="177f5-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="177f5-121">Je povolený jenom jeden modifikátor `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="177f5-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="177f5-122">Další informace o modifikátorech metod naleznete v tématu [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="177f5-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="177f5-123">Použití</span><span class="sxs-lookup"><span data-stu-id="177f5-123">Use</span></span>  
 <span data-ttu-id="177f5-124">Můžete zavolat částečnou metodu, protože byste volali jakoukoli jinou `Sub` proceduru.</span><span class="sxs-lookup"><span data-stu-id="177f5-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="177f5-125">Pokud byla metoda implementována, jsou vyhodnoceny argumenty a je provedeno tělo metody.</span><span class="sxs-lookup"><span data-stu-id="177f5-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="177f5-126">Nezapomeňte však, že implementace částečné metody je volitelná.</span><span class="sxs-lookup"><span data-stu-id="177f5-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="177f5-127">Pokud není metoda implementována, volání na ni nemá žádný účinek a výrazy předané metodě nejsou vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="177f5-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177f5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="177f5-128">Example</span></span>  
 <span data-ttu-id="177f5-129">V souboru s názvem Product. Designer. vb Definujte třídu `Product`, která má vlastnost `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="177f5-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="177f5-130">V souboru s názvem Product. vb Poskytněte implementaci pro `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="177f5-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="177f5-131">Nakonec v hlavní metodě projektu deklarujte instanci `Product` a zadejte počáteční hodnotu pro její vlastnost `Quantity`.</span><span class="sxs-lookup"><span data-stu-id="177f5-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="177f5-132">Zobrazí se okno se zprávou s touto zprávou:</span><span class="sxs-lookup"><span data-stu-id="177f5-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="177f5-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="177f5-133">See also</span></span>

- [<span data-ttu-id="177f5-134">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="177f5-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="177f5-135">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="177f5-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="177f5-136">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="177f5-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="177f5-137">Partial</span><span class="sxs-lookup"><span data-stu-id="177f5-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="177f5-138">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="177f5-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="177f5-139">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="177f5-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
