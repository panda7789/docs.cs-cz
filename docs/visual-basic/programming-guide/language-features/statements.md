---
title: Příkazy
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401976"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="e9477-102">Příkazy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9477-102">Statements in Visual Basic</span></span>

<span data-ttu-id="e9477-103">Příkaz v Visual Basic je ucelenou instrukcí.</span><span class="sxs-lookup"><span data-stu-id="e9477-103">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="e9477-104">Může obsahovat klíčová slova, operátory, proměnné, konstanty a výrazy.</span><span class="sxs-lookup"><span data-stu-id="e9477-104">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="e9477-105">Každý příkaz patří do jedné z následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="e9477-105">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="e9477-106">**Příkazy deklarace**, které pojmenují proměnnou, konstantu nebo proceduru a mohou také určovat datový typ.</span><span class="sxs-lookup"><span data-stu-id="e9477-106">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="e9477-107">**Spustitelné příkazy**, které iniciují akce.</span><span class="sxs-lookup"><span data-stu-id="e9477-107">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="e9477-108">Tyto příkazy mohou volat metodu nebo funkci a mohou cykly nebo větvení prostřednictvím bloků kódu.</span><span class="sxs-lookup"><span data-stu-id="e9477-108">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="e9477-109">Spustitelné příkazy zahrnují **příkazy přiřazení**, které přiřazují hodnotu nebo výraz proměnné nebo konstantě.</span><span class="sxs-lookup"><span data-stu-id="e9477-109">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="e9477-110">V tomto tématu jsou popsány jednotlivé kategorie.</span><span class="sxs-lookup"><span data-stu-id="e9477-110">This topic describes each category.</span></span> <span data-ttu-id="e9477-111">Toto téma také popisuje, jak zkombinovat více příkazů na jednom řádku a jak pokračovat v příkazu nad více řádky.</span><span class="sxs-lookup"><span data-stu-id="e9477-111">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="e9477-112">Příkazy deklarace</span><span class="sxs-lookup"><span data-stu-id="e9477-112">Declaration statements</span></span>

<span data-ttu-id="e9477-113">Příkazy deklarace můžete použít k pojmenování a definování procedur, proměnných, vlastností, polí a konstant.</span><span class="sxs-lookup"><span data-stu-id="e9477-113">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="e9477-114">Při deklaraci programovacího prvku můžete také definovat jeho datový typ, úroveň přístupu a rozsah.</span><span class="sxs-lookup"><span data-stu-id="e9477-114">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="e9477-115">Další informace naleznete v tématu [deklarované charakteristiky elementu](./declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-115">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="e9477-116">Následující příklad obsahuje tři deklarace.</span><span class="sxs-lookup"><span data-stu-id="e9477-116">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="e9477-117">První deklarace je `Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e9477-117">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="e9477-118">Spolu s odpovídajícím `End Sub` prohlášením deklaruje proceduru s názvem `applyFormat` .</span><span class="sxs-lookup"><span data-stu-id="e9477-118">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="e9477-119">Určuje také to `applyFormat` `Public` , což znamená, že může volat libovolný kód, který na něj může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="e9477-119">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="e9477-120">Druhá deklarace je `Const` příkaz, který deklaruje konstantu `limit` `Integer` a určuje datový typ a hodnotu 33.</span><span class="sxs-lookup"><span data-stu-id="e9477-120">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="e9477-121">Třetí deklarace je `Dim` příkaz, který deklaruje proměnnou `thisWidget` .</span><span class="sxs-lookup"><span data-stu-id="e9477-121">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="e9477-122">Datový typ je konkrétní objekt, konkrétně objekt vytvořený z `Widget` třídy.</span><span class="sxs-lookup"><span data-stu-id="e9477-122">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="e9477-123">Můžete deklarovat proměnnou, která bude mít jakýkoli základní datový typ nebo jakýkoli typ objektu, který je zveřejněn v aplikaci, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e9477-123">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="e9477-124">Počáteční hodnoty</span><span class="sxs-lookup"><span data-stu-id="e9477-124">Initial Values</span></span>

<span data-ttu-id="e9477-125">Při spuštění kódu obsahujícího příkaz deklarace Visual Basic vyhrazuje paměť potřebnou pro deklarovaný element.</span><span class="sxs-lookup"><span data-stu-id="e9477-125">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="e9477-126">Pokud element obsahuje hodnotu, Visual Basic ji inicializuje na výchozí hodnotu pro svůj datový typ.</span><span class="sxs-lookup"><span data-stu-id="e9477-126">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="e9477-127">Další informace naleznete v tématu "Behavior" v [příkazu Dim](../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-127">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="e9477-128">Můžete přiřadit počáteční hodnotu proměnné jako součást její deklarace, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-128">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="e9477-129">Pokud je proměnná objektovou proměnnou, můžete explicitně vytvořit instanci své třídy při jejím deklaraci pomocí klíčového slova [New operátor](../../language-reference/operators/new-operator.md) , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-129">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="e9477-130">Všimněte si, že počáteční hodnota, kterou zadáte v příkazu deklarace, není přiřazena proměnné, dokud spuštění nedosáhne příkazu deklarace.</span><span class="sxs-lookup"><span data-stu-id="e9477-130">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="e9477-131">Do této doby proměnná obsahuje výchozí hodnotu pro svůj datový typ.</span><span class="sxs-lookup"><span data-stu-id="e9477-131">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="e9477-132">Spustitelné příkazy</span><span class="sxs-lookup"><span data-stu-id="e9477-132">Executable statements</span></span>

<span data-ttu-id="e9477-133">Spustitelný příkaz provede akci.</span><span class="sxs-lookup"><span data-stu-id="e9477-133">An executable statement performs an action.</span></span> <span data-ttu-id="e9477-134">Může zavolat proceduru, větvení na jiné místo v kódu, projít několik příkazů nebo vyhodnotit výraz.</span><span class="sxs-lookup"><span data-stu-id="e9477-134">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="e9477-135">Příkaz přiřazení je zvláštní případ spustitelného příkazu.</span><span class="sxs-lookup"><span data-stu-id="e9477-135">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="e9477-136">Následující příklad používá `If...Then...Else` strukturu ovládacího prvku ke spouštění různých bloků kódu na základě hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9477-136">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="e9477-137">V rámci každého bloku kódu `For...Next` cyklus spouští zadaný počet opakování.</span><span class="sxs-lookup"><span data-stu-id="e9477-137">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="e9477-138">`If`Příkaz v předchozím příkladu kontroluje hodnotu parametru `clockwise` .</span><span class="sxs-lookup"><span data-stu-id="e9477-138">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="e9477-139">Pokud je hodnota `True` , volá `spinClockwise` metodu `aWidget` .</span><span class="sxs-lookup"><span data-stu-id="e9477-139">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="e9477-140">Pokud je hodnota `False` , volá `spinCounterClockwise` metodu `aWidget` .</span><span class="sxs-lookup"><span data-stu-id="e9477-140">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="e9477-141">`If...Then...Else`Struktura ovládacího prvku končí na `End If` .</span><span class="sxs-lookup"><span data-stu-id="e9477-141">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="e9477-142">`For...Next`Smyčka v rámci každého bloku volá odpovídající metodu tolikrát, kolikrát se rovná hodnotě `revolutions` parametru.</span><span class="sxs-lookup"><span data-stu-id="e9477-142">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="e9477-143">Příkazy přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9477-143">Assignment statements</span></span>

<span data-ttu-id="e9477-144">Příkazy přiřazení provádějí operace přiřazení, které se skládají z převzetí hodnoty na pravé straně operátoru přiřazení ( `=` ) a jejich uložení v elementu vlevo, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e9477-144">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="e9477-145">V předchozím příkladu příkaz přiřazení ukládá hodnotu literálu 42 v proměnné `v` .</span><span class="sxs-lookup"><span data-stu-id="e9477-145">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="e9477-146">Oprávněné programovací prvky</span><span class="sxs-lookup"><span data-stu-id="e9477-146">Eligible programming elements</span></span>

<span data-ttu-id="e9477-147">Programovací element na levé straně operátoru přiřazení musí být schopný přijmout a uložit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9477-147">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="e9477-148">To znamená, že musí být proměnná nebo vlastnost, která není [jen pro čtení](../../language-reference/modifiers/readonly.md), nebo musí být prvkem pole.</span><span class="sxs-lookup"><span data-stu-id="e9477-148">This means it must be a variable or property that is not [ReadOnly](../../language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="e9477-149">V kontextu příkazu přiřazení se takový prvek někdy označuje jako *l*-hodnota, například "hodnota" Left.</span><span class="sxs-lookup"><span data-stu-id="e9477-149">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="e9477-150">Hodnota na pravé straně operátoru přiřazení je vygenerována výrazem, který se může skládat z jakékoli kombinace literálů, konstant, proměnných, vlastností, prvků pole, jiných výrazů nebo volání funkcí.</span><span class="sxs-lookup"><span data-stu-id="e9477-150">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="e9477-151">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-151">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="e9477-152">Předchozí příklad přidá hodnotu drženou v proměnné `y` do hodnoty uložené v proměnné `z` a poté přidá hodnotu vrácenou voláním funkce `findResult` .</span><span class="sxs-lookup"><span data-stu-id="e9477-152">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="e9477-153">Celková hodnota tohoto výrazu je pak uložena v proměnné `x` .</span><span class="sxs-lookup"><span data-stu-id="e9477-153">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="e9477-154">Datové typy v příkazech přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9477-154">Data types in assignment statements</span></span>

<span data-ttu-id="e9477-155">Kromě číselných hodnot operátor přiřazení může také přiřadit `String` hodnoty, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-155">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="e9477-156">Můžete také přiřadit `Boolean` hodnoty pomocí `Boolean` literálu nebo `Boolean` výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-156">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="e9477-157">Podobně můžete přiřadit příslušné hodnoty programovým prvkům `Char` , `Date` nebo `Object` datovým typem.</span><span class="sxs-lookup"><span data-stu-id="e9477-157">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="e9477-158">Instanci objektu lze také přiřadit elementu, který je deklarován jako třída, ze které je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="e9477-158">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="e9477-159">Složené příkazy přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9477-159">Compound assignment statements</span></span>

<span data-ttu-id="e9477-160">*Složené příkazy přiřazení* nejprve provede operaci na výrazu před přiřazením k programovacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="e9477-160">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="e9477-161">Následující příklad ilustruje jeden z těchto operátorů, `+=` , který zvyšuje hodnotu proměnné na levé straně operátoru hodnotou výrazu na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="e9477-161">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="e9477-162">Předchozí příklad přidá 1 k hodnotě `n` a pak uloží tuto novou hodnotu do `n` .</span><span class="sxs-lookup"><span data-stu-id="e9477-162">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="e9477-163">Jedná se o zkrácený ekvivalent následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="e9477-163">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="e9477-164">Pomocí operátorů tohoto typu lze provádět různé operace složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9477-164">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="e9477-165">Seznam těchto operátorů a další informace o těchto operátorech naleznete v tématu [operátory přiřazení](../../language-reference/operators/assignment-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-165">For a list of these operators and more information about them, see [Assignment Operators](../../language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="e9477-166">Operátor přiřazení zřetězení ( `&=` ) je vhodný pro přidání řetězce na konec již existujících řetězců, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-166">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="e9477-167">Převody typů v příkazech přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9477-167">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="e9477-168">Hodnota, kterou přiřadíte proměnné, vlastnosti nebo prvku pole musí být datového typu, který je vhodný pro daný cílový element.</span><span class="sxs-lookup"><span data-stu-id="e9477-168">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="e9477-169">Obecně byste se měli pokusit vygenerovat hodnotu stejného datového typu jako cílový element.</span><span class="sxs-lookup"><span data-stu-id="e9477-169">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="e9477-170">Některé typy však lze v průběhu přiřazení převést na jiné typy.</span><span class="sxs-lookup"><span data-stu-id="e9477-170">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="e9477-171">Informace o převodu mezi datovými typy naleznete [v tématu převody typu v Visual Basic](./data-types/type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-171">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="e9477-172">V krátkém Visual Basic automaticky převede hodnotu daného typu na jiný typ, na který se rozšíří.</span><span class="sxs-lookup"><span data-stu-id="e9477-172">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="e9477-173">*Rozšiřující převod* je jeden v, který se vždy zdaří za běhu a neztratí žádná data.</span><span class="sxs-lookup"><span data-stu-id="e9477-173">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="e9477-174">Například Visual Basic převede `Integer` hodnotu na `Double` , pokud je to vhodné, protože se `Integer` rozšíří na `Double` .</span><span class="sxs-lookup"><span data-stu-id="e9477-174">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="e9477-175">Další informace najdete v tématu [rozšiřování a zúžení převodů](./data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-175">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="e9477-176">*Zúžení převodů* (těch, které nejsou rozšiřující) mají riziko selhání za běhu nebo ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="e9477-176">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="e9477-177">Můžete provést zužující převod explicitně pomocí funkce pro převod typu nebo můžete kompilátor nasměrovat tak, aby se všechny převody implicitně prováděly nastavením `Option Strict Off` .</span><span class="sxs-lookup"><span data-stu-id="e9477-177">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="e9477-178">Další informace naleznete v tématu [implicitní a explicitní převody](./data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-178">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="e9477-179">Vložení více příkazů na jeden řádek</span><span class="sxs-lookup"><span data-stu-id="e9477-179">Putting multiple statements on one line</span></span>

<span data-ttu-id="e9477-180">Na jednom řádku, který je oddělen znakem dvojtečky (), můžete mít více příkazů `:` .</span><span class="sxs-lookup"><span data-stu-id="e9477-180">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="e9477-181">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e9477-181">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="e9477-182">V některých případech je to možné, že tato forma syntaxe má těžko čitelný a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="e9477-182">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="e9477-183">Proto se doporučuje uchovávat jeden příkaz na řádek.</span><span class="sxs-lookup"><span data-stu-id="e9477-183">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="e9477-184">Pokračování příkazu nad více řádky</span><span class="sxs-lookup"><span data-stu-id="e9477-184">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="e9477-185">Příkaz se obvykle vejde na jeden řádek, ale pokud je příliš dlouhý, můžete pokračovat na další řádek pomocí sekvence pokračování řádku, která je tvořena mezerou následovanou znakem podtržítka ( `_` ) následovaným návratem na začátek řádku.</span><span class="sxs-lookup"><span data-stu-id="e9477-185">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="e9477-186">V následujícím příkladu se `MsgBox` spustitelný příkaz pokračuje přes dva řádky.</span><span class="sxs-lookup"><span data-stu-id="e9477-186">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="e9477-187">Implicitní pokračování řádku</span><span class="sxs-lookup"><span data-stu-id="e9477-187">Implicit line continuation</span></span>

<span data-ttu-id="e9477-188">V mnoha případech můžete pokračovat v příkazu na dalším po sobě jdoucích řádcích bez použití podtržítka ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-188">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="e9477-189">Následující elementy syntaxe implicitně pokračují v příkazu na dalším řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="e9477-189">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="e9477-190">Za čárkou ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-190">After a comma (`,`).</span></span> <span data-ttu-id="e9477-191">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-191">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="e9477-192">Po otevírací závorce ( `(` ) nebo před pravou závorku ( `)` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-192">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="e9477-193">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-193">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="e9477-194">Za levou složenou závorku ( `{` ) nebo před pravou složenou závorkou ( `}` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-194">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="e9477-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-195">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="e9477-196">Další informace naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md) nebo [inicializátory kolekce](./collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-196">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="e9477-197">Po otevření vloženého výrazu ( `<%=` ) nebo před ukončením vloženého výrazu ( `%>` ) v rámci literálu XML.</span><span class="sxs-lookup"><span data-stu-id="e9477-197">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="e9477-198">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-198">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="e9477-199">Další informace najdete v tématu [vložené výrazy v XML](./xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-199">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="e9477-200">Po operátoru zřetězení ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-200">After the concatenation operator (`&`).</span></span> <span data-ttu-id="e9477-201">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-201">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="e9477-202">Další informace najdete v tématu [operátory uvedené podle funkcí](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-202">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="e9477-203">Po operátoru přiřazení ( `=` , `&=` , `:=` , `+=` , `-=` , `*=` , `/=` , `\=` , `^=` , `<<=` , `>>=` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-203">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="e9477-204">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-204">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="e9477-205">Další informace najdete v tématu [operátory uvedené podle funkcí](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-205">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="e9477-206">Po binárních operátorech ( `+` , `-` , `/` , `*` , `Mod` , `<>` , `<` , `>` , `<=` , `>=` , `^` , `>>` , `<<` , `And` , `AndAlso` , `Or` , `OrElse` , `Like` , `Xor` ) v rámci výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9477-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="e9477-207">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-207">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="e9477-208">Další informace najdete v tématu [operátory uvedené podle funkcí](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-208">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="e9477-209">Za `Is` operátory a `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="e9477-209">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="e9477-210">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-210">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="e9477-211">Další informace najdete v tématu [operátory uvedené podle funkcí](../../language-reference/operators/operators-listed-by-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-211">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="e9477-212">Po znaku kvalifikátoru členu ( `.` ) a před názvem členu.</span><span class="sxs-lookup"><span data-stu-id="e9477-212">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="e9477-213">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-213">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="e9477-214">`_`Při použití `With` příkazu nebo zadání hodnot v inicializačním seznamu pro daný typ však musíte zahrnout znak pro pokračování řádku () za znakem kvalifikátoru členu.</span><span class="sxs-lookup"><span data-stu-id="e9477-214">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="e9477-215">Zvažte rozdělení řádku po operátoru přiřazení (například `=` ) při použití `With` příkazů nebo seznamů inicializace objektů.</span><span class="sxs-lookup"><span data-stu-id="e9477-215">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="e9477-216">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-216">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="e9477-217">Další informace najdete v tématu [s... Ukončete příkazy](../../language-reference/statements/with-end-with-statement.md) nebo [Inicializátory objektů: pojmenované a anonymní typy](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-217">For more information, see [With...End With Statement](../../language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="e9477-218">Po kvalifikátoru Vlastnosti osy XML ( `.` nebo `.@` nebo `...` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-218">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="e9477-219">Je však nutné zadat znak pro pokračování řádku ( `_` ) při zadání kvalifikátoru člena při použití `With` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="e9477-219">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="e9477-220">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-220">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="e9477-221">Další informace najdete v tématu [Vlastnosti osy XML](../../language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-221">For more information, see [XML Axis Properties](../../language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="e9477-222">Za znaménkem menší než (<) nebo před symbolem větším než ( `>` ) při určení atributu.</span><span class="sxs-lookup"><span data-stu-id="e9477-222">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="e9477-223">Také po zadání znaku většího než ( `>` ) při určení atributu.</span><span class="sxs-lookup"><span data-stu-id="e9477-223">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="e9477-224">`_`Při zadání atributů na úrovni sestavení nebo modulu je však nutné zahrnout znak pro pokračování řádku ().</span><span class="sxs-lookup"><span data-stu-id="e9477-224">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="e9477-225">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-225">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="e9477-226">Další informace najdete v tématu [Přehled atributů](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-226">For more information, see [Attributes overview](../concepts/attributes/index.md).</span></span>

- <span data-ttu-id="e9477-227">Před a po operátorech dotazů ( `Aggregate` , `Distinct` , `From` , `Group By` , `Group Join` , `Join` , `Let` , `Order By` , `Select` ,,, `Skip` `Skip While` `Take` , `Take While` , `Where` ,,, `In` `Into` `On` , `Ascending` , a `Descending` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-227">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="e9477-228">Mezi klíčovými slovy operátorů dotazu, které se skládají z více klíčových slov ( `Order By` , `Group Join` , `Take While` a), nelze rozdělit čáru `Skip While` .</span><span class="sxs-lookup"><span data-stu-id="e9477-228">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="e9477-229">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-229">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="e9477-230">Další informace najdete v tématu [dotazy](../../language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-230">For more information, see [Queries](../../language-reference/queries/index.md).</span></span>

- <span data-ttu-id="e9477-231">Za `In` klíčovým slovem v `For Each` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e9477-231">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="e9477-232">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-232">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="e9477-233">Další informace najdete v tématu [for each... Další příkaz](../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-233">For more information, see [For Each...Next Statement](../../language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="e9477-234">Za `From` klíčovým slovem v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="e9477-234">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="e9477-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9477-235">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="e9477-236">Další informace najdete v tématu [inicializátory kolekce](collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9477-236">For more information, see [Collection Initializers](collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="e9477-237">Přidávání komentářů</span><span class="sxs-lookup"><span data-stu-id="e9477-237">Adding comments</span></span>

<span data-ttu-id="e9477-238">Zdrojový kód není vždy samozřejmý ani programátorovi, který ho vytvořil.</span><span class="sxs-lookup"><span data-stu-id="e9477-238">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="e9477-239">Aby bylo možné dokumentovat v kódu, proto většina programátorů využívá vložené komentáře.</span><span class="sxs-lookup"><span data-stu-id="e9477-239">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="e9477-240">Komentáře v kódu mohou vysvětlit postup nebo konkrétní instrukci pro někoho, kdo nebo s ním pracují později.</span><span class="sxs-lookup"><span data-stu-id="e9477-240">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="e9477-241">Visual Basic ignoruje komentáře během kompilace a nemá vliv na zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e9477-241">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="e9477-242">Řádky komentářů začínají znakem apostrofu ( `'` ) nebo `REM` následovaným mezerou.</span><span class="sxs-lookup"><span data-stu-id="e9477-242">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="e9477-243">Lze je přidat kdekoli v kódu, s výjimkou v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="e9477-243">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="e9477-244">Chcete-li připojit komentář k příkazu, vložte apostrof nebo `REM` za příkaz následovaný komentářem.</span><span class="sxs-lookup"><span data-stu-id="e9477-244">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="e9477-245">Komentáře mohou také jít na vlastní samostatný řádek.</span><span class="sxs-lookup"><span data-stu-id="e9477-245">Comments can also go on their own separate line.</span></span> <span data-ttu-id="e9477-246">Následující příklad znázorňuje tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="e9477-246">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="e9477-247">Kontrola chyb kompilace</span><span class="sxs-lookup"><span data-stu-id="e9477-247">Checking compilation errors</span></span>

<span data-ttu-id="e9477-248">Pokud po zadání řádku kódu se řádek zobrazí s modrou vlnovkou (může se zobrazit i chybová zpráva), v příkazu se zobrazí chyba syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e9477-248">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="e9477-249">Je třeba zjistit, co je v příkazu chybné, a to tak, že v seznamu úkolů vyhledáte ukazatel myši nebo najedete myší na chybu a napíšete chybovou zprávu) a opravíte ji.</span><span class="sxs-lookup"><span data-stu-id="e9477-249">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="e9477-250">Dokud neopravíte všechny chyby syntaxe v kódu, program se nepodaří zkompilovat správně.</span><span class="sxs-lookup"><span data-stu-id="e9477-250">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e9477-251">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e9477-251">Related sections</span></span>

|<span data-ttu-id="e9477-252">Pojem</span><span class="sxs-lookup"><span data-stu-id="e9477-252">Term</span></span>|<span data-ttu-id="e9477-253">Definice</span><span class="sxs-lookup"><span data-stu-id="e9477-253">Definition</span></span>|
|---|---|
|[<span data-ttu-id="e9477-254">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="e9477-254">Assignment Operators</span></span>](../../language-reference/operators/assignment-operators.md)|<span data-ttu-id="e9477-255">Obsahuje odkazy na jazykové referenční stránky, které kryjí operátory přiřazení `=` , jako jsou, `*=` a `&=` .</span><span class="sxs-lookup"><span data-stu-id="e9477-255">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="e9477-256">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e9477-256">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="e9477-257">Ukazuje, jak kombinovat prvky s operátory, aby se zadávaly nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e9477-257">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="e9477-258">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="e9477-258">How to: Break and Combine Statements in Code</span></span>](../program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="e9477-259">Ukazuje, jak rozdělit jeden příkaz na více řádků a jak umístit více příkazů na stejný řádek.</span><span class="sxs-lookup"><span data-stu-id="e9477-259">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="e9477-260">Postupy: Vytváření popisků příkazů</span><span class="sxs-lookup"><span data-stu-id="e9477-260">How to: Label Statements</span></span>](../program-structure/how-to-label-statements.md)|<span data-ttu-id="e9477-261">Ukazuje, jak označit řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="e9477-261">Shows how to label a line of code.</span></span>|
