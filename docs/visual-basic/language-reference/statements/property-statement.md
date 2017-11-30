---
title: "Property – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af4666ecb059f141480be2295055644537819293
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property-statement"></a><span data-ttu-id="836df-102">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="836df-102">Property Statement</span></span>
<span data-ttu-id="836df-103">Deklaruje název vlastnosti a vlastnosti postupy používají k ukládání a načítání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="836df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="836df-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="836df-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="836df-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="836df-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-106">Optional.</span></span> <span data-ttu-id="836df-107">Seznam atributů, které platí pro tuto vlastnost nebo `Get` nebo `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="836df-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="836df-108">V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="836df-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="836df-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-109">Optional.</span></span> <span data-ttu-id="836df-110">Určuje, že je tato vlastnost Výchozí vlastnost pro třídu nebo strukturu, na kterém je definovaný.</span><span class="sxs-lookup"><span data-stu-id="836df-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="836df-111">Výchozí vlastnosti musí přijmout parametry a může být nastavit a načíst bez zadání názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="836df-112">Pokud je deklarovat vlastnost jako `Default`, nemůžete použít `Private` na vlastnost nebo na některý z jeho procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="836df-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="836df-113">Volitelné na `Property` příkaz a na maximálně jedno z `Get` a `Set` příkazy.</span><span class="sxs-lookup"><span data-stu-id="836df-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="836df-114">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="836df-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="836df-115">Veřejné</span><span class="sxs-lookup"><span data-stu-id="836df-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="836df-116">Chráněný</span><span class="sxs-lookup"><span data-stu-id="836df-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="836df-117">Friend</span><span class="sxs-lookup"><span data-stu-id="836df-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="836df-118">Privátní</span><span class="sxs-lookup"><span data-stu-id="836df-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="836df-119">V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="836df-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="836df-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-120">Optional.</span></span> <span data-ttu-id="836df-121">Může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="836df-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="836df-122">Přetížení</span><span class="sxs-lookup"><span data-stu-id="836df-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="836df-123">Přepsání</span><span class="sxs-lookup"><span data-stu-id="836df-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="836df-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="836df-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="836df-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="836df-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="836df-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="836df-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="836df-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-127">Optional.</span></span> <span data-ttu-id="836df-128">V tématu [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="836df-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="836df-129">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-129">Optional.</span></span> <span data-ttu-id="836df-130">V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="836df-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="836df-131">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-131">Optional.</span></span> <span data-ttu-id="836df-132">V tématu [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="836df-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="836df-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-133">Optional.</span></span> <span data-ttu-id="836df-134">V tématu [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="836df-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="836df-135">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-135">Optional.</span></span> <span data-ttu-id="836df-136">V tématu [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="836df-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="836df-137">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="836df-137">Required.</span></span> <span data-ttu-id="836df-138">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="836df-138">Name of the property.</span></span> <span data-ttu-id="836df-139">V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="836df-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="836df-140">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-140">Optional.</span></span> <span data-ttu-id="836df-141">Seznam představující parametry této vlastnosti a možné další parametry místní názvy proměnných `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="836df-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="836df-142">V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="836df-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="836df-143">Požadováno pokud `Option``Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="836df-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="836df-144">Datový typ hodnoty vrácené tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="836df-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="836df-145">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-145">Optional.</span></span> <span data-ttu-id="836df-146">Označuje, že tato vlastnost implementuje jednu nebo více vlastností, každé z nich definované v rozhraní implementované obsahující třídu nebo strukturu tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="836df-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="836df-147">V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="836df-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="836df-148">Požadováno pokud `Implements` pochází.</span><span class="sxs-lookup"><span data-stu-id="836df-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="836df-149">Seznam vlastností se implementuje.</span><span class="sxs-lookup"><span data-stu-id="836df-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="836df-150">Každý `implementedproperty` má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="836df-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="836df-151">Část</span><span class="sxs-lookup"><span data-stu-id="836df-151">Part</span></span>|<span data-ttu-id="836df-152">Popis</span><span class="sxs-lookup"><span data-stu-id="836df-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="836df-153">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="836df-153">Required.</span></span> <span data-ttu-id="836df-154">Název rozhraní implementované tato vlastnost obsahující třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="836df-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="836df-155">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="836df-155">Required.</span></span> <span data-ttu-id="836df-156">Název, podle kterého je vlastnost definována v `interface`.</span><span class="sxs-lookup"><span data-stu-id="836df-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="836df-157">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-157">Optional.</span></span> <span data-ttu-id="836df-158">Vyžaduje, pokud je vlastnost označena `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="836df-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="836df-159">Spustí `Get` procedury vlastnosti, která se používá k vrácení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="836df-160">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-160">Optional.</span></span> <span data-ttu-id="836df-161">Blok příkazů ke spuštění v rámci `Get` nebo `Set` postupu.</span><span class="sxs-lookup"><span data-stu-id="836df-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="836df-162">Ukončí `Get` procedura property.</span><span class="sxs-lookup"><span data-stu-id="836df-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="836df-163">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="836df-163">Optional.</span></span> <span data-ttu-id="836df-164">Vyžaduje, pokud je vlastnost označena `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="836df-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="836df-165">Spustí `Set` procedury vlastnosti, která se používá k ukládání hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="836df-166">Ukončí `Set` procedura property.</span><span class="sxs-lookup"><span data-stu-id="836df-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="836df-167">Ukončí definici této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="836df-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="836df-168">Remarks</span></span>  
 <span data-ttu-id="836df-169">`Property` Příkaz zavádí deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="836df-170">Může mít vlastnost `Get` postupu (jen pro čtení), `Set` procedura (pouze pro zápis) nebo obě (pro čtení a zápis).</span><span class="sxs-lookup"><span data-stu-id="836df-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="836df-171">Můžete vynechat `Get` a `Set` procedury při použití ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="836df-172">Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="836df-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="836df-173">Můžete použít `Property` jenom na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="836df-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="836df-174">To znamená *deklarace kontextu* pro vlastnost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, postup nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="836df-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="836df-175">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="836df-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="836df-176">Ve výchozím nastavení použijte vlastnosti veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="836df-176">By default, properties use public access.</span></span> <span data-ttu-id="836df-177">Úroveň přístupu vlastnosti s – modifikátor přístupu můžete upravit na `Property` příkaz a můžete případně upravit jeden z jeho vlastnost postupů k více omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="836df-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="836df-178">Parametr, který se předá jazyka Visual Basic `Set` postup při přiřazení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="836df-179">Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`.</span><span class="sxs-lookup"><span data-stu-id="836df-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="836df-180">Tento parametr obsahuje hodnota, která má být přiřazeno k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="836df-181">Obvykle uložte tuto hodnotu v privátní místní proměnné a obnoví v něm vždy, když `Get` procedura je volána.</span><span class="sxs-lookup"><span data-stu-id="836df-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="836df-182">Pravidla</span><span class="sxs-lookup"><span data-stu-id="836df-182">Rules</span></span>  
  
-   <span data-ttu-id="836df-183">**Smíšenými úrovněmi přístupu.**</span><span class="sxs-lookup"><span data-stu-id="836df-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="836df-184">Pokud definujete vlastnost pro čtení a zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="836df-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="836df-185">Pokud to uděláte, musí být úroveň přístupu postup více omezující než úroveň přístupu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="836df-186">Například, pokud je deklarovaná vlastnost `Friend`, můžou deklarovat `Set` postup `Private`, ale ne `Public`.</span><span class="sxs-lookup"><span data-stu-id="836df-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="836df-187">Pokud definujete `ReadOnly` nebo `WriteOnly` vlastnost, postup jedinou vlastností (`Get` nebo `Set`, v uvedeném pořadí) představuje všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="836df-188">Vzhledem k tomu, který se nastavuje dvě úrovně přístupu pro vlastnost nelze deklarovat různý přístup úroveň pro tento postup.</span><span class="sxs-lookup"><span data-stu-id="836df-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="836df-189">**Návratový typ.**</span><span class="sxs-lookup"><span data-stu-id="836df-189">**Return Type.**</span></span> <span data-ttu-id="836df-190">`Property` Příkaz můžou deklarovat datový typ hodnoty, vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="836df-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="836df-191">Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="836df-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="836df-192">Pokud nezadáte `returntype`, vrátí vlastnost `Object`.</span><span class="sxs-lookup"><span data-stu-id="836df-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="836df-193">**Implementace.**</span><span class="sxs-lookup"><span data-stu-id="836df-193">**Implementation.**</span></span> <span data-ttu-id="836df-194">Pokud tuto vlastnost používá `Implements` – klíčové slovo, obsahující třídu nebo strukturu, musíte mít `Implements` bezprostředně za jeho `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="836df-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="836df-195">`Implements` Příkaz musí zahrnovat každé rozhraní zadaný v `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="836df-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="836df-196">Ale název, podle kterého rozhraní definuje `Property` (v `definedname`) nemusí být stejný jako název této vlastnosti (v `name`).</span><span class="sxs-lookup"><span data-stu-id="836df-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="836df-197">Chování</span><span class="sxs-lookup"><span data-stu-id="836df-197">Behavior</span></span>  
  
-   <span data-ttu-id="836df-198">**Vrácení z procedury vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="836df-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="836df-199">Když `Get` nebo `Set` postup vrátí kód volání, provádění pokračuje s příkazem následující příkaz, která je volána.</span><span class="sxs-lookup"><span data-stu-id="836df-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="836df-200">`Exit Property` a `Return` příkazy způsobí okamžité ukončení z procedury vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="836df-201">Libovolný počet `Exit Property` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.</span><span class="sxs-lookup"><span data-stu-id="836df-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="836df-202">**Vrátí hodnotu.**</span><span class="sxs-lookup"><span data-stu-id="836df-202">**Return Value.**</span></span> <span data-ttu-id="836df-203">Vrácení hodnoty z `Get` postup, můžete přiřadit hodnotu pro název vlastnosti nebo ji v zahrnout `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="836df-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="836df-204">Následující příklad přiřadí návratovou hodnotu pro název vlastnosti `quoteForTheDay` a použije je `Exit Property` příkaz, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="836df-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="836df-205">Pokud používáte `Exit Property` bez přiřazení hodnoty k `name`, `Get` postup vrátí výchozí hodnota pro typ dat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="836df-205">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="836df-206">`Return` Příkaz ve stejnou dobu přiřazuje `Get` postup vracet hodnotu a ukončí proceduru.</span><span class="sxs-lookup"><span data-stu-id="836df-206">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="836df-207">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="836df-207">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="836df-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="836df-208">Example</span></span>  
 <span data-ttu-id="836df-209">Následující příklad deklaruje vlastnost v třídě.</span><span class="sxs-lookup"><span data-stu-id="836df-209">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="836df-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="836df-210">See Also</span></span>  
 [<span data-ttu-id="836df-211">Automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="836df-211">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="836df-212">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="836df-212">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="836df-213">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="836df-213">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="836df-214">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="836df-214">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="836df-215">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="836df-215">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="836df-216">Výchozí</span><span class="sxs-lookup"><span data-stu-id="836df-216">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
