---
title: Sub – procedury
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163810"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="2439d-102">Procedury Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2439d-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="2439d-103">Procedura `Sub` je série Visual Basic příkazů, které jsou uzavřeny příkazy `Sub` a `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="2439d-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="2439d-104">Procedura `Sub` provede úlohu a vrátí řízení volajícímu kódu, ale nevrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="2439d-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="2439d-105">Pokaždé, když je procedura volána, její příkazy jsou spouštěny, počínaje prvním spustitelným příkazem po příkazu `Sub` a končící prvním `End Sub`, `Exit Sub`nebo `Return`m příkazem.</span><span class="sxs-lookup"><span data-stu-id="2439d-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="2439d-106">Můžete definovat `Sub` proceduru v modulech, třídách a strukturách.</span><span class="sxs-lookup"><span data-stu-id="2439d-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="2439d-107">Ve výchozím nastavení je `Public`, což znamená, že ho můžete volat odkudkoli v aplikaci, která má přístup k modulu, třídě nebo struktuře, ve které jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="2439d-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="2439d-108">Pojem *Metoda* popisuje `Sub` nebo `Function` postup, který je k dispozici vně jeho definujícího modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2439d-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="2439d-109">Další informace najdete v tématu [postupy](./index.md).</span><span class="sxs-lookup"><span data-stu-id="2439d-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="2439d-110">`Sub` procedura může přebírat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou předány volajícím kódem.</span><span class="sxs-lookup"><span data-stu-id="2439d-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="2439d-111">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="2439d-111">Declaration syntax</span></span>

<span data-ttu-id="2439d-112">Syntaxe pro deklaraci `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="2439d-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="2439d-113">`modifiers` může určovat úroveň přístupu a informace o přetížení, přepsání, sdílení a stínování.</span><span class="sxs-lookup"><span data-stu-id="2439d-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="2439d-114">Další informace naleznete v tématu [Sub Statement](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2439d-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="2439d-115">Deklarace parametru</span><span class="sxs-lookup"><span data-stu-id="2439d-115">Parameter declaration</span></span>

<span data-ttu-id="2439d-116">Každý parametr procedury deklarujete podobně, jak deklarujete proměnnou, zadáním názvu parametru a datového typu.</span><span class="sxs-lookup"><span data-stu-id="2439d-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="2439d-117">Můžete také zadat mechanismus předávání a to, zda je parametr volitelný, nebo pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="2439d-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="2439d-118">Syntaxe pro každý parametr v seznamu parametrů je následující:</span><span class="sxs-lookup"><span data-stu-id="2439d-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="2439d-119">Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="2439d-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="2439d-120">Syntaxe pro určení výchozí hodnoty je následující:</span><span class="sxs-lookup"><span data-stu-id="2439d-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="2439d-121">Parametry jako lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="2439d-121">Parameters as local variables</span></span>

<span data-ttu-id="2439d-122">Při předání řízení proceduře je každý parametr považován za místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2439d-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="2439d-123">To znamená, že jeho životnost je stejná jako procedura a jeho rozsah je celý postup.</span><span class="sxs-lookup"><span data-stu-id="2439d-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="2439d-124">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="2439d-124">Calling syntax</span></span>

<span data-ttu-id="2439d-125">Vyvoláte `Sub` proceduru explicitně pomocí příkazu samostatného volání.</span><span class="sxs-lookup"><span data-stu-id="2439d-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="2439d-126">Nemůžete ji volat pomocí jejího názvu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2439d-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="2439d-127">Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="2439d-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="2439d-128">Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="2439d-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2439d-129">Použití klíčového slova `Call` je volitelné, ale nedoporučuje se.</span><span class="sxs-lookup"><span data-stu-id="2439d-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="2439d-130">Syntaxe pro volání `Sub` postup je následující:</span><span class="sxs-lookup"><span data-stu-id="2439d-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="2439d-131">Metodu `Sub` můžete volat vně třídy, která ji definuje.</span><span class="sxs-lookup"><span data-stu-id="2439d-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="2439d-132">Nejdříve je nutné použít klíčové slovo `New` pro vytvoření instance třídy nebo volání metody, která vrací instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="2439d-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="2439d-133">Další informace najdete v tématu [New operator](../../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2439d-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="2439d-134">Pak můžete použít následující syntaxi pro volání metody `Sub` objektu instance:</span><span class="sxs-lookup"><span data-stu-id="2439d-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="2439d-135">Ilustrace deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="2439d-135">Illustration of declaration and call</span></span>

<span data-ttu-id="2439d-136">Následující postup `Sub` informuje operátora počítače, který úkol aplikace provede, a také zobrazí časové razítko.</span><span class="sxs-lookup"><span data-stu-id="2439d-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="2439d-137">Namísto duplikování tohoto kódu na začátku každé úlohy aplikace volá pouze `tellOperator` z různých umístění.</span><span class="sxs-lookup"><span data-stu-id="2439d-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="2439d-138">Každé volání předá řetězec v argumentu `task`, který identifikuje spuštěnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="2439d-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="2439d-139">Následující příklad ukazuje typické volání `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="2439d-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="2439d-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2439d-140">See also</span></span>

- [<span data-ttu-id="2439d-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="2439d-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2439d-142">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="2439d-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="2439d-143">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2439d-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2439d-144">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="2439d-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2439d-145">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="2439d-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2439d-146">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="2439d-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2439d-147">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="2439d-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="2439d-148">Postupy: volání obslužné rutiny události v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2439d-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
