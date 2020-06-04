---
title: 'Postupy: Deklarace a volání výchozí vlastnosti'
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
ms.openlocfilehash: 4de5d94a94e764d1fc543ffae41b00a9bb729c94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388151"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="1fa9c-102">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fa9c-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="1fa9c-103">*Výchozí vlastnost* je vlastnost třídy nebo struktury, ke které má váš kód přístup bez zadání.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="1fa9c-104">Při volání názvů kódu třída nebo struktura, ale ne vlastnost, a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup k výchozí vlastnosti této třídy nebo struktury, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="1fa9c-105">Třída nebo struktura může mít nejvýše jednu výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="1fa9c-106">Můžete však přetížit výchozí vlastnost a mít více než jednu verzi.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="1fa9c-107">Další informace najdete v tématu [výchozí](../../../language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="1fa9c-107">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="1fa9c-108">Deklarace výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="1fa9c-109">Deklarujte vlastnost normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-109">Declare the property in the normal way.</span></span> <span data-ttu-id="1fa9c-110">Nezadávejte `Shared` `Private` klíčové slovo or.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="1fa9c-111">Zahrňte `Default` klíčové slovo v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="1fa9c-112">Zadejte alespoň jeden parametr pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="1fa9c-113">Nelze definovat výchozí vlastnost, která nepřijímá alespoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="1fa9c-114">Volání výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-114">To call a default property</span></span>  
  
1. <span data-ttu-id="1fa9c-115">Deklaruje proměnnou obsahujícího typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="1fa9c-116">Použijte název proměnné samotný ve výrazu, kde byste normálně zahrnuli název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="1fa9c-117">Použijte název proměnné se seznamem argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="1fa9c-118">Výchozí vlastnost musí mít alespoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="1fa9c-119">Chcete-li načíst výchozí hodnotu vlastnosti, použijte název proměnné se seznamem argumentů ve výrazu nebo za `=` znaménkem EQUAL () v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="1fa9c-120">Chcete-li nastavit výchozí hodnotu vlastnosti, použijte název proměnné s seznamem argumentů na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="1fa9c-121">Název výchozí vlastnosti můžete vždy zadat společně s názvem proměnné, stejně jako při přístupu k libovolné jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="1fa9c-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fa9c-122">Example</span></span>  
 <span data-ttu-id="1fa9c-123">Následující příklad deklaruje výchozí vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="1fa9c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fa9c-124">Example</span></span>  
 <span data-ttu-id="1fa9c-125">Následující příklad ukazuje, jak volat výchozí vlastnost `myProperty` třídy `class1` .</span><span class="sxs-lookup"><span data-stu-id="1fa9c-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="1fa9c-126">Tři příkazy přiřazení ukládají hodnoty do `myProperty` a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání přečte hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="1fa9c-127">Nejběžnějším použitím výchozí vlastnosti je <xref:Microsoft.VisualBasic.Collection.Item%2A> vlastnost u různých tříd kolekcí.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1fa9c-128">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1fa9c-128">Robust Programming</span></span>  
 <span data-ttu-id="1fa9c-129">Výchozí vlastnosti můžou mít za následek malé snížení počtu znaků zdrojového kódu, ale můžou ztížit čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="1fa9c-130">Pokud volající kód není obeznámen s vaší třídou nebo strukturou, při odkazování na název třídy nebo struktury nemůže být jisté, zda tento odkaz přistupuje k třídě nebo struktuře samotné nebo výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="1fa9c-131">To může vést k chybám kompilátoru nebo k drobným chybám logiky run-time.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="1fa9c-132">Můžete trochu snížit pravděpodobnost chyb výchozích vlastností – vždy pomocí [příkazu Option Strict](../../../language-reference/statements/option-strict-statement.md) nastavit kontrolu typu kompilátoru na `On` .</span><span class="sxs-lookup"><span data-stu-id="1fa9c-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="1fa9c-133">Pokud plánujete použít předdefinovanou třídu nebo strukturu v kódu, je nutné určit, zda má výchozí vlastnost, a pokud ano, jaký je její název.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="1fa9c-134">Z důvodu těchto nevýhody byste měli zvážit, že nedefinujete výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="1fa9c-135">V případě čitelnosti kódu byste měli také zvážit možnost vždy odkazovat na všechny vlastnosti, a to i na výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa9c-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa9c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fa9c-136">See also</span></span>

- [<span data-ttu-id="1fa9c-137">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1fa9c-138">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="1fa9c-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1fa9c-139">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="1fa9c-139">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="1fa9c-140">Výchozí</span><span class="sxs-lookup"><span data-stu-id="1fa9c-140">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="1fa9c-141">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fa9c-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="1fa9c-142">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="1fa9c-143">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="1fa9c-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="1fa9c-144">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="1fa9c-145">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="1fa9c-146">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fa9c-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
