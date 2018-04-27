---
title: 'Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c4f471eba42e47d6bef45a4d38abc0cbd2d32bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="eec7d-102">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eec7d-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="eec7d-103">A *výchozí vlastnost* je vlastnost třídu nebo strukturu, která může kód přistupovat bez zadání ho.</span><span class="sxs-lookup"><span data-stu-id="eec7d-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="eec7d-104">Při volání metody kód názvy třídu nebo strukturu, ale není vlastnost a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup třídy nebo struktury je výchozí vlastnost, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="eec7d-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="eec7d-105">Třídu nebo strukturu může mít maximálně jeden výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eec7d-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="eec7d-106">Můžete však přetížení výchozí vlastnost a mít více než jednu verzi.</span><span class="sxs-lookup"><span data-stu-id="eec7d-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="eec7d-107">Další informace najdete v tématu [výchozí](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="eec7d-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="eec7d-108">Deklarace výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="eec7d-109">Deklarujte vlastnost běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="eec7d-109">Declare the property in the normal way.</span></span> <span data-ttu-id="eec7d-110">Nezadávejte `Shared` nebo `Private` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="eec7d-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="eec7d-111">Zahrnout `Default` – klíčové slovo v deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eec7d-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="eec7d-112">Zadejte jeden nebo více parametrů pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eec7d-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="eec7d-113">Nelze definovat výchozí vlastnost, která nevyužívá alespoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="eec7d-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="eec7d-114">K volání výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="eec7d-115">Deklarace proměnné obsahující třídu nebo strukturu typu.</span><span class="sxs-lookup"><span data-stu-id="eec7d-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="eec7d-116">Použijte název proměnné samostatně ve výrazu, kde bude obvykle zahrnovat název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eec7d-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="eec7d-117">Postupujte podle názvu proměnné s seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="eec7d-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="eec7d-118">Výchozí vlastnost vyžaduje alespoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="eec7d-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="eec7d-119">Načíst výchozí hodnotu vlastnosti, použijte název proměnné, s seznam argumentů, ve výrazu, nebo rovno (`=`) přihlásit příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="eec7d-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="eec7d-120">Pokud chcete nastavit výchozí hodnotu vlastnosti, použijte název proměnné, s seznam argumentů, na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="eec7d-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="eec7d-121">Vždy můžete výchozí název vlastnosti společně s názvem proměnné, stejně, jako byste to udělali pro přístup k libovolné jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eec7d-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="eec7d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="eec7d-122">Example</span></span>  
 <span data-ttu-id="eec7d-123">Následující příklad uvádí výchozí vlastnost třídy.</span><span class="sxs-lookup"><span data-stu-id="eec7d-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="eec7d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="eec7d-124">Example</span></span>  
 <span data-ttu-id="eec7d-125">Následující příklad ukazuje, jak volat výchozí vlastnost `myProperty` na třídě `class1`.</span><span class="sxs-lookup"><span data-stu-id="eec7d-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="eec7d-126">Příkazy tři přiřazení ukládání hodnot v `myProperty`a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání čte hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eec7d-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="eec7d-127">Se nejčastěji používá výchozí vlastnosti <xref:Microsoft.VisualBasic.Collection.Item%2A> vlastnost na různé třídy kolekce.</span><span class="sxs-lookup"><span data-stu-id="eec7d-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="eec7d-128">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eec7d-128">Robust Programming</span></span>  
 <span data-ttu-id="eec7d-129">Výchozí vlastnosti může vést ke snížení malé znaky zdrojový kód, ale jejich byl váš kód obtížněji čitelný.</span><span class="sxs-lookup"><span data-stu-id="eec7d-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="eec7d-130">Pokud volání kód není obeznámeni s třídě nebo struktuře, když má odkaz na název třídy nebo struktura nemůže být určité jestli přistupuje k tento odkaz, třídu nebo strukturu sám sebe nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eec7d-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="eec7d-131">To může vést k chybám kompilátoru nebo jemně běhu logické chyby.</span><span class="sxs-lookup"><span data-stu-id="eec7d-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="eec7d-132">Poněkud může snížit pravděpodobnost chyby výchozí vlastnost vždy pomocí [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavte typ kompilátoru kontrole `On`.</span><span class="sxs-lookup"><span data-stu-id="eec7d-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="eec7d-133">Pokud máte v úmyslu použít předdefinované třídu nebo strukturu ve vašem kódu, je třeba určit, jestli má výchozí vlastnost a pokud ano, jaké jeho název je.</span><span class="sxs-lookup"><span data-stu-id="eec7d-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="eec7d-134">Z důvodu tyto nevýhody měli byste zvážit není definování výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eec7d-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="eec7d-135">Kód čitelnější měli také zvážit vždy odkazující na všechny vlastnosti explicitně, i výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eec7d-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec7d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="eec7d-136">See Also</span></span>  
 [<span data-ttu-id="eec7d-137">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-137">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="eec7d-138">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="eec7d-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="eec7d-139">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="eec7d-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="eec7d-140">Default</span><span class="sxs-lookup"><span data-stu-id="eec7d-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)  
 [<span data-ttu-id="eec7d-141">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eec7d-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="eec7d-142">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="eec7d-143">Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu</span><span class="sxs-lookup"><span data-stu-id="eec7d-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="eec7d-144">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="eec7d-145">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="eec7d-146">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eec7d-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
