---
title: "Vlastnosti a metody přetečení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="1e7a8-102">Vlastnosti a metody přetečení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e7a8-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="1e7a8-103">Přetížení je vytvoření více procedur, konstruktoru instance nebo vlastnost v třídě se stejným názvem, ale s typy argumentů jiný.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="1e7a8-104">Přetížení využití</span><span class="sxs-lookup"><span data-stu-id="1e7a8-104">Overloading Usage</span></span>  
 <span data-ttu-id="1e7a8-105">Přetížení je obzvláště užitečné, když objektový model stanoví, že nepoužijete identické názvy postupy, které působí na různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="1e7a8-106">Například může mít třídy, která může zobrazit několik různých datových typů `Display` postupy, které vypadají takto:</span><span class="sxs-lookup"><span data-stu-id="1e7a8-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 <span data-ttu-id="1e7a8-107">Bez přetížení, museli byste vytvořit jedinečné názvy pro každý postup, i když udělají samé, jak ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="1e7a8-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 <span data-ttu-id="1e7a8-108">Přetížení usnadňuje použít vlastností nebo metod, protože poskytuje výběru datových typů, které lze použít.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="1e7a8-109">Například přetížené `Display` popsané dříve nelze volat metodu s žádným z následujících řádků kódu:</span><span class="sxs-lookup"><span data-stu-id="1e7a8-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 <span data-ttu-id="1e7a8-110">V době běhu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] volání správný postup na základě datové typy parametrů můžete zadat.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-110">At run time, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="1e7a8-111">Přetížení pravidla</span><span class="sxs-lookup"><span data-stu-id="1e7a8-111">Overloading Rules</span></span>  
 <span data-ttu-id="1e7a8-112">Vytvoříte člena přetížená pro třídu přidáním dva nebo více vlastností nebo metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="1e7a8-113">S výjimkou přetížené odvozené členy každý přetížené člen musí mít jiný parametr seznamy a následující položky nelze použít jako rozdílné funkce v případě přetížení vlastnosti nebo postup:</span><span class="sxs-lookup"><span data-stu-id="1e7a8-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="1e7a8-114">Modifikátory, jako například `ByVal` nebo `ByRef`, která platí pro člen, nebo parametry člena.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="1e7a8-115">Názvy parametrů</span><span class="sxs-lookup"><span data-stu-id="1e7a8-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="1e7a8-116">Návratové typy procedury</span><span class="sxs-lookup"><span data-stu-id="1e7a8-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="1e7a8-117">`Overloads` – Klíčové slovo je nepovinný, pokud přetížení, ale pokud existují přetížený člen používá `Overloads` – klíčové slovo, pak všechny ostatní přetěžované členy se stejným názvem musíte zadat také toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="1e7a8-118">Odvozené třídy mohou přetížení zděděné členy se členy, kteří mají stejné parametry a typy parametrů, tento proces se označuje jako *stínový provoz podle názvu a podpis*.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="1e7a8-119">Pokud `Overloads` – klíčové slovo se používá, když stínováním podle názvu a podpis, implementaci odvozené třídě člena použije místo implementace v základní třídě a dalšími přetíženími pro tento člen bude k dispozici pro instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="1e7a8-120">Pokud `Overloads` – klíčové slovo je vynechán, při přetížení zděděného členu s člena, který má stejné parametry a typy parametrů a potom přetížení se nazývá *stínový provoz podle názvu*.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="1e7a8-121">Stínový provoz podle názvu nahrazuje zděděné implementace členem, a dalšími přetíženími umožňuje pro instance odvozené třídě a jeho decedents není dostupná.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="1e7a8-122">`Overloads` a `Shadows` Modifikátory nelze kombinovat s stejné vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="1e7a8-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e7a8-123">Example</span></span>  
 <span data-ttu-id="1e7a8-124">Následující příklad vytvoří přetížené metody, které přijímají buď `String` nebo `Decimal` reprezentace dolaru velikost a vrátí řetězec obsahující DPH.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="1e7a8-125">Chcete-li použít tento příklad k vytvoření přetížené metody</span><span class="sxs-lookup"><span data-stu-id="1e7a8-125">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="1e7a8-126">Otevřete nový projekt a přidejte třídu s názvem `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="1e7a8-127">Přidejte následující kód, který `TaxClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  <span data-ttu-id="1e7a8-128">Přidejte do svého formuláře následující postup.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  <span data-ttu-id="1e7a8-129">Přidání tlačítka do formuláře a volání `ShowTax` procedury `Button1_Click` události tlačítka.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="1e7a8-130">Spusťte projekt a klikněte na tlačítko ve formuláři pro testování přetížené `ShowTax` postupu.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="1e7a8-131">V době běhu zvolí kompilátoru příslušné přetížené funkce, která odpovídá parametry používá.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="1e7a8-132">Když kliknete na tlačítko, přetížené metoda je volána nejprve s `Price` parametr, který je řetězec a zobrazí zpráva "cena je řetězec.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="1e7a8-133">Daň je $5.12" se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="1e7a8-134">`TaxAmount`je volána s `Decimal` hodnotu druhém a zpráva, "cena je datový typ Decimal.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="1e7a8-135">Daň je $5.12" se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="1e7a8-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e7a8-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e7a8-136">See Also</span></span>  
 [<span data-ttu-id="1e7a8-137">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="1e7a8-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="1e7a8-138">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e7a8-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="1e7a8-139">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="1e7a8-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="1e7a8-140">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="1e7a8-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="1e7a8-141">Stínů</span><span class="sxs-lookup"><span data-stu-id="1e7a8-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="1e7a8-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="1e7a8-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="1e7a8-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="1e7a8-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="1e7a8-144">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1e7a8-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="1e7a8-145">Stínů</span><span class="sxs-lookup"><span data-stu-id="1e7a8-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
