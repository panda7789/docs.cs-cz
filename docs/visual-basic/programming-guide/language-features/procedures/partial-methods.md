---
title: Částečné metody (Visual Basic)
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
ms.openlocfilehash: 50d7f24fd9f854d36bb2ed48c2e41a996c29dfe8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638888"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="eafad-102">Částečné metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eafad-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="eafad-103">Částečné metody umožňují vývojářům k vložení vlastní logiky do kódu.</span><span class="sxs-lookup"><span data-stu-id="eafad-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="eafad-104">Kód je obvykle součástí třídy generovaný návrhářem.</span><span class="sxs-lookup"><span data-stu-id="eafad-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="eafad-105">Částečné metody jsou definovány v dílčí třídě vytvořený generátor kódu a běžně se používají k poskytování oznámení, něco se změnila.</span><span class="sxs-lookup"><span data-stu-id="eafad-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="eafad-106">Umožňují vývojářům určit vlastní chování v reakci na změnu.</span><span class="sxs-lookup"><span data-stu-id="eafad-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="eafad-107">Návrhář generátoru kódu definuje podpis metody a jeden nebo více volání metody.</span><span class="sxs-lookup"><span data-stu-id="eafad-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="eafad-108">Vývojáři jim pak můžou implementace metody, pokud je to vyžadováno k přizpůsobení chování generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="eafad-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="eafad-109">Pokud je k dispozici žádná implementace, odeberou se volání metody kompilátorem, což vede k žádné dalším výkonnostním režiím.</span><span class="sxs-lookup"><span data-stu-id="eafad-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="eafad-110">Deklarace</span><span class="sxs-lookup"><span data-stu-id="eafad-110">Declaration</span></span>  
 <span data-ttu-id="eafad-111">Generovaný kód označí definicí částečné metody tak, že klíčové slovo `Partial` na začátku řádku podpisu.</span><span class="sxs-lookup"><span data-stu-id="eafad-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="eafad-112">Definice musí splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="eafad-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="eafad-113">Metoda musí být `Sub`, nikoli `Function`.</span><span class="sxs-lookup"><span data-stu-id="eafad-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="eafad-114">Tělo metody musí být prázdná.</span><span class="sxs-lookup"><span data-stu-id="eafad-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="eafad-115">Modifikátor přístupu musí být `Private`.</span><span class="sxs-lookup"><span data-stu-id="eafad-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="eafad-116">Implementace</span><span class="sxs-lookup"><span data-stu-id="eafad-116">Implementation</span></span>  
 <span data-ttu-id="eafad-117">Implementace sestává především z vyplnění textu částečné metody.</span><span class="sxs-lookup"><span data-stu-id="eafad-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="eafad-118">Implementace je obvykle v samostatné částečné třídy z definice a je vytvořená systémem pro vývojáře, kteří chtějí rozšířit generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="eafad-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="eafad-119">V předchozím příkladu přesně duplikuje podpisu v deklaraci, ale změny jsou možné.</span><span class="sxs-lookup"><span data-stu-id="eafad-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="eafad-120">Zejména jiných modifikátory lze přidat, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="eafad-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="eafad-121">Pouze jeden `Overrides` smí obsahovat modifikátor.</span><span class="sxs-lookup"><span data-stu-id="eafad-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="eafad-122">Další informace o modifikátory metodu, najdete v části [příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eafad-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="eafad-123">Použití</span><span class="sxs-lookup"><span data-stu-id="eafad-123">Use</span></span>  
 <span data-ttu-id="eafad-124">Částečná metoda zavoláte jako jakýkoli jiný zavolal `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="eafad-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="eafad-125">Pokud byl implementován metody, jsou vyhodnoceny argumenty a provede se tělo metody.</span><span class="sxs-lookup"><span data-stu-id="eafad-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="eafad-126">Nezapomeňte však, že implementace částečné metody je volitelné.</span><span class="sxs-lookup"><span data-stu-id="eafad-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="eafad-127">Pokud metoda není implementována, volání k němu nemá žádný vliv, a není u nich vyhodnoceno výrazy předané jako argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="eafad-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eafad-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="eafad-128">Example</span></span>  
 <span data-ttu-id="eafad-129">Do souboru s názvem Product.Designer.vb definovat `Product` třídu, která má `Quantity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eafad-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="eafad-130">Do souboru s názvem Product.vb poskytnout implementaci pro `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="eafad-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="eafad-131">Nakonec do metody Main projektu deklarovat `Product` instance a zadejte počáteční hodnotu pro jeho `Quantity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eafad-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="eafad-132">Okno se zprávou by měl vypadat, který se zobrazí tato zpráva:</span><span class="sxs-lookup"><span data-stu-id="eafad-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="eafad-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eafad-133">See also</span></span>

- [<span data-ttu-id="eafad-134">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="eafad-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="eafad-135">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="eafad-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="eafad-136">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="eafad-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="eafad-137">Partial</span><span class="sxs-lookup"><span data-stu-id="eafad-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="eafad-138">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="eafad-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="eafad-139">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="eafad-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
