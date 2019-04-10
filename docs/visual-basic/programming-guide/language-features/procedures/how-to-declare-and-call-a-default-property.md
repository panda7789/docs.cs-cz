---
title: 'Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 9ca9a0ccdac3ac13429928233a0c09d58427ce74
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295637"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="2c5f2-102">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c5f2-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="2c5f2-103">A *výchozí vlastnost* je vlastnost třídy nebo struktury, který váš kód může přistupovat bez zadání ho.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="2c5f2-104">Při volání metody kódu názvy třídy nebo struktury, ale není vlastnost a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup k dané třídy nebo struktury výchozí vlastnost pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="2c5f2-105">Třídy nebo struktury může mít maximálně jeden výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="2c5f2-106">Můžete však přetížení výchozí vlastností a mají více než jednu verzi.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="2c5f2-107">Další informace najdete v tématu [výchozí](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="2c5f2-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="2c5f2-108">Chcete-li deklarovat výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2c5f2-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="2c5f2-109">Deklarujte vlastnost běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-109">Declare the property in the normal way.</span></span> <span data-ttu-id="2c5f2-110">Nezadávejte `Shared` nebo `Private` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="2c5f2-111">Zahrnout `Default` – klíčové slovo v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="2c5f2-112">Zadejte nejméně jeden parametr pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="2c5f2-113">Nelze definovat výchozí vlastnost, která nevyužívá aspoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="2c5f2-114">K volání výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2c5f2-114">To call a default property</span></span>  
  
1. <span data-ttu-id="2c5f2-115">Deklarujte proměnnou obsahující typ třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="2c5f2-116">Použijte název proměnné pouze ve výrazu, kde by obvykle zahrnují název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="2c5f2-117">Použijte název proměnné se seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="2c5f2-118">Výchozí vlastnost musí přebírat aspoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="2c5f2-119">Načíst výchozí hodnota vlastnosti, použijte název proměnné, se seznamem argumentů, ve výrazu nebo rovno (`=`) Přihlaste se příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="2c5f2-120">Pokud chcete nastavit výchozí hodnotu vlastnosti, použijte název proměnné, se seznamem argumentů, na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="2c5f2-121">Výchozí název vlastnosti spolu s názvem proměnné, můžete zadat vždy, stejně jako by tomu pro přístup k žádné jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="2c5f2-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c5f2-122">Example</span></span>  
 <span data-ttu-id="2c5f2-123">Následující příklad deklaruje výchozí vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="2c5f2-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c5f2-124">Example</span></span>  
 <span data-ttu-id="2c5f2-125">Následující příklad ukazuje způsob volání výchozí vlastnosti `myProperty` ve třídě `class1`.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="2c5f2-126">Tři přiřazovací příkazy ukládání hodnot v `myProperty`a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání načte hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="2c5f2-127">Se nejčastěji používá výchozí vlastnost <xref:Microsoft.VisualBasic.Collection.Item%2A> vlastnost na různé třídy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2c5f2-128">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2c5f2-128">Robust Programming</span></span>  
 <span data-ttu-id="2c5f2-129">Výchozí vlastnosti může vést k malé snížení zdrojového kódu – znaků, ale váš kód mohl provést obtížněji čitelný.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="2c5f2-130">Pokud volající kód není znáte třídy nebo struktury, když se vytváří odkaz na název třídy nebo struktury nemůže být určité Určuje, zda přistupuje k této referenční třídy nebo struktury samotné nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="2c5f2-131">To může vést k chybám kompilátoru nebo běhové logiky drobné chyby.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="2c5f2-132">Můžete poněkud snížit pravděpodobnost vzniku chyby výchozí vlastnost vždy používat [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavení kompilátoru kontroly typů pro `On`.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="2c5f2-133">Pokud máte v úmyslu použít předdefinované třídy nebo struktury v kódu, musíte určit, zda má výchozí vlastnosti a pokud ano, co její název je.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="2c5f2-134">Z důvodu tyto nevýhody měli byste zvážit, není definování výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="2c5f2-135">Pro lepší čitelnost kódu byste také vzít v úvahu vždy odkazuje na všechny vlastnosti explicitně, dokonce i výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2c5f2-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5f2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c5f2-136">See also</span></span>

- [<span data-ttu-id="2c5f2-137">Procedury Property</span><span class="sxs-lookup"><span data-stu-id="2c5f2-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2c5f2-138">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="2c5f2-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2c5f2-139">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2c5f2-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2c5f2-140">Výchozí</span><span class="sxs-lookup"><span data-stu-id="2c5f2-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="2c5f2-141">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c5f2-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="2c5f2-142">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2c5f2-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="2c5f2-143">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="2c5f2-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="2c5f2-144">Postupy: Volání procedury Property</span><span class="sxs-lookup"><span data-stu-id="2c5f2-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="2c5f2-145">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2c5f2-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="2c5f2-146">Postupy: Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2c5f2-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
