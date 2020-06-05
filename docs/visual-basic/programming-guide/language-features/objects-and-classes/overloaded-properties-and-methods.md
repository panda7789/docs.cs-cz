---
title: Přetížené vlastnosti a metody
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
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389149"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="0248b-102">Přetížené vlastnosti a metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0248b-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="0248b-103">Přetížení je vytvoření více než jedné procedury, konstruktoru instance nebo vlastnosti ve třídě se stejným názvem, ale s různými typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="0248b-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="0248b-104">Přetížení využití</span><span class="sxs-lookup"><span data-stu-id="0248b-104">Overloading usage</span></span>

<span data-ttu-id="0248b-105">Přetížení je obzvláště užitečné, když objektový model určuje, že pro procedury, které pracují s různými datovými typy, využíváte stejné názvy.</span><span class="sxs-lookup"><span data-stu-id="0248b-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="0248b-106">Například třída, která může zobrazit několik různých datových typů, může mít `Display` postupy, které vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="0248b-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="0248b-107">Bez přetížení byste museli pro každý postup vytvořit rozdílné názvy, a to i v případě, že mají stejnou věc, jak je uvedeno dále:</span><span class="sxs-lookup"><span data-stu-id="0248b-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="0248b-108">Přetížení usnadňuje používání vlastností nebo metod, protože poskytuje možnost volby datových typů, které lze použít.</span><span class="sxs-lookup"><span data-stu-id="0248b-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="0248b-109">Například přetížená metoda, kterou `Display` jsme probrali dříve, může být volána s libovolným z následujících řádků kódu:</span><span class="sxs-lookup"><span data-stu-id="0248b-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="0248b-110">V době běhu Visual Basic volá správný postup na základě datových typů zadaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="0248b-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="0248b-111">Pravidla přetížení</span><span class="sxs-lookup"><span data-stu-id="0248b-111">Overloading rules</span></span>

 <span data-ttu-id="0248b-112">Můžete vytvořit přetíženého člena pro třídu přidáním dvou nebo více vlastností nebo metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="0248b-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="0248b-113">S výjimkou přetížených členů musí mít každý přetížený člen jiný seznam parametrů a následující položky nelze použít jako rozdílové funkce při přetížení vlastnosti nebo procedury:</span><span class="sxs-lookup"><span data-stu-id="0248b-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="0248b-114">Modifikátory, například `ByVal` nebo `ByRef` , které platí pro člena nebo parametry člena.</span><span class="sxs-lookup"><span data-stu-id="0248b-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="0248b-115">Názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="0248b-115">Names of parameters</span></span>

- <span data-ttu-id="0248b-116">Návratové typy procedur</span><span class="sxs-lookup"><span data-stu-id="0248b-116">Return types of procedures</span></span>

<span data-ttu-id="0248b-117">`Overloads`Klíčové slovo je nepovinné při přetížení, ale pokud nějaký přetížený člen používá `Overloads` klíčové slovo, pak všechny ostatní přetížené členy, které mají stejný název, musí také zadat toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0248b-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="0248b-118">Odvozené třídy mohou přetížit zděděné členy se členy, kteří mají stejné parametry a typy parametrů, což je proces známý jako *stínování podle názvu a podpisu*.</span><span class="sxs-lookup"><span data-stu-id="0248b-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="0248b-119">Pokud `Overloads` je klíčové slovo použito při stínování podle názvu a signatury, použije se místo implementace v základní třídě implementace odvozené třídy a všechna ostatní přetížení tohoto člena budou k dispozici pro instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="0248b-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="0248b-120">Pokud `Overloads` je klíčové slovo vynecháno při přetížení zděděného člena se členem, který má stejné parametry a typy parametrů, pak přetížení se nazývá *Stínová hodnota podle názvu*.</span><span class="sxs-lookup"><span data-stu-id="0248b-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="0248b-121">Stínová kopie podle názvu nahradí zděděnou implementaci člena a zpřístupňuje všechna ostatní přetížení instancím odvozené třídy a její decedents.</span><span class="sxs-lookup"><span data-stu-id="0248b-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="0248b-122">`Overloads` `Shadows` Modifikátory a nelze současně použít se stejnou vlastností nebo metodou.</span><span class="sxs-lookup"><span data-stu-id="0248b-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="0248b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="0248b-123">Example</span></span>

<span data-ttu-id="0248b-124">Následující příklad vytvoří přetížené metody, které přijímají buď `String` nebo `Decimal` reprezentaci částky dolaru, a vrátí řetězec obsahující DPH.</span><span class="sxs-lookup"><span data-stu-id="0248b-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="0248b-125">Chcete-li použít tento příklad k vytvoření přetížené metody</span><span class="sxs-lookup"><span data-stu-id="0248b-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="0248b-126">Otevřete nový projekt a přidejte třídu s názvem `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="0248b-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="0248b-127">Do třídy přidejte následující kód `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="0248b-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="0248b-128">Do formuláře přidejte následující proceduru.</span><span class="sxs-lookup"><span data-stu-id="0248b-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="0248b-129">Přidejte do formuláře tlačítko a zavolejte `ShowTax` proceduru z `Button1_Click` události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="0248b-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="0248b-130">Spusťte projekt a klikněte na tlačítko na formuláři pro otestování přetížené `ShowTax` procedury.</span><span class="sxs-lookup"><span data-stu-id="0248b-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="0248b-131">V době běhu kompilátor zvolí vhodnou přetíženou funkci, která odpovídá použitým parametrům.</span><span class="sxs-lookup"><span data-stu-id="0248b-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="0248b-132">Po kliknutí na tlačítko je přetížená metoda nejprve volána s `Price` parametrem, který je řetězec a zpráva, "Price je řetězec.</span><span class="sxs-lookup"><span data-stu-id="0248b-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="0248b-133">Zobrazí se daň $5,12.</span><span class="sxs-lookup"><span data-stu-id="0248b-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="0248b-134">`TaxAmount`je volána s `Decimal` hodnotou podruhé a zprávou "Price je desetinné číslo.</span><span class="sxs-lookup"><span data-stu-id="0248b-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="0248b-135">Zobrazí se daň $5,12.</span><span class="sxs-lookup"><span data-stu-id="0248b-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0248b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="0248b-136">See also</span></span>

- [<span data-ttu-id="0248b-137">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="0248b-137">Objects and Classes</span></span>](index.md)
- [<span data-ttu-id="0248b-138">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0248b-138">Shadowing in Visual Basic</span></span>](../declared-elements/shadowing.md)
- [<span data-ttu-id="0248b-139">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="0248b-139">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="0248b-140">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="0248b-140">Inheritance Basics</span></span>](inheritance-basics.md)
- [<span data-ttu-id="0248b-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="0248b-141">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="0248b-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="0248b-142">ByVal</span></span>](../../../language-reference/modifiers/byval.md)
- [<span data-ttu-id="0248b-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="0248b-143">ByRef</span></span>](../../../language-reference/modifiers/byref.md)
- [<span data-ttu-id="0248b-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="0248b-144">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="0248b-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="0248b-145">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
