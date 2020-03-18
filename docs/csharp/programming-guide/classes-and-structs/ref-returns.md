---
title: Ref vrácené hodnoty a místní ref (C# Guide)
description: Naučte se definovat a používat ref return a ref místní hodnoty
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170070"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="618a2-103">Návratové hodnoty podle odkazu a lokální proměnné podle odkazu</span><span class="sxs-lookup"><span data-stu-id="618a2-103">Ref returns and ref locals</span></span>

<span data-ttu-id="618a2-104">Počínaje C# 7.0, C# podporuje referenční vrácené hodnoty (ref vrátí).</span><span class="sxs-lookup"><span data-stu-id="618a2-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="618a2-105">Vrácená hodnota odkazu umožňuje metodu vrátit odkaz na proměnnou, nikoli hodnotu, zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="618a2-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="618a2-106">Volající pak můžete zvolit léčbu vrácené proměnné, jako kdyby byly vráceny podle hodnoty nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="618a2-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="618a2-107">Volající může vytvořit novou proměnnou, která je sama odkaz na vrácenou hodnotu, nazývanou ref local.</span><span class="sxs-lookup"><span data-stu-id="618a2-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="618a2-108">Co je referenční vrácená hodnota?</span><span class="sxs-lookup"><span data-stu-id="618a2-108">What is a reference return value?</span></span>

<span data-ttu-id="618a2-109">Většina vývojářů je obeznámena s předáním argumentu volané *metodě odkazem*.</span><span class="sxs-lookup"><span data-stu-id="618a2-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="618a2-110">Seznam argumentů volané metody obsahuje proměnnou předanou odkazem.</span><span class="sxs-lookup"><span data-stu-id="618a2-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="618a2-111">Všechny změny provedené v jeho hodnotě volanou metodou jsou sledovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="618a2-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="618a2-112">Referenční *vrácená hodnota* znamená, že metoda vrátí *odkaz* (nebo alias) na nějakou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="618a2-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="618a2-113">Rozsah této proměnné musí obsahovat metodu.</span><span class="sxs-lookup"><span data-stu-id="618a2-113">That variable's scope must include the method.</span></span> <span data-ttu-id="618a2-114">Životnost této proměnné musí přesahovat vrácení metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="618a2-115">Změny návratové hodnoty metody volajícím jsou provedeny na proměnnou, která je vrácena metodou.</span><span class="sxs-lookup"><span data-stu-id="618a2-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="618a2-116">Deklarování, že metoda vrátí *referenční vrácená hodnota* označuje, že metoda vrátí alias proměnné.</span><span class="sxs-lookup"><span data-stu-id="618a2-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="618a2-117">Záměr návrhu je často, že volající kód by měl mít přístup k této proměnné prostřednictvím aliasu, včetně jeho úpravy.</span><span class="sxs-lookup"><span data-stu-id="618a2-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="618a2-118">Z toho vyplývá, že metody vracející se `void`odkazem nemůže mít návratový typ .</span><span class="sxs-lookup"><span data-stu-id="618a2-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="618a2-119">Existují určitá omezení výrazu, který může metoda vrátit jako referenční vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="618a2-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="618a2-120">Omezení zahrnují:</span><span class="sxs-lookup"><span data-stu-id="618a2-120">Restrictions include:</span></span>

- <span data-ttu-id="618a2-121">Vrácená hodnota musí mít životnost, která přesahuje provádění metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="618a2-122">Jinými slovy nemůže být místní proměnnou v metodě, která ji vrací.</span><span class="sxs-lookup"><span data-stu-id="618a2-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="618a2-123">Může se jedná o instanci nebo statické pole třídy nebo může být argumentem předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="618a2-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="618a2-124">Pokus o vrácení místní proměnné generuje chybu kompilátoru CS8168, "Nelze vrátit místní obj' odkazem, protože není ref místní."</span><span class="sxs-lookup"><span data-stu-id="618a2-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="618a2-125">Vrácená hodnota nemůže být `null`literál .</span><span class="sxs-lookup"><span data-stu-id="618a2-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="618a2-126">Vrácení `null` generuje chybu kompilátoru CS8156, "Výraz nelze použít v tomto kontextu, protože nemusí být vrácena odkazem."</span><span class="sxs-lookup"><span data-stu-id="618a2-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="618a2-127">Metoda s návratem ref může vrátit alias proměnné, jejíž hodnota je aktuálně hodnota null (uninstantiated) nebo [typ hodnoty s možnou hodnotou s možnou hodnotou](../../language-reference/builtin-types/nullable-value-types.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="618a2-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../../language-reference/builtin-types/nullable-value-types.md) for a value type.</span></span>

- <span data-ttu-id="618a2-128">Vrácená hodnota nemůže být konstanta, člen výčtu, vrácená hodnota podle hodnoty `class` z `struct`vlastnosti nebo metoda a nebo .</span><span class="sxs-lookup"><span data-stu-id="618a2-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="618a2-129">Porušení tohoto pravidla generuje chybu kompilátoru CS8156, "Výraz nelze použít v tomto kontextu, protože nemusí být vrácena odkazem."</span><span class="sxs-lookup"><span data-stu-id="618a2-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="618a2-130">Kromě toho referenční vrácené hodnoty nejsou povoleny na asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="618a2-131">Asynchronní metoda může vrátit před dokončením spuštění, zatímco jeho vrácená hodnota je stále neznámý.</span><span class="sxs-lookup"><span data-stu-id="618a2-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="618a2-132">Definování vrácené hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="618a2-132">Defining a ref return value</span></span>

<span data-ttu-id="618a2-133">Metoda, která vrací *referenční vrácenou hodnotu,* musí splňovat následující dvě podmínky:</span><span class="sxs-lookup"><span data-stu-id="618a2-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="618a2-134">Podpis metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="618a2-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="618a2-135">Každý [příkaz return](../../language-reference/keywords/return.md) v těle metody obsahuje klíčové slovo [ref](../../language-reference/keywords/ref.md) před názvem vrácené instance.</span><span class="sxs-lookup"><span data-stu-id="618a2-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="618a2-136">Následující příklad ukazuje metodu, která splňuje tyto podmínky `Person` a `p`vrátí odkaz na objekt s názvem :</span><span class="sxs-lookup"><span data-stu-id="618a2-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="618a2-137">Spotřeba vrácené hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="618a2-137">Consuming a ref return value</span></span>

<span data-ttu-id="618a2-138">Vrácená hodnota ref je alias jiné proměnné v oboru volané metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="618a2-139">Jakékoli použití ref return můžete interpretovat jako použití proměnné, kterou aliasuje:</span><span class="sxs-lookup"><span data-stu-id="618a2-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="618a2-140">Když přiřadíte její hodnotu, přiřazujete hodnotu proměnné, kterou aliasuje.</span><span class="sxs-lookup"><span data-stu-id="618a2-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="618a2-141">Při čtení jeho hodnoty čtete hodnotu proměnné, kterou aliasuje.</span><span class="sxs-lookup"><span data-stu-id="618a2-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="618a2-142">Pokud jej vrátíte *odkazem*, vracíte alias stejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="618a2-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="618a2-143">Pokud ji předáte jiné metodě *odkazem*, předáváte odkaz na proměnnou, kterou aliasuje.</span><span class="sxs-lookup"><span data-stu-id="618a2-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="618a2-144">Když vytvoříte místní alias [ref,](#ref-locals) vytvoříte nový alias pro stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="618a2-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="618a2-145">Ref místní obyvatelé</span><span class="sxs-lookup"><span data-stu-id="618a2-145">Ref locals</span></span>

<span data-ttu-id="618a2-146">Předpokládejme, `GetContactInformation` že metoda je deklarována jako ref return:</span><span class="sxs-lookup"><span data-stu-id="618a2-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="618a2-147">Přiřazení podle hodnoty přečte hodnotu proměnné a přiřadí ji k nové proměnné:</span><span class="sxs-lookup"><span data-stu-id="618a2-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="618a2-148">Předchozí přiřazení deklaruje `p` jako místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="618a2-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="618a2-149">Jeho počáteční hodnota je zkopírována ze čtení hodnoty vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="618a2-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="618a2-150">Žádná budoucí přiřazení `p` nezmění hodnotu proměnné vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="618a2-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="618a2-151">Proměnná `p` již není alias proměnné vrácené.</span><span class="sxs-lookup"><span data-stu-id="618a2-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="618a2-152">Deklarujete místní proměnnou *ref* pro kopírování aliasu na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="618a2-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="618a2-153">V následujícím přiřazení `p` je alias proměnné vrácené z `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="618a2-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="618a2-154">Následné použití `p` je stejné jako použití `GetContactInformation` proměnné `p` vrácené, protože je alias pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="618a2-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="618a2-155">Změní `p` také změnu proměnné `GetContactInformation`vrácené z .</span><span class="sxs-lookup"><span data-stu-id="618a2-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="618a2-156">Klíčové `ref` slovo se používá jak před *deklarací* místní proměnné, tak před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span>

<span data-ttu-id="618a2-157">Můžete přistupovat k hodnotě odkazem stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="618a2-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="618a2-158">V některých případech přístup k hodnotě odkazem zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="618a2-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="618a2-159">Například následující příkaz ukazuje, jak lze definovat ref místní hodnotu, která se používá k odkazu na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="618a2-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="618a2-160">Klíčové `ref` slovo se používá jak před *deklarací* místní proměnné, tak před hodnotou v druhém příkladu.</span><span class="sxs-lookup"><span data-stu-id="618a2-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="618a2-161">Pokud nezahrnete obě `ref` klíčová slova do deklarace proměnné a přiřazení v obou příkladech, výsledkem je chyba kompilátoru CS8172, "Nelze inicializovat proměnnou odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="618a2-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="618a2-162">Před C# 7.3 ref místní proměnné nelze znovu přiřadit odkazovat na různé úložiště po inicializování.</span><span class="sxs-lookup"><span data-stu-id="618a2-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="618a2-163">Toto omezení bylo odstraněno.</span><span class="sxs-lookup"><span data-stu-id="618a2-163">That restriction has been removed.</span></span> <span data-ttu-id="618a2-164">Následující příklad ukazuje přeřazení:</span><span class="sxs-lookup"><span data-stu-id="618a2-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="618a2-165">Ref místní proměnné musí být stále inicializovány, když jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="618a2-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="618a2-166">Ref vrátí a ref místní: příklad</span><span class="sxs-lookup"><span data-stu-id="618a2-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="618a2-167">Následující příklad definuje `NumberStore` třídu, která ukládá pole celé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="618a2-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="618a2-168">Metoda `FindNumber` vrátí odkazem na první číslo, které je větší nebo rovno číslo předáno jako argument.</span><span class="sxs-lookup"><span data-stu-id="618a2-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="618a2-169">Pokud žádné číslo je větší než nebo rovno argument, metoda vrátí číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="618a2-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="618a2-170">Následující příklad volá `NumberStore.FindNumber` metodu k načtení první hodnoty, která je větší nebo rovna 16.</span><span class="sxs-lookup"><span data-stu-id="618a2-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="618a2-171">Volající pak zdvojnásobí hodnotu vrácenou metodou.</span><span class="sxs-lookup"><span data-stu-id="618a2-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="618a2-172">Výstup z příkladu ukazuje změnu, která se odráží `NumberStore` v hodnotě prvků pole instance.</span><span class="sxs-lookup"><span data-stu-id="618a2-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="618a2-173">Bez podpory pro referenční vrácené hodnoty, taková operace se provádí vrácením indexu prvku pole spolu s jeho hodnotou.</span><span class="sxs-lookup"><span data-stu-id="618a2-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="618a2-174">Volající pak můžete použít tento index upravit hodnotu v samostatné volání metody.</span><span class="sxs-lookup"><span data-stu-id="618a2-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="618a2-175">Volající však můžete také upravit index pro přístup a případně upravit jiné hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="618a2-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="618a2-176">Následující příklad ukazuje, `FindNumber` jak by metoda mohla být přepsána po C# 7.3 pro použití místního přeřazení ref:</span><span class="sxs-lookup"><span data-stu-id="618a2-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="618a2-177">Tato druhá verze je efektivnější s delší sekvence ve scénářích, kde požadované číslo je blíže ke konci pole.</span><span class="sxs-lookup"><span data-stu-id="618a2-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="618a2-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="618a2-178">See also</span></span>

- [<span data-ttu-id="618a2-179">klíčové slovo ref</span><span class="sxs-lookup"><span data-stu-id="618a2-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="618a2-180">Zapisujte bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="618a2-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
