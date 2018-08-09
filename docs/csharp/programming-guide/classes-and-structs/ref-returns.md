---
title: Návratové hodnoty REF a místní referenční hodnoty (Průvodce v C#)
description: Zjistěte, jak definovat a používat ref návratové a místní hodnoty ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e749b9c9309a4b1a737a0c1d0b5e1cfe5748114a
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "33339615"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="ee3f9-103">Návratové a místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="ee3f9-103">Ref returns and ref locals</span></span>

<span data-ttu-id="ee3f9-104">Od verze C# 7.0, C# podporuje referenční návratové hodnoty (ref vrátí).</span><span class="sxs-lookup"><span data-stu-id="ee3f9-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="ee3f9-105">Odkaz na návratové hodnoty umožňuje metody, která vrátí odkaz na proměnnou, nikoli hodnotu, zpět do volajícího.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="ee3f9-106">Volající pak můžete přistupovat ke všem vrácené proměnnou, jako by byly vráceny hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="ee3f9-107">Volající může vytvořit odkaz na vrácené hodnoty ref volá místní novou proměnnou, která sama o sobě.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="ee3f9-108">Co je návratová hodnota odkaz?</span><span class="sxs-lookup"><span data-stu-id="ee3f9-108">What is a reference return value?</span></span>

<span data-ttu-id="ee3f9-109">Většina vývojářů znají předání argumentu do volané metody *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="ee3f9-110">Seznam argumentů volané metody obsahuje proměnnou předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="ee3f9-111">Změny provedené na hodnotu ve volané metody jsou dodržovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="ee3f9-112">A *odkazovat na návratovou hodnotu* znamená, že metoda vrátí *odkaz* (nebo alias) některé proměnné.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="ee3f9-113">Tato proměnná rozsahu musí zahrnovat metodu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-113">That variable's scope must include the method.</span></span> <span data-ttu-id="ee3f9-114">Tato proměnná životnost musí přesahovat vrácení metody.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="ee3f9-115">Návratovou hodnotu metody volající změn do proměnné, který je vrácen touto metodou.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="ee3f9-116">Deklarace, která vrací metoda *odkazovat na návratovou hodnotu* označuje, že metoda vrací alias na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="ee3f9-117">Návrh záměr je často, že volající kód mají mít přístup k této proměnné prostřednictvím alias, včetně jej upravit.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="ee3f9-118">Vyplývá, že metody vracející odkaz nemůže mít návratový typ `void`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="ee3f9-119">Platí určitá omezení na výraz, který metoda může vrátit jako návratovou hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="ee3f9-120">Omezení patří:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-120">Restrictions include:</span></span>

- <span data-ttu-id="ee3f9-121">Vrácená hodnota musí mít životností, která se rozpíná za provádění metody.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="ee3f9-122">Jinými slovy nemůže být lokální proměnná v metodě, která vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="ee3f9-123">Může se jednat instance nebo statické pole třídy, nebo může být argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="ee3f9-124">Pokus o vrácení, že místní proměnná vygeneruje Chyba kompilátoru CS8168, "nejde vrátit místní"obj"podle odkazu protože se nejedná o lokální proměnnou."</span><span class="sxs-lookup"><span data-stu-id="ee3f9-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="ee3f9-125">Návratová hodnota nemůže být literál `null`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="ee3f9-126">Vrací `null` vygeneruje Chyba kompilátoru CS8156 "výraz nelze použít v tomto kontextu, protože nemusí být vrácená odkazem."</span><span class="sxs-lookup"><span data-stu-id="ee3f9-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="ee3f9-127">Metoda s ref návratový může vrátit alias na proměnnou, jehož hodnota je aktuálně hodnotu null (nevytvořeným instancím) nebo [typ připouštějící hodnotu Null](../nullable-types/index.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="ee3f9-128">Návratová hodnota nemůže být konstantní, člen výčtového typu, podle hodnoty vrátí hodnotu z vlastnosti nebo metody `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="ee3f9-129">Porušení tohoto pravidla vygeneruje Chyba kompilátoru CS8156 "výraz nelze použít v tomto kontextu, protože nemusí být vrácená odkazem."</span><span class="sxs-lookup"><span data-stu-id="ee3f9-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="ee3f9-130">Kromě toho referenční návratové hodnoty nejsou povoleny v asynchronních metodách.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="ee3f9-131">Asynchronní metoda může vrátit předtím, než se dokončí provádění, vrácená hodnota je stále neznámý.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="ee3f9-132">Definování návratová hodnota ref.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-132">Defining a ref return value</span></span>

<span data-ttu-id="ee3f9-133">Metoda, která vrátí *odkazovat na návratovou hodnotu* musí splňovat tyto dvě podmínky:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="ee3f9-134">Podpis metody zahrnuje [ref](../../language-reference/keywords/ref.md) – klíčové slovo před návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="ee3f9-135">Každý [vrátit](../../language-reference/keywords/return.md) zahrnuje příkaz v těle metody [ref](../../language-reference/keywords/ref.md) – klíčové slovo před název vrácená instance.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="ee3f9-136">Následující příklad ukazuje metodu, která splňuje tyto podmínky a vrátí odkaz na `Person` objekt s názvem `p`:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="ee3f9-137">Využívání návratová hodnota ref.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-137">Consuming a ref return value</span></span>

<span data-ttu-id="ee3f9-138">Ref návratové hodnoty je alias pro jiné proměnné v oboru volané metody.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="ee3f9-139">Lze interpretovat jakékoli využití návratový ref jako pomocí proměnné ho aliasy:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="ee3f9-140">Když přiřadíte její hodnotu, jsou přiřazení hodnoty proměnné ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="ee3f9-141">Při čtení jeho hodnotu při čtení hodnota proměnné je aliasy.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="ee3f9-142">Je-li se vrátit *odkazem*, alias se vrátí na tuto proměnnou stejné.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="ee3f9-143">Pokud předáte jiný způsob *odkazem*, jsou předáním odkazu na proměnnou je aliasy.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="ee3f9-144">Je-li [lokální proměnná podle odkazu](#ref-local) alias, můžete vytvořit nový alias u stejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="ee3f9-145">Místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="ee3f9-145">Ref locals</span></span>

<span data-ttu-id="ee3f9-146">Předpokládá `GetContactInformation` metoda je deklarován jako ref vrácení:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="ee3f9-147">Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji nové proměnné:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="ee3f9-148">Deklaruje předchozí přiřazení `p` jako místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="ee3f9-149">Počáteční hodnoty je zkopírován z čtení hodnoty vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="ee3f9-150">Všechny budoucí přiřazení `p` nedojde ke změně hodnoty proměnné vrácený `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="ee3f9-151">Proměnná `p` už není alias proměnné vrácen.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="ee3f9-152">Deklarujete *lokální proměnná podle odkazu* proměnnou ke zkopírování alias na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="ee3f9-153">V následující přiřazení `p` se alias pro proměnnou vrácená `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="ee3f9-154">Další využití `p` je stejný jako pomocí proměnné vrácený `GetContactInformation` protože `p` je alias pro danou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="ee3f9-155">Změny `p` také změnit proměnnou vrácená `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="ee3f9-156">`ref` Klíčové slovo se používá i před deklarace lokální proměnné *a* před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="ee3f9-157">Stejným způsobem můžete přistupovat hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="ee3f9-158">V některých případech se přístup k hodnota podle odkazu zvyšuje výkon se vyhnout operaci kopírování potenciálně nákladné.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="ee3f9-159">Následující příkaz například ukazuje, jak jeden můžete definovat, který se používá k odkazování hodnotu lokální hodnota ref.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="ee3f9-160">`ref` Klíčové slovo se používá i před deklarace lokální proměnné *a* před hodnotu v druhém příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="ee3f9-161">Selhání oba `ref` klíčová slova v deklaraci proměnné a přiřazení v obou příkladech vede k chybě kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="ee3f9-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="ee3f9-162">Před C# 7.3 místní proměnné odkazu nelze přiřadit k odkazování na jiného úložiště po jejich inicializaci.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="ee3f9-163">Odebrali jsme omezení.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-163">That restriction has been removed.</span></span> <span data-ttu-id="ee3f9-164">Následující příklad ukazuje změnu přiřazení:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="ee3f9-165">Místní proměnné odkazu musí být stále inicializován, pokud jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="ee3f9-166">Návratové a místní referenční hodnoty: příklad</span><span class="sxs-lookup"><span data-stu-id="ee3f9-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="ee3f9-167">Následující příklad definuje `NumberStore` třída, která obsahuje pole celočíselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="ee3f9-168">`FindNumber` Metoda vrací odkazem. první číslo, které je větší než nebo rovno počtu předán jako argument.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="ee3f9-169">Pokud číslo je větší než nebo rovna hodnotě argumentu, metoda vrátí číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="ee3f9-170">Následující příklad volá `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="ee3f9-171">Volající pak zdvojnásobuje hodnota vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="ee3f9-172">Výstup z příkladu ukazuje změnu v hodnotě pole prvků `NumberStore` instance.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="ee3f9-173">Bez podpory pro referenční návratové hodnoty tato operace se provádí tak, že vrací index prvku pole společně s jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="ee3f9-174">Volající pak můžete použít tento index ke změně hodnoty v samostatné metodě volání.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="ee3f9-175">Volající však můžete také upravit index pro přístup k a případně upravit další hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="ee3f9-176">Následující příklad ukazuje způsob, jakým `FindNumber` metody by mohla být přepsána za C# 7.3 používat místní opětovné přiřazení odkazu:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="ee3f9-177">Tento druhý verze je mnohem efektivnější s delší pořadí ve scénářích, kde číslo žádá o blíž ke konci pole.</span><span class="sxs-lookup"><span data-stu-id="ee3f9-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee3f9-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee3f9-178">See also</span></span>

[<span data-ttu-id="ee3f9-179">REF – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="ee3f9-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="ee3f9-180">Referenční sémantika s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="ee3f9-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
