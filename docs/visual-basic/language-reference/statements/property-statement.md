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
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332748"
---
# <a name="property-statement"></a><span data-ttu-id="51562-102">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="51562-102">Property Statement</span></span>

<span data-ttu-id="51562-103">Deklaruje název vlastnosti a procedury vlastnosti používané k ukládání a načítání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="51562-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51562-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="51562-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="51562-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="51562-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-106">Optional.</span></span> <span data-ttu-id="51562-107">Seznam atributů, které se vztahují na tuto vlastnost nebo `Get` nebo `Set` postup.</span><span class="sxs-lookup"><span data-stu-id="51562-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="51562-108">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="51562-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="51562-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-109">Optional.</span></span> <span data-ttu-id="51562-110">Určuje, že tato vlastnost je výchozí vlastností třídy nebo struktury, ve které je definována.</span><span class="sxs-lookup"><span data-stu-id="51562-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="51562-111">Výchozí vlastnosti musí přijímat parametry a lze je nastavit a načíst bez zadání názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="51562-112">Pokud vlastnost deklarujete jako `Default`, nemůžete použít `Private` na vlastnost nebo v jednom z jeho procedur vlastností.</span><span class="sxs-lookup"><span data-stu-id="51562-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="51562-113">Volitelné v příkazu `Property` a maximálně jeden z příkazů `Get` a `Set`.</span><span class="sxs-lookup"><span data-stu-id="51562-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="51562-114">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="51562-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="51562-115">Public</span><span class="sxs-lookup"><span data-stu-id="51562-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="51562-116">Protected</span><span class="sxs-lookup"><span data-stu-id="51562-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="51562-117">Friend</span><span class="sxs-lookup"><span data-stu-id="51562-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="51562-118">Private</span><span class="sxs-lookup"><span data-stu-id="51562-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="51562-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="51562-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="51562-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="51562-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="51562-121">Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="51562-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="51562-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-122">Optional.</span></span> <span data-ttu-id="51562-123">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="51562-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="51562-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="51562-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="51562-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="51562-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="51562-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="51562-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="51562-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="51562-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="51562-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="51562-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="51562-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-129">Optional.</span></span> <span data-ttu-id="51562-130">Viz [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="51562-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="51562-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-131">Optional.</span></span> <span data-ttu-id="51562-132">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="51562-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="51562-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-133">Optional.</span></span> <span data-ttu-id="51562-134">Zobrazit [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="51562-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="51562-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-135">Optional.</span></span> <span data-ttu-id="51562-136">Viz [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="51562-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="51562-137">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-137">Optional.</span></span> <span data-ttu-id="51562-138">Podívejte se na [iterátor](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="51562-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="51562-139">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="51562-139">Required.</span></span> <span data-ttu-id="51562-140">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="51562-140">Name of the property.</span></span> <span data-ttu-id="51562-141">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="51562-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="51562-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-142">Optional.</span></span> <span data-ttu-id="51562-143">Seznam místních názvů proměnných reprezentujících parametry této vlastnosti a možné další parametry `Set`ho postupu.</span><span class="sxs-lookup"><span data-stu-id="51562-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="51562-144">Viz [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="51562-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="51562-145">Vyžaduje se, pokud `Option Strict` `On`.</span><span class="sxs-lookup"><span data-stu-id="51562-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="51562-146">Datový typ hodnoty vrácené touto vlastností</span><span class="sxs-lookup"><span data-stu-id="51562-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="51562-147">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-147">Optional.</span></span> <span data-ttu-id="51562-148">Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každý z nich definovaný v rozhraní implementovaném touto vlastností, která obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="51562-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="51562-149">Viz [příkaz Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="51562-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="51562-150">Vyžaduje se, pokud je dodána `Implements`.</span><span class="sxs-lookup"><span data-stu-id="51562-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="51562-151">Seznam implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="51562-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="51562-152">Každý `implementedproperty` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="51562-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="51562-153">Částí</span><span class="sxs-lookup"><span data-stu-id="51562-153">Part</span></span>|<span data-ttu-id="51562-154">Popis</span><span class="sxs-lookup"><span data-stu-id="51562-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="51562-155">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="51562-155">Required.</span></span> <span data-ttu-id="51562-156">Název rozhraní implementovaného touto vlastností, která obsahuje třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="51562-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="51562-157">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="51562-157">Required.</span></span> <span data-ttu-id="51562-158">Název, podle kterého je vlastnost definovaná v `interface`.</span><span class="sxs-lookup"><span data-stu-id="51562-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="51562-159">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-159">Optional.</span></span> <span data-ttu-id="51562-160">Vyžaduje se, pokud je vlastnost označená `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="51562-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="51562-161">Spustí proceduru `Get` vlastnost, která se používá k vrácení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="51562-162">Příkaz `Get` se nepoužívá s [automaticky implementovanými vlastnostmi](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="51562-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="51562-163">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-163">Optional.</span></span> <span data-ttu-id="51562-164">Blok příkazů, které se mají spustit v rámci `Get` nebo `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="51562-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="51562-165">Ukončí proceduru vlastnosti `Get`.</span><span class="sxs-lookup"><span data-stu-id="51562-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="51562-166">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="51562-166">Optional.</span></span> <span data-ttu-id="51562-167">Vyžaduje se, pokud je vlastnost označená `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="51562-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="51562-168">Spustí `Set` proceduru vlastnosti, která se používá k uložení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="51562-169">Příkaz `Set` se nepoužívá s [automaticky implementovanými vlastnostmi](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="51562-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="51562-170">Ukončí proceduru vlastnosti `Set`.</span><span class="sxs-lookup"><span data-stu-id="51562-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="51562-171">Ukončí definici této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="51562-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51562-172">Remarks</span></span>

<span data-ttu-id="51562-173">Příkaz `Property` zavádí deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="51562-174">Vlastnost může mít `Get` proceduru (jen pro čtení), `Set` proceduru (jen pro zápis) nebo obou (pro čtení i zápis).</span><span class="sxs-lookup"><span data-stu-id="51562-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="51562-175">Můžete vynechat `Get` a `Set` postup při použití automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="51562-176">Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="51562-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="51562-177">`Property` lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="51562-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="51562-178">To znamená, že *kontext deklarace* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok.</span><span class="sxs-lookup"><span data-stu-id="51562-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="51562-179">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="51562-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="51562-180">Ve výchozím nastavení vlastnosti používají veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="51562-180">By default, properties use public access.</span></span> <span data-ttu-id="51562-181">Úroveň přístupu vlastnosti můžete upravit pomocí modifikátoru přístupu u příkazu `Property` a volitelně můžete upravit jeden z jeho procedur vlastností na více omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="51562-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="51562-182">Visual Basic předá do přiřazení vlastností parametr `Set` proceduře.</span><span class="sxs-lookup"><span data-stu-id="51562-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="51562-183">Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="51562-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="51562-184">Tento parametr obsahuje hodnotu, která má být přiřazena vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="51562-185">Tuto hodnotu obvykle ukládáte do privátní místní proměnné a vrátíte ji pokaždé, když je volána procedura `Get`.</span><span class="sxs-lookup"><span data-stu-id="51562-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="51562-186">Pravidla</span><span class="sxs-lookup"><span data-stu-id="51562-186">Rules</span></span>

- <span data-ttu-id="51562-187">**Smíšené úrovně přístupu.**</span><span class="sxs-lookup"><span data-stu-id="51562-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="51562-188">Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="51562-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="51562-189">Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="51562-190">Například pokud je vlastnost deklarována `Friend`, můžete deklarovat `Set` proceduru `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="51562-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="51562-191">Pokud definujete vlastnost `ReadOnly` nebo `WriteOnly`, bude procedura s jedinou vlastností (`Get` nebo `Set`) představovat všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="51562-192">Pro takový postup nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="51562-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="51562-193">**Návratový typ**</span><span class="sxs-lookup"><span data-stu-id="51562-193">**Return Type.**</span></span> <span data-ttu-id="51562-194">Příkaz `Property` může deklarovat datový typ hodnoty, kterou vrátí.</span><span class="sxs-lookup"><span data-stu-id="51562-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="51562-195">Můžete zadat libovolný datový typ nebo název výčtu, struktury, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="51562-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="51562-196">Pokud nezadáte `returntype`, vlastnost vrátí `Object`.</span><span class="sxs-lookup"><span data-stu-id="51562-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="51562-197">**Provádění.**</span><span class="sxs-lookup"><span data-stu-id="51562-197">**Implementation.**</span></span> <span data-ttu-id="51562-198">Pokud tato vlastnost používá klíčové slovo `Implements`, obsahující třídu nebo strukturu musí mít příkaz `Implements` hned za `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="51562-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="51562-199">Příkaz `Implements` musí zahrnovat každé rozhraní určené v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="51562-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="51562-200">Název, kterým rozhraní definuje `Property` (v `definedname`) ale nemusí být stejný jako název této vlastnosti (v `name`).</span><span class="sxs-lookup"><span data-stu-id="51562-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="51562-201">Chování</span><span class="sxs-lookup"><span data-stu-id="51562-201">Behavior</span></span>

- <span data-ttu-id="51562-202">**Návrat z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="51562-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="51562-203">Když se `Get` nebo `Set` vrátí k volajícímu kódu, provádění pokračuje příkazem po příkazu, který ho vyvolal.</span><span class="sxs-lookup"><span data-stu-id="51562-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="51562-204">Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="51562-205">Libovolný počet `Exit Property` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="51562-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="51562-206">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="51562-206">**Return Value.**</span></span> <span data-ttu-id="51562-207">Chcete-li vrátit hodnotu z `Get` postup, můžete buď přiřadit hodnotu k názvu vlastnosti nebo ji zahrnout do příkazu `Return`.</span><span class="sxs-lookup"><span data-stu-id="51562-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="51562-208">Následující příklad přiřadí návratovou hodnotu k názvu vlastnosti `quoteForTheDay` a poté pomocí příkazu `Exit Property` vrátí.</span><span class="sxs-lookup"><span data-stu-id="51562-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="51562-209">Použijete-li `Exit Property` bez přiřazení hodnoty k `name`, `Get` procedura vrátí výchozí hodnotu pro datový typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51562-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="51562-210">Příkaz `Return` současně přiřadí návratovou hodnotu procedury `Get` a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="51562-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="51562-211">Následující příklad ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="51562-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="51562-212">Příklad</span><span class="sxs-lookup"><span data-stu-id="51562-212">Example</span></span>

<span data-ttu-id="51562-213">Následující příklad deklaruje vlastnost ve třídě.</span><span class="sxs-lookup"><span data-stu-id="51562-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="51562-214">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51562-214">See also</span></span>

- [<span data-ttu-id="51562-215">Automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="51562-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="51562-216">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="51562-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="51562-217">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="51562-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="51562-218">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="51562-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="51562-219">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="51562-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="51562-220">Default</span><span class="sxs-lookup"><span data-stu-id="51562-220">Default</span></span>](../modifiers/default.md)
