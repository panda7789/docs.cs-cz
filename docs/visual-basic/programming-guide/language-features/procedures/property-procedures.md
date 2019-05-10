---
title: Procedury vlastnosti (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: b637f6a5f3ef367dfe769c2878878eeb938e3c81
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638806"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="26928-102">Procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26928-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="26928-103">Procedury vlastnosti je řadu příkazů jazyka Visual Basic, které pracují s vlastní vlastnost v modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="26928-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="26928-104">Procedury vlastnosti jsou známé také jako *přistupující objekty vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="26928-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="26928-105">Visual Basic poskytuje pokyny pro následující vlastnost:</span><span class="sxs-lookup"><span data-stu-id="26928-105">Visual Basic provides for the following property procedures:</span></span>  
  
- <span data-ttu-id="26928-106">A `Get` postup vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26928-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="26928-107">Je volána při přístupu k vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="26928-107">It is called when you access the property in an expression.</span></span>  
  
- <span data-ttu-id="26928-108">A `Set` postup nastaví vlastnost na hodnotu, včetně odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="26928-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="26928-109">Je volána při přiřazení hodnoty k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26928-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="26928-110">Obvykle definovat ve dvojicích, pomocí procedury vlastnosti `Get` a `Set` příkazy, ale můžete definovat těchto postupech samostatně, pokud je vlastnost jen pro čtení ([získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([nastavení Příkaz](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="26928-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="26928-111">Můžete vynechat `Get` a `Set` procedury při použití automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26928-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="26928-112">Další informace najdete v tématu [implemented Properties](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="26928-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="26928-113">Definujte vlastnosti do třídy, struktury a moduly.</span><span class="sxs-lookup"><span data-stu-id="26928-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="26928-114">Vlastnosti jsou `Public` ve výchozím nastavení, což znamená, že je můžete volat z libovolného místa v aplikaci s přístupem k vlastnosti kontejneru.</span><span class="sxs-lookup"><span data-stu-id="26928-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="26928-115">Porovnání vlastnostmi a proměnnými, naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="26928-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="26928-116">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="26928-116">Declaration Syntax</span></span>  
 <span data-ttu-id="26928-117">Samotné vlastnosti je definován bloku kódu uzavřený do složených závorek [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="26928-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="26928-118">V tomto bloku se každá procedura property zobrazí jako z vnitřního bloku uzavřeny v příkazu deklarace (`Get` nebo `Set`) a odpovídající `End` deklarace.</span><span class="sxs-lookup"><span data-stu-id="26928-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="26928-119">Syntaxe pro deklaraci vlastnosti a její postupy je následující:</span><span class="sxs-lookup"><span data-stu-id="26928-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="26928-120">`Modifiers` Můžete určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování, stejně jako Určuje, zda je vlastnost jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="26928-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="26928-121">`AccessLevel` Na `Get` nebo `Set` postupu může být libovolné úrovni, která je více omezující než úroveň přístupu, zadaná pro vlastnost samotný.</span><span class="sxs-lookup"><span data-stu-id="26928-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="26928-122">Další informace najdete v tématu [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26928-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="26928-123">Datový typ</span><span class="sxs-lookup"><span data-stu-id="26928-123">Data Type</span></span>  
 <span data-ttu-id="26928-124">Typ dat vlastnosti a úroveň přístupu objektu zabezpečení jsou definovány v `Property` příkaz není v procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="26928-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="26928-125">Vlastnost může mít pouze jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="26928-125">A property can have only one data type.</span></span> <span data-ttu-id="26928-126">Například nelze definovat vlastnost k ukládání `Decimal` hodnotu, ale načíst `Double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="26928-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="26928-127">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="26928-127">Access Level</span></span>  
 <span data-ttu-id="26928-128">Ale můžete definovat úroveň zabezpečení přístupu pro vlastnost a dál omezit úroveň přístupu v jednom z jeho procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="26928-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="26928-129">Například můžete definovat `Public` vlastnost a potom definovat, `Private Set` postup.</span><span class="sxs-lookup"><span data-stu-id="26928-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="26928-130">`Get` Postup zůstane `Public`.</span><span class="sxs-lookup"><span data-stu-id="26928-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="26928-131">Můžete změnit úroveň přístupu pouze v jednom z vlastnosti postupů a můžete pouze si je více omezující než úroveň přístupu instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="26928-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="26928-132">Další informace najdete v tématu [jak: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="26928-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="26928-133">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="26928-133">Parameter Declaration</span></span>  
 <span data-ttu-id="26928-134">Deklarujete každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md), s tím rozdílem, že musí být mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="26928-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="26928-135">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="26928-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="26928-136">Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="26928-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="26928-137">Syntaxe pro určení výchozí hodnota je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="26928-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="26928-138">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26928-138">Property Value</span></span>  
 <span data-ttu-id="26928-139">V `Get` procedury, vrácená hodnota je zadaný pro volání výrazu jako hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26928-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="26928-140">V `Set` postupu hodnota nové vlastnosti je předán jako parametr `Set` příkazu.</span><span class="sxs-lookup"><span data-stu-id="26928-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="26928-141">Pokud explicitně deklarujete parametr, musíte ji deklarovat s typem dat jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="26928-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="26928-142">Pokud parametr nedeklaruje, kompilátor používá implicitní parametr `Value` představující nová hodnota pro přiřazení k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26928-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="26928-143">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="26928-143">Calling Syntax</span></span>  
 <span data-ttu-id="26928-144">Vyvolání procedury vlastnosti implicitně tím, že odkaz na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="26928-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="26928-145">Můžete použít název vlastnosti stejným způsobem použijete název proměnné, s tím rozdílem, že je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="26928-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="26928-146">Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="26928-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="26928-147">Syntaxe pro implicitní volání `Set` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="26928-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="26928-148">Syntaxe pro implicitní volání `Get` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="26928-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="26928-149">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="26928-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="26928-150">Následující vlastnosti se ukládají úplný název jako dva základní názvy, křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="26928-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="26928-151">Když volající kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název.</span><span class="sxs-lookup"><span data-stu-id="26928-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="26928-152">Pokud volající kód přiřadí nový úplný název, `Set` postup pokusy o jeho rozdělení na dva základní názvy.</span><span class="sxs-lookup"><span data-stu-id="26928-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="26928-153">Pokud nelze najít mezeru, uloží jej jako křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="26928-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="26928-154">Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`.</span><span class="sxs-lookup"><span data-stu-id="26928-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="26928-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26928-155">See also</span></span>

- [<span data-ttu-id="26928-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="26928-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="26928-157">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="26928-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="26928-158">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="26928-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="26928-159">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="26928-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="26928-160">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26928-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="26928-161">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26928-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="26928-162">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26928-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="26928-163">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26928-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="26928-164">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26928-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="26928-165">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26928-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
