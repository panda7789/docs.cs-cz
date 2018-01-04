---
title: "Částečné metody (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33e34c63988e74be2c22cb7b1358f5e8b04048c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="db938-102">Částečné metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db938-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="db938-103">Částečné metody umožňují vývojářům vložení vlastní logiky do kódu.</span><span class="sxs-lookup"><span data-stu-id="db938-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="db938-104">Kód je obvykle součástí návrháře generované třídy.</span><span class="sxs-lookup"><span data-stu-id="db938-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="db938-105">Částečné metody jsou definovány v konkrétní třídu, který byl vytvořený generátor kódu a běžně se používají k poskytování oznámení, že něco došlo ke změnám.</span><span class="sxs-lookup"><span data-stu-id="db938-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="db938-106">Umožňují vývojáři určit vlastní chování v reakci na změny.</span><span class="sxs-lookup"><span data-stu-id="db938-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="db938-107">Návrhář generátoru kódu definuje pouze podpis metody a jeden nebo více volání metody.</span><span class="sxs-lookup"><span data-stu-id="db938-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="db938-108">Vývojáři jim pak můžou implementace pro metodu, aby bylo možné přizpůsobit chování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="db938-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="db938-109">Pokud je k dispozici žádné implementace, se odeberou volání do metody kompilátorem, což vede k žádné další zatížení.</span><span class="sxs-lookup"><span data-stu-id="db938-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="db938-110">Deklarace</span><span class="sxs-lookup"><span data-stu-id="db938-110">Declaration</span></span>  
 <span data-ttu-id="db938-111">Generovaný kód označí definici částečné metody tím, že umístíte klíčové slovo `Partial` na začátku řádku podpisu.</span><span class="sxs-lookup"><span data-stu-id="db938-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="db938-112">Definice musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="db938-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="db938-113">Metoda musí být `Sub`, nikoli `Function`.</span><span class="sxs-lookup"><span data-stu-id="db938-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="db938-114">Tělo metody musí být prázdné.</span><span class="sxs-lookup"><span data-stu-id="db938-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="db938-115">Modifikátor přístupu musí být `Private`.</span><span class="sxs-lookup"><span data-stu-id="db938-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="db938-116">Implementace</span><span class="sxs-lookup"><span data-stu-id="db938-116">Implementation</span></span>  
 <span data-ttu-id="db938-117">Implementace se primárně skládá z naplnění v těle částečné metody.</span><span class="sxs-lookup"><span data-stu-id="db938-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="db938-118">Implementace je obvykle v samostatné částečné třídy z definice a je zapsán vývojáři, kteří chtějí rozšířit generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="db938-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="db938-119">Předchozí příklad duplikuje podpis v deklaraci přesně, ale je možné, variace.</span><span class="sxs-lookup"><span data-stu-id="db938-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="db938-120">Konkrétně jiných modifikátory lze přidat, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="db938-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="db938-121">Pouze jeden `Overrides` Modifikátor je povoleno.</span><span class="sxs-lookup"><span data-stu-id="db938-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="db938-122">Další informace o metoda modifikátory najdete v tématu [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="db938-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="db938-123">Použití</span><span class="sxs-lookup"><span data-stu-id="db938-123">Use</span></span>  
 <span data-ttu-id="db938-124">Při volání metody částečné, jako by všechny další volání `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="db938-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="db938-125">Pokud byl implementován metodu, argumenty, které se vyhodnocují a je proveden těla metody.</span><span class="sxs-lookup"><span data-stu-id="db938-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="db938-126">Nezapomeňte však, že implementace částečné metoda je volitelné.</span><span class="sxs-lookup"><span data-stu-id="db938-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="db938-127">Pokud metoda není implementována, volání k ní nemá žádný vliv, a nejsou vyhodnotí výrazy předány jako argumenty metodě.</span><span class="sxs-lookup"><span data-stu-id="db938-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db938-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="db938-128">Example</span></span>  
 <span data-ttu-id="db938-129">V souboru s názvem Product.Designer.vb, definovat `Product` třídu, která má `Quantity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db938-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="db938-130">V souboru s názvem Product.vb, poskytovat implementaci `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="db938-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="db938-131">Nakonec v metodě hlavní projektu deklarovat `Product` instance a zadat počáteční hodnotu pro jeho `Quantity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db938-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="db938-132">Okno se zprávou by měla vypadat, zobrazí tato zpráva:</span><span class="sxs-lookup"><span data-stu-id="db938-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="db938-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="db938-133">See Also</span></span>  
 [<span data-ttu-id="db938-134">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="db938-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="db938-135">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="db938-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="db938-136">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="db938-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="db938-137">Partial</span><span class="sxs-lookup"><span data-stu-id="db938-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="db938-138">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="db938-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="db938-139">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="db938-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
