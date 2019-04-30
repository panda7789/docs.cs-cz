---
title: Property – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783991"
---
# <a name="property-statement"></a><span data-ttu-id="3fb87-102">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="3fb87-102">Property Statement</span></span>

<span data-ttu-id="3fb87-103">Deklaruje název vlastnosti a procedury vlastnosti používané k ukládání a načítání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fb87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb87-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="3fb87-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3fb87-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="3fb87-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-106">Optional.</span></span> <span data-ttu-id="3fb87-107">Seznam atributů, které se vztahují k této vlastnosti nebo `Get` nebo `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="3fb87-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="3fb87-108">Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="3fb87-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-109">Optional.</span></span> <span data-ttu-id="3fb87-110">Určuje, že tato vlastnost je výchozí vlastnost pro třídu nebo strukturu, na kterém je definována.</span><span class="sxs-lookup"><span data-stu-id="3fb87-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="3fb87-111">Výchozí vlastnosti musí přijímat parametry a může být nastavit a načíst bez určení názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="3fb87-112">Je-li deklarována vlastnost jako `Default`, nemůžete použít `Private` na vlastnost nebo některý z jeho procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="3fb87-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="3fb87-113">Volitelné na `Property` příkazu a jenom jedna z `Get` a `Set` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3fb87-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="3fb87-114">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3fb87-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="3fb87-115">Public</span><span class="sxs-lookup"><span data-stu-id="3fb87-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="3fb87-116">Protected</span><span class="sxs-lookup"><span data-stu-id="3fb87-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="3fb87-117">Friend</span><span class="sxs-lookup"><span data-stu-id="3fb87-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="3fb87-118">Private</span><span class="sxs-lookup"><span data-stu-id="3fb87-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="3fb87-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="3fb87-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="3fb87-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="3fb87-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="3fb87-121">Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="3fb87-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-122">Optional.</span></span> <span data-ttu-id="3fb87-123">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3fb87-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="3fb87-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="3fb87-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="3fb87-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="3fb87-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="3fb87-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="3fb87-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="3fb87-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3fb87-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="3fb87-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3fb87-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="3fb87-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-129">Optional.</span></span> <span data-ttu-id="3fb87-130">Zobrazit [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="3fb87-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-131">Optional.</span></span> <span data-ttu-id="3fb87-132">Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="3fb87-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-133">Optional.</span></span> <span data-ttu-id="3fb87-134">Zobrazit [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="3fb87-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-135">Optional.</span></span> <span data-ttu-id="3fb87-136">Zobrazit [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="3fb87-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-137">Optional.</span></span> <span data-ttu-id="3fb87-138">Zobrazit [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="3fb87-139">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3fb87-139">Required.</span></span> <span data-ttu-id="3fb87-140">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3fb87-140">Name of the property.</span></span> <span data-ttu-id="3fb87-141">Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="3fb87-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-142">Optional.</span></span> <span data-ttu-id="3fb87-143">Seznam představující parametry této vlastnosti a je to možné další parametry místní názvy proměnných `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="3fb87-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="3fb87-144">Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="3fb87-145">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="3fb87-146">Datový typ hodnoty vrácené touto vlastností.</span><span class="sxs-lookup"><span data-stu-id="3fb87-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="3fb87-147">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-147">Optional.</span></span> <span data-ttu-id="3fb87-148">Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každý z nich definované v rozhraní implementované obsahující třídu nebo strukturu tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3fb87-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="3fb87-149">Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="3fb87-150">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="3fb87-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="3fb87-151">Seznam vlastností se implementuje.</span><span class="sxs-lookup"><span data-stu-id="3fb87-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="3fb87-152">Každý `implementedproperty` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="3fb87-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="3fb87-153">Část</span><span class="sxs-lookup"><span data-stu-id="3fb87-153">Part</span></span>|<span data-ttu-id="3fb87-154">Popis</span><span class="sxs-lookup"><span data-stu-id="3fb87-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="3fb87-155">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3fb87-155">Required.</span></span> <span data-ttu-id="3fb87-156">Název rozhraní implementovaná touto vlastností obsahující třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3fb87-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="3fb87-157">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3fb87-157">Required.</span></span> <span data-ttu-id="3fb87-158">Název, podle kterého je vlastnost definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="3fb87-159">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-159">Optional.</span></span> <span data-ttu-id="3fb87-160">Povinné, pokud je vlastnost označena `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3fb87-161">Spustí `Get` procedura property, který se používá k vrácení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>

- `statements`

  <span data-ttu-id="3fb87-162">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-162">Optional.</span></span> <span data-ttu-id="3fb87-163">Blok příkazů ke spuštění v rámci `Get` nebo `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="3fb87-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="3fb87-164">Ukončuje `Get` procedura property.</span><span class="sxs-lookup"><span data-stu-id="3fb87-164">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="3fb87-165">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3fb87-165">Optional.</span></span> <span data-ttu-id="3fb87-166">Povinné, pokud je vlastnost označena `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3fb87-167">Spustí `Set` procedura property, který se používá k uložení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>

- `End Set`

  <span data-ttu-id="3fb87-168">Ukončuje `Set` procedura property.</span><span class="sxs-lookup"><span data-stu-id="3fb87-168">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="3fb87-169">Ukončí definici této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-169">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fb87-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fb87-170">Remarks</span></span>

<span data-ttu-id="3fb87-171">`Property` Příkaz zavádí deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="3fb87-172">Vlastnost může mít `Get` procedury (jen pro čtení), `Set` postupu (pouze pro zápis) nebo obě (čtení a zápis).</span><span class="sxs-lookup"><span data-stu-id="3fb87-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="3fb87-173">Můžete vynechat `Get` a `Set` procedury při použití automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="3fb87-174">Další informace najdete v tématu [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="3fb87-175">Můžete použít `Property` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="3fb87-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="3fb87-176">To znamená, že *kontext deklarace* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="3fb87-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="3fb87-177">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3fb87-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="3fb87-178">Ve výchozím nastavení použijte vlastnosti veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="3fb87-178">By default, properties use public access.</span></span> <span data-ttu-id="3fb87-179">Úroveň přístupu k vlastnosti s modifikátor přístupu můžete upravit na `Property` příkaz kde můžete volitelně nastavit jeden z jeho vlastnost postupy do více omezující úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="3fb87-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="3fb87-180">Visual Basic předá parametr `Set` postupu během přiřazení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3fb87-181">Pokud nezadáte parametr `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3fb87-182">Tento parametr obsahuje hodnotu pro přiřazení k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3fb87-183">Obvykle tuto hodnotu v privátní místní proměnné a vrácení pokaždé, když `Get` volání procedury.</span><span class="sxs-lookup"><span data-stu-id="3fb87-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="3fb87-184">pravidla</span><span class="sxs-lookup"><span data-stu-id="3fb87-184">Rules</span></span>

- <span data-ttu-id="3fb87-185">**Smíšenými úrovněmi přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3fb87-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="3fb87-186">Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="3fb87-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3fb87-187">Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="3fb87-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3fb87-188">Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Set` postup `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="3fb87-189">Pokud definujete `ReadOnly` nebo `WriteOnly` vlastnosti, procedury jedné vlastnosti (`Get` nebo `Set`v uvedeném pořadí) představuje všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="3fb87-190">Úroveň různý přístup pro tento postup nemůže deklarovat, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.</span><span class="sxs-lookup"><span data-stu-id="3fb87-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="3fb87-191">**Návratový typ.**</span><span class="sxs-lookup"><span data-stu-id="3fb87-191">**Return Type.**</span></span> <span data-ttu-id="3fb87-192">`Property` Příkazu můžete deklarovat datový typ hodnoty vrácením.</span><span class="sxs-lookup"><span data-stu-id="3fb87-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="3fb87-193">Můžete zadat libovolný datový typ nebo název výčtu, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3fb87-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="3fb87-194">Pokud nezadáte `returntype`, vrátí vlastnost `Object`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-194">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="3fb87-195">**Implementace.**</span><span class="sxs-lookup"><span data-stu-id="3fb87-195">**Implementation.**</span></span> <span data-ttu-id="3fb87-196">Pokud tuto vlastnost používá `Implements` – klíčové slovo, obsahuje třídu nebo strukturu, musíte mít `Implements` příkaz ihned po jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="3fb87-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="3fb87-197">`Implements` Příkazu musí obsahovat každé rozhraní, udávaná v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="3fb87-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="3fb87-198">Ale název, pomocí kterého rozhraní definuje `Property` (v `definedname`) nebude muset být stejný jako název této vlastnosti (v `name`).</span><span class="sxs-lookup"><span data-stu-id="3fb87-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="3fb87-199">Chování</span><span class="sxs-lookup"><span data-stu-id="3fb87-199">Behavior</span></span>

- <span data-ttu-id="3fb87-200">**Návrat z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="3fb87-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3fb87-201">Když `Get` nebo `Set` postup vrátí volajícímu kódu, provádění pokračuje s příkazu za příkazem, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="3fb87-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="3fb87-202">`Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3fb87-203">Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3fb87-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="3fb87-204">**Vrátí hodnotu.**</span><span class="sxs-lookup"><span data-stu-id="3fb87-204">**Return Value.**</span></span> <span data-ttu-id="3fb87-205">Pro navrácení hodnoty z `Get` postup, můžete přiřadit hodnoty pro název vlastnosti, nebo ho v `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3fb87-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="3fb87-206">Následující příklad přiřadí návratovou hodnotu pro název vlastnosti `quoteForTheDay` a použije je `Exit Property` příkazu vrátit.</span><span class="sxs-lookup"><span data-stu-id="3fb87-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="3fb87-207">Pokud používáte `Exit Property` bez přiřazení hodnoty k `name`, `Get` procedura vrací výchozí hodnota pro typ dat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3fb87-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="3fb87-208">`Return` Příkaz v době, přiřadí `Get` procedura vracet hodnotu a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="3fb87-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="3fb87-209">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="3fb87-209">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="3fb87-210">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fb87-210">Example</span></span>

<span data-ttu-id="3fb87-211">Následující příklad deklaruje vlastnosti ve třídě.</span><span class="sxs-lookup"><span data-stu-id="3fb87-211">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="3fb87-212">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fb87-212">See also</span></span>

- [<span data-ttu-id="3fb87-213">Automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3fb87-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="3fb87-214">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="3fb87-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3fb87-215">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="3fb87-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="3fb87-216">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="3fb87-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="3fb87-217">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="3fb87-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="3fb87-218">Default</span><span class="sxs-lookup"><span data-stu-id="3fb87-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
