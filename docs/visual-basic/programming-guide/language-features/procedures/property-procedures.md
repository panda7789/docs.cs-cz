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
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352566"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="937af-102">Procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="937af-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="937af-103">Procedura vlastnosti je řada příkazů Visual Basic, které pracují s vlastní vlastností v modulu, třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="937af-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="937af-104">Procedury vlastnosti jsou také známé jako *přistupující objekty vlastností*.</span><span class="sxs-lookup"><span data-stu-id="937af-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="937af-105">Visual Basic poskytuje následující procedury vlastností:</span><span class="sxs-lookup"><span data-stu-id="937af-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="937af-106">`Get` procedura vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="937af-107">Je volána při přístupu k vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="937af-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="937af-108">Procedura `Set` nastaví vlastnost na hodnotu, včetně odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="937af-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="937af-109">Je volána, když přiřadíte hodnotu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="937af-110">Procedury vlastností ve dvojicích obvykle definujete pomocí příkazů `Get` a `Set`, ale můžete definovat buď samostatně, pokud je vlastnost jen pro čtení ([příkaz Get](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([příkaz set](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="937af-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="937af-111">Můžete vynechat `Get` a `Set` postup při použití automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="937af-112">Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="937af-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="937af-113">Můžete definovat vlastnosti v třídách, strukturách a modulech.</span><span class="sxs-lookup"><span data-stu-id="937af-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="937af-114">Ve výchozím nastavení jsou vlastnosti `Public`, což znamená, že je můžete volat odkudkoli v aplikaci, která má přístup k kontejneru vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="937af-115">Porovnání vlastností a proměnných naleznete [v tématu rozdíly mezi vlastnostmi a proměnnými v Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="937af-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="937af-116">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="937af-116">Declaration syntax</span></span>

<span data-ttu-id="937af-117">Samotná vlastnost je definována blokem kódu uzavřeným v rámci [příkazu Property](../../../../visual-basic/language-reference/statements/property-statement.md) a příkazu `End Property`.</span><span class="sxs-lookup"><span data-stu-id="937af-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="937af-118">V rámci tohoto bloku se každá procedura Vlastnosti zobrazuje jako vnitřní blok uzavřený v rámci příkazu deklarace (`Get` nebo `Set`) a deklarace `End`.</span><span class="sxs-lookup"><span data-stu-id="937af-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="937af-119">Syntaxe pro deklaraci vlastnosti a její postupy je následující:</span><span class="sxs-lookup"><span data-stu-id="937af-119">The syntax for declaring a property and its procedures is as follows:</span></span>

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

<span data-ttu-id="937af-120">`Modifiers` může určovat úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování a také zda je vlastnost jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="937af-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="937af-121">`AccessLevel` v proceduře `Get` nebo `Set` může být libovolná úroveň, která je více omezující než úroveň přístupu zadaná pro samotnou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="937af-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="937af-122">Další informace naleznete v tématu [příkaz Vlastnosti](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="937af-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="937af-123">Typ dat</span><span class="sxs-lookup"><span data-stu-id="937af-123">Data Type</span></span>

<span data-ttu-id="937af-124">Datový typ vlastnosti a úroveň přístupu zabezpečení jsou definovány v příkazu `Property`, nikoli v procedurách vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="937af-125">Vlastnost může mít pouze jeden datový typ.</span><span class="sxs-lookup"><span data-stu-id="937af-125">A property can have only one data type.</span></span> <span data-ttu-id="937af-126">Například nelze definovat vlastnost pro uložení `Decimal` hodnoty, ale načtení `Double` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="937af-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="937af-127">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="937af-127">Access Level</span></span>

<span data-ttu-id="937af-128">Můžete však definovat hlavní úroveň přístupu pro vlastnost a dále omezit úroveň přístupu v jednom z jeho procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="937af-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="937af-129">Můžete například definovat vlastnost `Public` a potom definovat `Private Set` proceduru.</span><span class="sxs-lookup"><span data-stu-id="937af-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="937af-130">`Get` postup zůstane `Public`.</span><span class="sxs-lookup"><span data-stu-id="937af-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="937af-131">Úroveň přístupu můžete změnit jenom v jednom z procedur vlastnosti a můžete ji omezit jenom na úroveň přístupu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="937af-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="937af-132">Další informace najdete v tématu [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="937af-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="937af-133">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="937af-133">Parameter declaration</span></span>

<span data-ttu-id="937af-134">Každý parametr deklarujete stejným způsobem jako u [dílčích procedur](sub-procedures.md), s tím rozdílem, že mechanismus předávání musí být `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="937af-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="937af-135">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="937af-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="937af-136">Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="937af-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="937af-137">Syntaxe pro určení výchozí hodnoty je následující:</span><span class="sxs-lookup"><span data-stu-id="937af-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="937af-138">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="937af-138">Property value</span></span>

<span data-ttu-id="937af-139">V `Get` proceduře je návratovou hodnotou poskytnut výraz volání jako hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="937af-140">V `Set` proceduře je nová hodnota vlastnosti předána parametru příkazu `Set`.</span><span class="sxs-lookup"><span data-stu-id="937af-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="937af-141">Pokud explicitně deklarujete parametr, je nutné jej deklarovat se stejným datovým typem jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="937af-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="937af-142">Pokud parametr nedeklarujete, kompilátor použije implicitní parametr `Value` k reprezentaci nové hodnoty, která má být přiřazena vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="937af-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="937af-143">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="937af-143">Calling syntax</span></span>

<span data-ttu-id="937af-144">Proceduru vlastnosti můžete implicitně vyvolat tak, že vytvoříte odkaz na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="937af-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="937af-145">Název vlastnosti použijete stejným způsobem jako název proměnné, s výjimkou toho, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="937af-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="937af-146">Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="937af-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="937af-147">Syntaxe pro implicitní volání procedury `Set` je následující:</span><span class="sxs-lookup"><span data-stu-id="937af-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="937af-148">Syntaxe pro implicitní volání procedury `Get` je následující:</span><span class="sxs-lookup"><span data-stu-id="937af-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="937af-149">Ilustrace deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="937af-149">Illustration of declaration and call</span></span>

<span data-ttu-id="937af-150">Následující vlastnost uchovává úplný název jako dva názvy prvků, křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="937af-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="937af-151">Když volající kód přečte `fullName`, procedura `Get` kombinuje dva názvy prvků a vrátí úplný název.</span><span class="sxs-lookup"><span data-stu-id="937af-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="937af-152">Když volající kód přiřadí nový úplný název, `Set` postup se pokusí ho rozdělit do dvou názvů prvků.</span><span class="sxs-lookup"><span data-stu-id="937af-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="937af-153">Pokud nenalezne žádné místo, uloží ho jako křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="937af-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="937af-154">Následující příklad ukazuje typická volání procedur vlastností `fullName`:</span><span class="sxs-lookup"><span data-stu-id="937af-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="937af-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="937af-155">See also</span></span>

- [<span data-ttu-id="937af-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="937af-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="937af-157">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="937af-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="937af-158">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="937af-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="937af-159">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="937af-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="937af-160">Rozdíly mezi vlastnostmi a proměnnými v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="937af-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="937af-161">Postupy: Vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="937af-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="937af-162">Postupy: Volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="937af-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="937af-163">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="937af-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="937af-164">Postupy: Vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="937af-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="937af-165">Postupy: Získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="937af-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
