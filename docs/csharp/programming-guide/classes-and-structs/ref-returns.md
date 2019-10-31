---
title: Návratové hodnoty ref a lokální hodnoty REFC# (Průvodce)
description: Naučte se definovat a používat místní hodnoty Return a ref ref.
ms.date: 04/04/2018
ms.openlocfilehash: 99e0f9d995cf3bf5c0486415b6f2d578147d3c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114477"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="fea91-103">Návratové hodnoty podle odkazu a lokální proměnné podle odkazu</span><span class="sxs-lookup"><span data-stu-id="fea91-103">Ref returns and ref locals</span></span>

<span data-ttu-id="fea91-104">Počínaje C# 7,0 C# podporuje návratové hodnoty odkazů (vrátí ref).</span><span class="sxs-lookup"><span data-stu-id="fea91-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="fea91-105">Návratová hodnota odkazu umožňuje metodě vrátit odkaz na proměnnou, nikoli na hodnotu, zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fea91-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="fea91-106">Volající pak může zvolit, že se vrácená proměnná bude zacházet, jako kdyby byla vrácena hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="fea91-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="fea91-107">Volající může vytvořit novou proměnnou, která je sám odkazem na vrácenou hodnotu, která se nazývá ref Local.</span><span class="sxs-lookup"><span data-stu-id="fea91-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="fea91-108">Co je návratová hodnota odkazu?</span><span class="sxs-lookup"><span data-stu-id="fea91-108">What is a reference return value?</span></span>

<span data-ttu-id="fea91-109">Většina vývojářů je obeznámená s předáním argumentu s volanou metodou *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="fea91-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="fea91-110">Seznam argumentů volané metody obsahuje proměnnou předanou odkazem.</span><span class="sxs-lookup"><span data-stu-id="fea91-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="fea91-111">Všechny změny provedené v hodnotě volané metodou jsou pozorovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="fea91-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="fea91-112">*Návratová hodnota odkazu* znamená, že metoda vrátí *odkaz* (nebo alias) na určitou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="fea91-113">Rozsah této proměnné musí zahrnovat metodu.</span><span class="sxs-lookup"><span data-stu-id="fea91-113">That variable's scope must include the method.</span></span> <span data-ttu-id="fea91-114">Životnost této proměnné musí překračovat rámec návratové metody.</span><span class="sxs-lookup"><span data-stu-id="fea91-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="fea91-115">Změny návratové hodnoty metody volajícím jsou provedeny na proměnnou, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="fea91-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="fea91-116">Deklarace, že metoda vrátí *návratovou hodnotu odkazu* , označuje, že metoda vrací alias k proměnné.</span><span class="sxs-lookup"><span data-stu-id="fea91-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="fea91-117">Záměr návrhu je často, že volající kód by měl mít přístup k této proměnné prostřednictvím aliasu, včetně změny.</span><span class="sxs-lookup"><span data-stu-id="fea91-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="fea91-118">Tyto metody vracené odkazem nemohou mít návratový typ `void`.</span><span class="sxs-lookup"><span data-stu-id="fea91-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="fea91-119">Existují určitá omezení pro výraz, který metoda může vracet jako návratovou hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="fea91-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="fea91-120">Mezi omezení patří:</span><span class="sxs-lookup"><span data-stu-id="fea91-120">Restrictions include:</span></span>

- <span data-ttu-id="fea91-121">Návratová hodnota musí mít životnost, která překračuje provádění metody.</span><span class="sxs-lookup"><span data-stu-id="fea91-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="fea91-122">Jinými slovy nemůže být lokální proměnná v metodě, která ji vrací.</span><span class="sxs-lookup"><span data-stu-id="fea91-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="fea91-123">Může to být instance nebo statické pole třídy, nebo může být argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="fea91-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="fea91-124">Pokus o návrat lokální proměnné generuje chybu kompilátoru CS8168, "" nemůže vrátit místní "obj" odkazem, protože se nejedná o místní odkaz. "</span><span class="sxs-lookup"><span data-stu-id="fea91-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="fea91-125">Návratovou hodnotou nemůže být literální `null`.</span><span class="sxs-lookup"><span data-stu-id="fea91-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="fea91-126">Vrácení `null` generuje chybu kompilátoru CS8156; "výraz nelze v tomto kontextu použít, protože jej nelze vrátit odkazem."</span><span class="sxs-lookup"><span data-stu-id="fea91-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="fea91-127">Metoda s návratovým odkazem může vracet alias k proměnné, jejíž hodnota je aktuálně hodnotou null (bez instancí) nebo [typ hodnoty s možnou hodnotou null](../nullable-types/index.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fea91-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../nullable-types/index.md) for a value type.</span></span>

- <span data-ttu-id="fea91-128">Návratovou hodnotou nemůže být konstanta, člen výčtu, návratová hodnota po hodnotě z vlastnosti nebo metoda `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="fea91-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="fea91-129">Porušení tohoto pravidla generuje chybu kompilátoru CS8156. výraz nemůže být v tomto kontextu použit, protože jej nelze vrátit odkazem.</span><span class="sxs-lookup"><span data-stu-id="fea91-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="fea91-130">Kromě toho nejsou povoleny návratové hodnoty odkazů u asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="fea91-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="fea91-131">Asynchronní metoda může vracet před dokončením provádění, zatímco vrácená hodnota je stále neznámá.</span><span class="sxs-lookup"><span data-stu-id="fea91-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="fea91-132">Definování návratové hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="fea91-132">Defining a ref return value</span></span>

<span data-ttu-id="fea91-133">Metoda, která vrací *vrácenou hodnotu odkazu* , musí splňovat následující dvě podmínky:</span><span class="sxs-lookup"><span data-stu-id="fea91-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="fea91-134">Signatura metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="fea91-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="fea91-135">Každý příkaz [return](../../language-reference/keywords/return.md) v těle metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před název vrácené instance.</span><span class="sxs-lookup"><span data-stu-id="fea91-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="fea91-136">Následující příklad ukazuje metodu, která splňuje tyto podmínky a vrací odkaz na objekt `Person` s názvem `p`:</span><span class="sxs-lookup"><span data-stu-id="fea91-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="fea91-137">Využívání návratové hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="fea91-137">Consuming a ref return value</span></span>

<span data-ttu-id="fea91-138">Návratová hodnota REF je alias jiné proměnné v oboru volané metody.</span><span class="sxs-lookup"><span data-stu-id="fea91-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="fea91-139">Můžete interpretovat jakékoli použití parametru REF jako pomocí proměnné aliasy IT:</span><span class="sxs-lookup"><span data-stu-id="fea91-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="fea91-140">Pokud přiřadíte jeho hodnotu, přiřadíte jí hodnotu proměnné, které aliasuje.</span><span class="sxs-lookup"><span data-stu-id="fea91-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="fea91-141">Při čtení hodnoty se čte hodnota proměnné, které aliasuje.</span><span class="sxs-lookup"><span data-stu-id="fea91-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="fea91-142">Pokud ho vrátíte *odkazem*, vracíte alias pro stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="fea91-143">Pokud je předáte do jiné metody *odkazem*, předáváte odkaz na proměnnou, kterou aliasuje.</span><span class="sxs-lookup"><span data-stu-id="fea91-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="fea91-144">Při vytváření [referenčního místního](#ref-locals) aliasu je třeba vytvořit nový alias pro stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="fea91-145">Lokální hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="fea91-145">Ref locals</span></span>

<span data-ttu-id="fea91-146">Předpokládat, že metoda `GetContactInformation` je deklarovaná jako ref Return:</span><span class="sxs-lookup"><span data-stu-id="fea91-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="fea91-147">Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji k nové proměnné:</span><span class="sxs-lookup"><span data-stu-id="fea91-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="fea91-148">Předchozí přiřazení deklaruje `p` jako místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="fea91-149">Počáteční hodnota je zkopírována z čtení hodnoty vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="fea91-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="fea91-150">Jakákoli budoucí přiřazení `p` nemění hodnotu proměnné vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="fea91-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="fea91-151">Proměnná `p` již není aliasem pro vrácenou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="fea91-152">Deklaraci *místní proměnné ref* můžete pro zkopírování aliasu na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fea91-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="fea91-153">V následujícím přiřazení je `p` alias pro proměnnou vrácenou z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="fea91-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="fea91-154">Následné použití `p` je stejné jako použití proměnné vrácené `GetContactInformation`, protože `p` je alias pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fea91-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="fea91-155">Změny `p` také mění proměnnou vrácenou z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="fea91-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="fea91-156">Klíčové slovo `ref` se používá před deklarací místní proměnné *a* před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="fea91-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="fea91-157">K hodnotě můžete přistupovat stejným způsobem pomocí odkazu.</span><span class="sxs-lookup"><span data-stu-id="fea91-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="fea91-158">V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="fea91-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="fea91-159">Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fea91-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="fea91-160">Klíčové slovo `ref` se používá před deklarací místní proměnné *a* před hodnotou v druhém příkladu.</span><span class="sxs-lookup"><span data-stu-id="fea91-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="fea91-161">Nepovedlo se zahrnout klíčová slova `ref` v deklaraci proměnné a přiřazení v obou příkladech způsobí chybu kompilátoru CS8172. "nemůže inicializovat proměnnou podle odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="fea91-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="fea91-162">Před C# 7,3 se nepovedlo znovu přiřadit místní proměnné ref, aby se po inicializaci odkazovaly na jiné úložiště.</span><span class="sxs-lookup"><span data-stu-id="fea91-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="fea91-163">Toto omezení bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="fea91-163">That restriction has been removed.</span></span> <span data-ttu-id="fea91-164">Následující příklad ukazuje změnu přiřazení:</span><span class="sxs-lookup"><span data-stu-id="fea91-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="fea91-165">Místní proměnné ref musí být při deklarování stále inicializovány.</span><span class="sxs-lookup"><span data-stu-id="fea91-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="fea91-166">Návratové hodnoty ref a lokální hodnoty REF: příklad</span><span class="sxs-lookup"><span data-stu-id="fea91-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="fea91-167">Následující příklad definuje třídu `NumberStore`, která ukládá pole celočíselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="fea91-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="fea91-168">Metoda `FindNumber` vrací odkazem na první číslo, které je větší než nebo rovno číslu předanému jako argument.</span><span class="sxs-lookup"><span data-stu-id="fea91-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="fea91-169">Pokud číslo není větší než nebo rovno argumentu, vrátí metoda číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="fea91-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="fea91-170">Následující příklad volá metodu `NumberStore.FindNumber` pro načtení první hodnoty, která je větší nebo rovna 16.</span><span class="sxs-lookup"><span data-stu-id="fea91-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="fea91-171">Volající pak zdvojnásobí hodnotu vrácenou metodou.</span><span class="sxs-lookup"><span data-stu-id="fea91-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="fea91-172">Výstup z příkladu ukazuje změnu odrážející se v hodnotě prvků pole instance `NumberStore`.</span><span class="sxs-lookup"><span data-stu-id="fea91-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="fea91-173">Bez podpory návratových hodnot odkazů je taková operace provedena vrácením indexu prvku pole spolu s jeho hodnotou.</span><span class="sxs-lookup"><span data-stu-id="fea91-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="fea91-174">Volající pak může použít tento index k úpravě hodnoty v samostatném volání metody.</span><span class="sxs-lookup"><span data-stu-id="fea91-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="fea91-175">Volající však může také změnit index k přístupu a případně upravit jiné hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="fea91-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="fea91-176">Následující příklad ukazuje, jak může být metoda `FindNumber` přepsána po C# 7,3 pro použití místního opětovného přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="fea91-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="fea91-177">Tato druhá verze je efektivnější s delšími sekvencemi ve scénářích, kde se hledané číslo blíží konci pole.</span><span class="sxs-lookup"><span data-stu-id="fea91-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="fea91-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fea91-178">See also</span></span>

- [<span data-ttu-id="fea91-179">ref – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="fea91-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="fea91-180">Zapisovat bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="fea91-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
