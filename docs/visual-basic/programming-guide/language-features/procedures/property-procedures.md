---
title: Procedury vlastnosti (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbdf49d5c3eb5ef71b25a060d62f55f19098f445
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="ecd5b-102">Procedury vlastnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecd5b-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="ecd5b-103">Procedury vlastnosti je řada [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] příkazy, které pracují s vlastní vlastnost na modul, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-103">A property procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="ecd5b-104">Procedury vlastností se také označují jako *přístupové objekty vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-104">Property procedures are also known as *property accessors*.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="ecd5b-105">poskytuje následující postupy vlastnost:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-105"> provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="ecd5b-106">A `Get` postup vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="ecd5b-107">Je volána při přístupu k vlastnosti ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="ecd5b-108">A `Set` postup nastaví vlastnost na hodnotu, včetně odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="ecd5b-109">Je volána při přiřazení hodnotu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="ecd5b-110">Obvykle definovat procedury vlastností v párech, a pomocí `Get` a `Set` příkazy, ale můžete definovat buď postup samostatně, pokud vlastnost je jen pro čtení ([získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([nastavit Příkaz](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="ecd5b-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="ecd5b-111">Můžete vynechat `Get` a `Set` procedury při použití ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="ecd5b-112">Další informace najdete v tématu [Auto-Implemented vlastnosti](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ecd5b-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="ecd5b-113">V tříd, struktur a moduly můžete definovat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="ecd5b-114">Vlastnosti jsou `Public` ve výchozím nastavení, což znamená, můžete je volat z libovolného místa v aplikaci, které můžete přístup k vlastnosti kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="ecd5b-115">Porovnání vlastností a proměnných najdete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ecd5b-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ecd5b-116">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="ecd5b-116">Declaration Syntax</span></span>  
 <span data-ttu-id="ecd5b-117">Samotné vlastnosti je definována blok kódu v rámci uzavřené [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="ecd5b-118">V tomto bloku každý procedury vlastnosti se zobrazí jako interní bloku uzavřené v rámci příkazu deklarace (`Get` nebo `Set`) a vyhledávání shody `End` deklarace.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="ecd5b-119">Syntaxe deklarace vlastnost a její postupy vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="ecd5b-120">`Modifiers` Můžete zadat úroveň přístupu a informací o přetížení, přepsání, sdílení a stínový provoz, stejně jako jestli vlastnost je jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="ecd5b-121">`AccessLevel` Na `Get` nebo `Set` postupu může být všechny úrovně, který je více omezující než úroveň přístupu, zadaná pro vlastnost sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="ecd5b-122">Další informace najdete v tématu [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ecd5b-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="ecd5b-123">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ecd5b-123">Data Type</span></span>  
 <span data-ttu-id="ecd5b-124">Datový typ vlastnost a úroveň hlavní přístupu jsou definovány v `Property` příkaz není v procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="ecd5b-125">Vlastnost může mít pouze jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-125">A property can have only one data type.</span></span> <span data-ttu-id="ecd5b-126">Například nelze definovat vlastnosti, které chcete uložit `Decimal` hodnotu, ale načíst `Double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="ecd5b-127">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="ecd5b-127">Access Level</span></span>  
 <span data-ttu-id="ecd5b-128">Můžete však definovat úroveň hlavní přístup pro vlastnost a dál omezit úroveň přístupu v jednom z jeho procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="ecd5b-129">Například můžete definovat `Public` vlastnost a potom zadejte `Private Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="ecd5b-130">`Get` Postup zůstane `Public`.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="ecd5b-131">Můžete změnit úroveň přístupu v pouze jeden z postupů vlastnost a pouze jej lze vytvořit více omezující než úroveň hlavní přístupu.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="ecd5b-132">Další informace najdete v tématu [postupy: deklarace vlastnosti se smíšené úrovně přístupu](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ecd5b-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="ecd5b-133">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="ecd5b-133">Parameter Declaration</span></span>  
 <span data-ttu-id="ecd5b-134">Deklarovat každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md)kromě toho, že musí být tento mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="ecd5b-135">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="ecd5b-136">Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu v rámci jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="ecd5b-137">Syntaxe pro určení výchozí hodnota je následující:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="ecd5b-138">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecd5b-138">Property Value</span></span>  
 <span data-ttu-id="ecd5b-139">V `Get` poskytnutý postupu návratovou hodnotu volání výrazu jako hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="ecd5b-140">V `Set` postup, nová hodnota vlastnosti je předaný parametr `Set` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="ecd5b-141">Pokud je výslovně deklarovat parametr, je třeba deklarovat s stejný datový typ jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="ecd5b-142">Pokud parametr nedeklarujte, kompilátor použije implicitní parametr `Value` představují nová hodnota pro přiřazení k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ecd5b-143">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="ecd5b-143">Calling Syntax</span></span>  
 <span data-ttu-id="ecd5b-144">Vyvolání procedury vlastnosti implicitně tím, že odkaz na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="ecd5b-145">Pomocí názvu vlastnosti stejným způsobem, jako byste použili název proměnné, s tím rozdílem, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="ecd5b-146">Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="ecd5b-147">Syntaxe pro implicitní volání `Set` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="ecd5b-148">Syntaxe pro implicitní volání `Get` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="ecd5b-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ecd5b-149">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="ecd5b-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ecd5b-150">Následující vlastnosti se ukládají jméno a příjmení jako dvě základní názvy, křestní jméno a příjmení.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="ecd5b-151">Při volání kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="ecd5b-152">Při volání kód přiřadí nový úplný název, `Set` postup pokusí rozdělit na dvě základní názvy.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="ecd5b-153">Pokud nenajde mezeru, uloží jej všechny jako křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="ecd5b-154">Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`.</span><span class="sxs-lookup"><span data-stu-id="ecd5b-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ecd5b-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecd5b-155">See Also</span></span>  
 [<span data-ttu-id="ecd5b-156">Postupy</span><span class="sxs-lookup"><span data-stu-id="ecd5b-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ecd5b-157">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="ecd5b-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="ecd5b-158">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ecd5b-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="ecd5b-159">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="ecd5b-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ecd5b-160">Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecd5b-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="ecd5b-161">Postupy: vytvoření vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecd5b-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="ecd5b-162">Postupy: volání procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecd5b-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="ecd5b-163">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecd5b-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="ecd5b-164">Postupy: vložení hodnoty do vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecd5b-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="ecd5b-165">Postupy: získání hodnoty z vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecd5b-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
