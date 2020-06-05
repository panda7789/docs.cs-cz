---
title: Procedury vlastnosti
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363730"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="c3fd3-102">Procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3fd3-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="c3fd3-103">Procedura vlastnosti je řada příkazů Visual Basic, které pracují s vlastní vlastností v modulu, třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="c3fd3-104">Procedury vlastnosti jsou také známé jako *přistupující objekty vlastností*.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="c3fd3-105">Visual Basic poskytuje následující procedury vlastností:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="c3fd3-106">`Get`Procedura vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="c3fd3-107">Je volána při přístupu k vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="c3fd3-108">`Set`Procedura nastaví vlastnost na hodnotu, včetně odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="c3fd3-109">Je volána, když přiřadíte hodnotu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="c3fd3-110">Procedury vlastností ve dvojicích obvykle definujete pomocí `Get` příkazů a `Set` , ale můžete definovat buď samostatně, pokud je vlastnost jen pro čtení ([příkaz Get](../../../language-reference/statements/get-statement.md)) nebo pouze pro zápis ([příkaz set](../../../language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="c3fd3-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="c3fd3-111">Můžete vynechat `Get` `Set` proceduru a při použití automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="c3fd3-112">Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c3fd3-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="c3fd3-113">Můžete definovat vlastnosti v třídách, strukturách a modulech.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="c3fd3-114">`Public`Ve výchozím nastavení jsou vlastnosti, což znamená, že je můžete volat odkudkoli v aplikaci, která má přístup k kontejneru vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="c3fd3-115">Porovnání vlastností a proměnných naleznete [v tématu rozdíly mezi vlastnostmi a proměnnými v Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="c3fd3-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="c3fd3-116">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="c3fd3-116">Declaration syntax</span></span>

<span data-ttu-id="c3fd3-117">Samotná vlastnost je definována blokem kódu uzavřeným v rámci [příkazu Property](../../../language-reference/statements/property-statement.md) a `End Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="c3fd3-118">V rámci tohoto bloku se každá procedura Vlastnosti zobrazuje jako vnitřní blok uzavřený v příkazu deklarace ( `Get` nebo `Set` ) a v rámci `End` deklarace v porovnání.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="c3fd3-119">Syntaxe pro deklaraci vlastnosti a její postupy je následující:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-119">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="c3fd3-120">`Modifiers`Může určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování a také zda je vlastnost jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="c3fd3-121">`AccessLevel`V `Get` `Set` proceduře nebo může být libovolná úroveň, která je více omezující než úroveň přístupu zadaná pro samotnou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="c3fd3-122">Další informace naleznete v tématu [příkaz Vlastnosti](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c3fd3-122">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="c3fd3-123">Typ dat</span><span class="sxs-lookup"><span data-stu-id="c3fd3-123">Data Type</span></span>

<span data-ttu-id="c3fd3-124">Datový typ vlastnosti a úroveň přístupu zabezpečení jsou definovány v `Property` příkazu, nikoli v procedurách vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="c3fd3-125">Vlastnost může mít pouze jeden datový typ.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-125">A property can have only one data type.</span></span> <span data-ttu-id="c3fd3-126">Například nelze definovat vlastnost pro uložení `Decimal` hodnoty, ale načtení `Double` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="c3fd3-127">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="c3fd3-127">Access Level</span></span>

<span data-ttu-id="c3fd3-128">Můžete však definovat hlavní úroveň přístupu pro vlastnost a dále omezit úroveň přístupu v jednom z jeho procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="c3fd3-129">Můžete například definovat `Public` vlastnost a pak definovat `Private Set` proceduru.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="c3fd3-130">`Get`Postup zůstane `Public` .</span><span class="sxs-lookup"><span data-stu-id="c3fd3-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="c3fd3-131">Úroveň přístupu můžete změnit jenom v jednom z procedur vlastnosti a můžete ji omezit jenom na úroveň přístupu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="c3fd3-132">Další informace najdete v tématu [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c3fd3-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="c3fd3-133">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="c3fd3-133">Parameter declaration</span></span>

<span data-ttu-id="c3fd3-134">Každý parametr deklarujete stejným způsobem jako u [procedur sub](sub-procedures.md), s tím rozdílem, že mechanismus předávání musí být `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="c3fd3-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="c3fd3-135">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="c3fd3-136">Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="c3fd3-137">Syntaxe pro určení výchozí hodnoty je následující:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="c3fd3-138">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3fd3-138">Property value</span></span>

<span data-ttu-id="c3fd3-139">V `Get` proceduře je vrácená hodnota dodána volajícímu výrazu jako hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="c3fd3-140">V `Set` proceduře je nová hodnota vlastnosti předána parametru `Set` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="c3fd3-141">Pokud explicitně deklarujete parametr, je nutné jej deklarovat se stejným datovým typem jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="c3fd3-142">Pokud parametr nedeklarujete, kompilátor použije implicitní parametr `Value` pro reprezentaci nové hodnoty, která má být přiřazena vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="c3fd3-143">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="c3fd3-143">Calling syntax</span></span>

<span data-ttu-id="c3fd3-144">Proceduru vlastnosti můžete implicitně vyvolat tak, že vytvoříte odkaz na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="c3fd3-145">Název vlastnosti použijete stejným způsobem jako název proměnné, s výjimkou toho, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c3fd3-146">Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="c3fd3-147">Syntaxe implicitního volání `Set` procedury je následující:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="c3fd3-148">Syntaxe implicitního volání `Get` procedury je následující:</span><span class="sxs-lookup"><span data-stu-id="c3fd3-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c3fd3-149">Ilustrace deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="c3fd3-149">Illustration of declaration and call</span></span>

<span data-ttu-id="c3fd3-150">Následující vlastnost uchovává úplný název jako dva názvy prvků, křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="c3fd3-151">Když volající kód přečte `fullName` , `Get` procedura Zkombinuje dva názvy prvků a vrátí úplný název.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="c3fd3-152">Když volající kód přiřadí nový úplný název, procedura se `Set` pokusí ho rozdělit do dvou názvů prvků.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="c3fd3-153">Pokud nenalezne žádné místo, uloží ho jako křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="c3fd3-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="c3fd3-154">Následující příklad ukazuje typická volání procedur vlastností `fullName` :</span><span class="sxs-lookup"><span data-stu-id="c3fd3-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="c3fd3-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3fd3-155">See also</span></span>

- [<span data-ttu-id="c3fd3-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="c3fd3-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="c3fd3-157">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="c3fd3-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="c3fd3-158">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="c3fd3-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="c3fd3-159">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="c3fd3-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c3fd3-160">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3fd3-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="c3fd3-161">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3fd3-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="c3fd3-162">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3fd3-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="c3fd3-163">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3fd3-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="c3fd3-164">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3fd3-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="c3fd3-165">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3fd3-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
