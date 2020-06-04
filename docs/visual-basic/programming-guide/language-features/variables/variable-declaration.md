---
title: Deklarace proměnné
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 587cb84faa09b686361c255c413ad852780b8971
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410293"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="30511-102">Deklarace proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30511-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="30511-103">Deklarujete proměnnou pro určení jejího názvu a charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="30511-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="30511-104">Příkaz deklarace pro proměnné je [příkaz Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30511-104">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="30511-105">Jeho umístění a obsah určují charakteristiky proměnné.</span><span class="sxs-lookup"><span data-stu-id="30511-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="30511-106">Informace o pravidlech pojmenovávání a požadavcích naleznete v tématu [deklarované názvy elementů](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="30511-106">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="30511-107">Úrovně deklarací</span><span class="sxs-lookup"><span data-stu-id="30511-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="30511-108">Místní a členské proměnné</span><span class="sxs-lookup"><span data-stu-id="30511-108">Local and Member Variables</span></span>  
 <span data-ttu-id="30511-109">*Lokální proměnná* je jedna, která je deklarována v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="30511-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="30511-110">*Členská proměnná* je členem Visual Basicho typu; je deklarována na úrovni modulu uvnitř třídy, struktury nebo modulu, ale ne v rámci žádné procedury vnitřní k této třídě, struktuře nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="30511-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="30511-111">Sdílené a proměnné instance</span><span class="sxs-lookup"><span data-stu-id="30511-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="30511-112">Ve třídě nebo struktuře závisí kategorie členské proměnné na tom, zda je nebo není sdílena.</span><span class="sxs-lookup"><span data-stu-id="30511-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="30511-113">Je-li deklarován se [sdíleným](../../../language-reference/modifiers/shared.md) klíčovým slovem, jedná se o *sdílenou proměnnou*a existuje v jedné kopii sdílené mezi všemi instancemi třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="30511-113">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="30511-114">V opačném případě se jedná o *proměnnou instance*a samostatná kopie je vytvořena pro každou instanci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="30511-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="30511-115">Daná kopie proměnné instance je k dispozici pouze pro instanci třídy nebo struktury, ve které byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="30511-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="30511-116">Je nezávislý na kopii proměnné instance v jakékoli jiné instanci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="30511-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="30511-117">Deklarace datového typu</span><span class="sxs-lookup"><span data-stu-id="30511-117">Declaring Data Type</span></span>  
 <span data-ttu-id="30511-118">Klauzule [as](../../../language-reference/statements/as-clause.md) v příkazu Declaration umožňuje definovat datový typ nebo typ objektu pro proměnnou, kterou deklarujete.</span><span class="sxs-lookup"><span data-stu-id="30511-118">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="30511-119">Pro proměnnou můžete zadat kterýkoli z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="30511-119">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="30511-120">Základní datový typ, například `Boolean` , `Long` nebo`Decimal`</span><span class="sxs-lookup"><span data-stu-id="30511-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="30511-121">Složený datový typ, jako je například pole nebo struktura</span><span class="sxs-lookup"><span data-stu-id="30511-121">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="30511-122">Typ objektu nebo třída definovaný buď v aplikaci, nebo v jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="30511-122">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="30511-123">.NET Framework třídy, například <xref:System.Windows.Forms.Label> nebo<xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="30511-123">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="30511-124">Typ rozhraní, například <xref:System.IComparable> nebo<xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="30511-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="30511-125">Můžete deklarovat několik proměnných v jednom příkazu bez nutnosti opakovat datový typ.</span><span class="sxs-lookup"><span data-stu-id="30511-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="30511-126">V následujících příkazech `i` jsou proměnné, `j` a `k` deklarovány jako typ `Integer` `l` a jako a `m` `Long` `x` a a `y` jako `Single` :</span><span class="sxs-lookup"><span data-stu-id="30511-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="30511-127">Další informace o typech dat najdete v tématu [datové typy](../data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="30511-127">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="30511-128">Další informace o objektech naleznete v tématu [objekty a třídy](../objects-and-classes/index.md) a [programování pomocí komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="30511-128">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="30511-129">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="30511-129">Local Type Inference</span></span>  
 <span data-ttu-id="30511-130">*Odvození typu* se používá k určení datových typů místních proměnných deklarovaných bez `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="30511-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="30511-131">Kompilátor odvodí typ proměnné z typu inicializačního výrazu.</span><span class="sxs-lookup"><span data-stu-id="30511-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="30511-132">To umožňuje deklarovat proměnné bez explicitního oznámení typu.</span><span class="sxs-lookup"><span data-stu-id="30511-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="30511-133">V následujícím příkladu `num1` a `num2` jsou silného typu jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="30511-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="30511-134">Pokud chcete použít odvození místního typu, `Option Infer` musí být nastavena na `On` .</span><span class="sxs-lookup"><span data-stu-id="30511-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="30511-135">Další informace naleznete v tématu [odvození místního typu](local-type-inference.md) a [příkaz k odvození možnosti](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30511-135">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="30511-136">Charakteristiky deklarovaných proměnných</span><span class="sxs-lookup"><span data-stu-id="30511-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="30511-137">*Doba života* proměnné je doba, po kterou je možné ji použít.</span><span class="sxs-lookup"><span data-stu-id="30511-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="30511-138">Obecně platí, že proměnná existuje, pokud element, který ji deklaruje (například procedura nebo třída), nadále existují.</span><span class="sxs-lookup"><span data-stu-id="30511-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="30511-139">Pokud proměnná nemusí pokračovat po dobu životnosti jejího obsahujícího prvku, nemusíte v deklaraci provádět žádné zvláštní akce.</span><span class="sxs-lookup"><span data-stu-id="30511-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="30511-140">Pokud proměnná musí nadále existovat, než obsahuje element, můžete `Static` `Shared` do jejího příkazu zahrnout klíčové slovo or `Dim` .</span><span class="sxs-lookup"><span data-stu-id="30511-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="30511-141">Další informace najdete v tématu [Doba života v Visual Basic](../declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="30511-141">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="30511-142">*Rozsah* proměnné je sada veškerého kódu, který se na něj může odkazovat bez kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="30511-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="30511-143">Rozsah proměnné je určen podle toho, kde je deklarována.</span><span class="sxs-lookup"><span data-stu-id="30511-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="30511-144">Kód umístěný v dané oblasti může používat proměnné definované v této oblasti, aniž by bylo nutné kvalifikovat jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="30511-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="30511-145">Další informace najdete v tématu věnovaném [oboru v Visual Basic](../declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="30511-145">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="30511-146">*Úroveň přístupu* proměnné je rozsah kódu, který má oprávnění k přístupu.</span><span class="sxs-lookup"><span data-stu-id="30511-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="30511-147">To je určeno modifikátorem přístupu (například [veřejným](../../../language-reference/modifiers/public.md) nebo [soukromým](../../../language-reference/modifiers/private.md)), který použijete v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="30511-147">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="30511-148">Další informace najdete v tématu [úrovně přístupu v Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="30511-148">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30511-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="30511-149">See also</span></span>

- [<span data-ttu-id="30511-150">Postupy: Vytvoření nové proměnné</span><span class="sxs-lookup"><span data-stu-id="30511-150">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="30511-151">Postupy: Přesun dat do proměnné a z proměnné</span><span class="sxs-lookup"><span data-stu-id="30511-151">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="30511-152">Datové typy</span><span class="sxs-lookup"><span data-stu-id="30511-152">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="30511-153">Proti</span><span class="sxs-lookup"><span data-stu-id="30511-153">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="30511-154">Friend</span><span class="sxs-lookup"><span data-stu-id="30511-154">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="30511-155">Tras</span><span class="sxs-lookup"><span data-stu-id="30511-155">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="30511-156">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="30511-156">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="30511-157">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="30511-157">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="30511-158">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="30511-158">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
