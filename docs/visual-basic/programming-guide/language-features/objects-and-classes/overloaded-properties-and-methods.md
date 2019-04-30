---
title: Přetížená vlastnosti a metody (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864868"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="506f9-102">Přetížená vlastnosti a metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="506f9-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="506f9-103">Přetěžování je vytvoření více procedur, konstruktor instance nebo vlastnost ve třídě se stejným názvem, ale typy různých argumentů.</span><span class="sxs-lookup"><span data-stu-id="506f9-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="506f9-104">Přetížení využití</span><span class="sxs-lookup"><span data-stu-id="506f9-104">Overloading usage</span></span>

<span data-ttu-id="506f9-105">Přetěžování je zvlášť užitečné, když objektový model Určuje, že nepoužijete stejný název pro postupy, které pracují s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="506f9-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="506f9-106">Například může mít třídu, která se může zobrazit několik různých datových typů `Display` postupy, které vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="506f9-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="506f9-107">Bez přetížení, je třeba vytvořit odlišné názvy pro každý postup i v případě, že to samé udělá, jak je ukázáno dále:</span><span class="sxs-lookup"><span data-stu-id="506f9-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="506f9-108">Přetížení je snazší vzhledem k tomu, že poskytuje možnost datové typy, které je možné použít vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="506f9-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="506f9-109">Například přetížené `Display` probírali dříve nelze volat metodu s jakoukoli následující řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="506f9-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="506f9-110">V době běhu jazyka Visual Basic volá správný postup založené na datové typy parametrů, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="506f9-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="506f9-111">Přetížení pravidla</span><span class="sxs-lookup"><span data-stu-id="506f9-111">Overloading rules</span></span>

 <span data-ttu-id="506f9-112">Vytvořit přetíženého členu třídy přidáním dvou nebo více vlastností nebo metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="506f9-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="506f9-113">S výjimkou přetěžované členy odvozené každý přetíženého členu musí mít seznam různých parametrů a tyto položky nelze použít jako odlišující funkce při přetížení se vlastnost nebo procedura:</span><span class="sxs-lookup"><span data-stu-id="506f9-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="506f9-114">Modifikátory, jako například `ByVal` nebo `ByRef`, která platí pro člena nebo parametrů členu.</span><span class="sxs-lookup"><span data-stu-id="506f9-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="506f9-115">Názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="506f9-115">Names of parameters</span></span>

- <span data-ttu-id="506f9-116">Návratové typy postupů</span><span class="sxs-lookup"><span data-stu-id="506f9-116">Return types of procedures</span></span>

<span data-ttu-id="506f9-117">`Overloads` – Klíčové slovo je volitelný při přetížení, ale pokud existuje přetížení člena používá `Overloads` – klíčové slovo, pak všechny ostatní přetěžované členy se stejným názvem musíte zadat také toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="506f9-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="506f9-118">Odvozené třídy mohou přetěžování zděděných členů s členy, které mají shodné parametry a typy parametrů, tento proces se označuje jako *stínováním podle názvu a podpisu*.</span><span class="sxs-lookup"><span data-stu-id="506f9-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="506f9-119">Pokud `Overloads` – klíčové slovo se používá při stínováním podle názvu a podpisu implementace odvozené třídy člena se použijí místo implementace základní třídy a všechny další přetížení pro tento člen bude k dispozici pro instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="506f9-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="506f9-120">Pokud `Overloads` – klíčové slovo je tento parametr vynecháte při přetížení zděděného člena s člena, který má stejné parametry a typy parametrů a pak přetížení se nazývá *stínováním podle názvu*.</span><span class="sxs-lookup"><span data-stu-id="506f9-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="506f9-121">Stínový provoz podle názvu nahrazuje zděděná implementace členu a je k dispozici k instancím typu odvozené třídy a jeho decedents dalšími přetíženími.</span><span class="sxs-lookup"><span data-stu-id="506f9-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="506f9-122">`Overloads` a `Shadows` Modifikátory nelze použít současně s stejné vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="506f9-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="506f9-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="506f9-123">Example</span></span>

<span data-ttu-id="506f9-124">Následující příklad vytvoří přetížené metody, které přijímají buď `String` nebo `Decimal` reprezentace částku a vrátit řetězec obsahující DPH.</span><span class="sxs-lookup"><span data-stu-id="506f9-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="506f9-125">Chcete-li použít tento příklad k vytvoření přetížené metody</span><span class="sxs-lookup"><span data-stu-id="506f9-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="506f9-126">Otevřete nový projekt a přidejte třídu pojmenovanou `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="506f9-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="506f9-127">Přidejte následující kód, který `TaxClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="506f9-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="506f9-128">Přidejte do svého formuláře následující postup.</span><span class="sxs-lookup"><span data-stu-id="506f9-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="506f9-129">Přidání tlačítka do formuláře a volání `ShowTax` procedury ze `Button1_Click` událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="506f9-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="506f9-130">Spusťte projekt a klikněte na tlačítko na formuláři pro testování přetížené `ShowTax` postup.</span><span class="sxs-lookup"><span data-stu-id="506f9-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="506f9-131">V době běhu kompilátor volí odpovídající Přetížená funkce, která odpovídá parametrů používaných.</span><span class="sxs-lookup"><span data-stu-id="506f9-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="506f9-132">Když kliknete na tlačítko, přetížená metoda je volána nejdřív s `Price` parametr, který je řetězec a zpráva "cena je řetězec.</span><span class="sxs-lookup"><span data-stu-id="506f9-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="506f9-133">Daň se $5.12" se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="506f9-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="506f9-134">`TaxAmount` je volána s `Decimal` hodnotu druhého klonování a zpráva, "cena je desetinné číslo.</span><span class="sxs-lookup"><span data-stu-id="506f9-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="506f9-135">Daň se $5.12" se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="506f9-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="506f9-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="506f9-136">See also</span></span>

- [<span data-ttu-id="506f9-137">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="506f9-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="506f9-138">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="506f9-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="506f9-139">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="506f9-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="506f9-140">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="506f9-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="506f9-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="506f9-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="506f9-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="506f9-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="506f9-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="506f9-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="506f9-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="506f9-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="506f9-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="506f9-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
