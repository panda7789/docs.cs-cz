---
title: Návratové hodnoty REF a ref lokální proměnné (Průvodce C#)
description: Zjistěte, jak definovat a použijte ref vrátit a místní hodnoty ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 57fa8f52320b30a1cb228b41e3f5e6655c235561
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="f0dae-103">Vrátí REF a místní hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="f0dae-103">Ref returns and ref locals</span></span>

<span data-ttu-id="f0dae-104">Od verze jazyka C# 7, C# podporuje odkaz návratové hodnoty (ref vrátí).</span><span class="sxs-lookup"><span data-stu-id="f0dae-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="f0dae-105">Odkaz vrátí hodnotu umožňuje metodu pro odkaz na proměnnou, nikoli hodnotu, vrátí zpět do volající.</span><span class="sxs-lookup"><span data-stu-id="f0dae-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="f0dae-106">Volající může zvolte zacházet s Vrácená proměnná, jako kdyby byly vráceny, hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="f0dae-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="f0dae-107">Volající můžete vytvořit nové proměnné, který je sám odkaz na vrácené hodnoty, názvem ref místní.</span><span class="sxs-lookup"><span data-stu-id="f0dae-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="f0dae-108">Co je návratovou hodnotu odkazu?</span><span class="sxs-lookup"><span data-stu-id="f0dae-108">What is a reference return value?</span></span>

<span data-ttu-id="f0dae-109">Většina vývojářů obeznámeni s předáním argumentu volané metodě *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="f0dae-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="f0dae-110">Seznam argumentů zavolat metodu zahrnuje předaná odkaz na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f0dae-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="f0dae-111">Všechny změny provedené zavolat metodu na jeho hodnotu je možné vysledovat volajícího.</span><span class="sxs-lookup"><span data-stu-id="f0dae-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="f0dae-112">A *odkazovat návratovou hodnotu* znamená, že metoda vrátí *odkaz* (nebo alias) některé proměnné.</span><span class="sxs-lookup"><span data-stu-id="f0dae-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="f0dae-113">Tuto proměnnou oboru musí obsahovat metodu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-113">That variable's scope must include the method.</span></span> <span data-ttu-id="f0dae-114">Tuto proměnnou životnost, musíte rozšířit nad rámec návratový metody.</span><span class="sxs-lookup"><span data-stu-id="f0dae-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="f0dae-115">Úpravy návratovou hodnotu metody volajícího jsou vytvářeny proměnnou, kterou vrátí metodu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="f0dae-116">Deklarace, který vrací metodu *odkazovat návratová hodnota* označuje, že metoda vrátí alias proměnné.</span><span class="sxs-lookup"><span data-stu-id="f0dae-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="f0dae-117">Návrh je často, volající kód mají mít přístup k této proměnné prostřednictvím alias, včetně jej upravit.</span><span class="sxs-lookup"><span data-stu-id="f0dae-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="f0dae-118">Vyplývá, že metody vrácení podle reference nemůže mít návratový typ `void`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="f0dae-119">Existují některá omezení na výrazu, která vrací metodu jako návratová hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="f0dae-120">Omezení, patří:</span><span class="sxs-lookup"><span data-stu-id="f0dae-120">Restrictions include:</span></span>

- <span data-ttu-id="f0dae-121">Návratová hodnota musí mít životnost, který je delší než provádění metody.</span><span class="sxs-lookup"><span data-stu-id="f0dae-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="f0dae-122">Jinými slovy nemůže být místní proměnné v metodě, která vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="f0dae-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="f0dae-123">Dá se instanci nebo statické pole třídy, nebo může být argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="f0dae-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="f0dae-124">Probíhá pokus o vraťte se generuje chyba kompilátoru CS8168, místní proměnné "nemůže vrátit místní 'obj' odkazem protože se nejedná o místní ref."</span><span class="sxs-lookup"><span data-stu-id="f0dae-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="f0dae-125">Návratová hodnota nemůže být literál `null`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="f0dae-126">Vrácení `null` vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="f0dae-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="f0dae-127">Metoda s návratovým ref může vrátit alias do proměnné, jehož hodnota je aktuálně hodnotu null (bez instancí) nebo [typ s možnou hodnotou Null](../nullable-types/index.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0dae-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="f0dae-128">Návratová hodnota nemůže být konstanta, člena výčtu, podle hodnota vrácená vlastnost nebo metoda `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="f0dae-129">Narušení toto pravidlo generuje chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="f0dae-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="f0dae-130">Kromě toho odkaz návratové hodnoty nejsou povoleny na asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="f0dae-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="f0dae-131">Asynchronní metoda může vrátit před dokončením provádění, zatímco vrácená hodnota je stále neznámé.</span><span class="sxs-lookup"><span data-stu-id="f0dae-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="f0dae-132">Definice návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="f0dae-132">Defining a ref return value</span></span>

<span data-ttu-id="f0dae-133">Definice návratové hodnoty ref přidáním [ref](../../language-reference/keywords/ref.md) – klíčové slovo k návratový typ podpis metody.</span><span class="sxs-lookup"><span data-stu-id="f0dae-133">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="f0dae-134">Například následující podpis znamená, že `GetContactInformation` vrátí odkaz na vlastnost `Person` objekt, který má volající:</span><span class="sxs-lookup"><span data-stu-id="f0dae-134">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="f0dae-135">Kromě toho název objektu vrácené každou [vrátit](../../language-reference/keywords/return.md) příkaz v těle metoda musí předcházet [ref](../../language-reference/keywords/ref.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f0dae-135">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="f0dae-136">Například následující `return` příkaz vrátí odkaz na `Person` objekt s názvem `p`:</span><span class="sxs-lookup"><span data-stu-id="f0dae-136">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="f0dae-137">Využívání návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="f0dae-137">Consuming a ref return value</span></span>

<span data-ttu-id="f0dae-138">Ref vrátí, zda je hodnota alias jiné proměnné v oboru zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="f0dae-139">Dokáže interpretovat jakékoli využití návratový ref jako použití proměnné ho aliasy:</span><span class="sxs-lookup"><span data-stu-id="f0dae-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="f0dae-140">Při přiřazení jeho hodnota se přiřazení hodnoty proměnné ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="f0dae-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="f0dae-141">Při čtení jeho hodnota se čtení hodnoty proměnné ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="f0dae-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="f0dae-142">Pokud se ji vrátíte *odkazem*, alias se vrátíte k dané stejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="f0dae-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="f0dae-143">Pokud předáte na jinou metodu *odkazem*, jsou předáním odkazu na proměnnou ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="f0dae-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="f0dae-144">Pokud vytvoříte [ref místní](#ref-local) alias, provedete nový alias stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f0dae-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="f0dae-145">Místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="f0dae-145">Ref locals</span></span>

<span data-ttu-id="f0dae-146">Předpokládejme, `GetContactInformation` metoda je deklarován jako ref návratový:</span><span class="sxs-lookup"><span data-stu-id="f0dae-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="f0dae-147">-Hodnota přiřazení čte hodnotu proměnné a přiřadí ji k nové proměnné:</span><span class="sxs-lookup"><span data-stu-id="f0dae-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="f0dae-148">Předchozí přiřazení deklaruje `p` jako místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="f0dae-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="f0dae-149">Počáteční hodnoty budou zkopírována z čtení hodnoty vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="f0dae-150">Všechny budoucí přiřazení `p` nedojde ke změně hodnoty proměnné vrácený `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="f0dae-151">Proměnná `p` již není alias proměnnou vrátila.</span><span class="sxs-lookup"><span data-stu-id="f0dae-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="f0dae-152">Deklarování *ref místní* proměnné pro kopírování alias na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="f0dae-153">V následující přiřazení `p` je alias proměnnou, kterou vrátil `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="f0dae-154">Následné použití `p` je stejný jako použití proměnné vrácený `GetContactInformation` protože `p` je alias pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f0dae-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="f0dae-155">Změny `p` změnit také proměnnou, kterou vrátil `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="f0dae-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="f0dae-156">`ref` – Klíčové slovo se používá i před místní deklarace proměnné *a* před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="f0dae-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="f0dae-157">Hodnotu můžete přejít pomocí odkazu stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f0dae-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="f0dae-158">V některých případech přístup k hodnotu odkazem zvyšuje výkon vyhnout potenciálně nákladné kopírování.</span><span class="sxs-lookup"><span data-stu-id="f0dae-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="f0dae-159">Například následující příkaz ukazuje, jak jeden můžete definovat ref místní hodnotu, která slouží k odkazování hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="f0dae-160">`ref` – Klíčové slovo se používá i před místní deklarace proměnné *a* před hodnotu v druhém příkladu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="f0dae-161">Nepodařilo se současně obsahovat `ref` klíčová slova v deklarace proměnné a přiřazení v obou příklady výsledkem chyba kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="f0dae-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="f0dae-162">Před C# 7.3 nelze odkazovat na jiného úložiště po inicializaci přeřadit ref lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="f0dae-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="f0dae-163">Aby byla odebrána omezení.</span><span class="sxs-lookup"><span data-stu-id="f0dae-163">That restriction has been removed.</span></span> <span data-ttu-id="f0dae-164">Následující příklad ukazuje opětovnému přiřazení:</span><span class="sxs-lookup"><span data-stu-id="f0dae-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="f0dae-165">Lokální proměnné REF musí být stále inicializován, když jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="f0dae-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="f0dae-166">Vrátí REF a místní hodnoty ref: příklad</span><span class="sxs-lookup"><span data-stu-id="f0dae-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="f0dae-167">V následujícím příkladu definuje `NumberStore` třídu, která ukládá pole celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0dae-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="f0dae-168">`FindNumber` Metoda vrátí odkaz na číslo, kterým je větší než nebo rovná počtu předat jako argument.</span><span class="sxs-lookup"><span data-stu-id="f0dae-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="f0dae-169">Pokud žádné číslo větší než nebo rovna hodnotě argument, metoda vrátí číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="f0dae-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="f0dae-170">Následující příklad volání `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16.</span><span class="sxs-lookup"><span data-stu-id="f0dae-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="f0dae-171">Volající pak zdvojnásobí hodnota vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="f0dae-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="f0dae-172">Výstup z příkladu zobrazuje změny projeví v hodnotě pole elementů `NumberStore` instance.</span><span class="sxs-lookup"><span data-stu-id="f0dae-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="f0dae-173">Bez podpory pro vrácené hodnoty odkaz takovou operaci provádí vrácení index pole element společně s jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f0dae-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="f0dae-174">Volající potom můžete pomocí tohoto indexu změňte hodnotu v samostatné metodě volání.</span><span class="sxs-lookup"><span data-stu-id="f0dae-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="f0dae-175">Volající však můžete také upravit index pro přístup a které by mohly mít úpravy ostatní hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="f0dae-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="f0dae-176">Následující příklad ukazuje jak `FindNumber` metoda by mohla být přepsána po 7.3 C# používat místní změny přiřazení ref:</span><span class="sxs-lookup"><span data-stu-id="f0dae-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="f0dae-177">Tato druhá verze je efektivnější s delší pořadí ve scénářích, kde číslo žádá o blíž ke konci pole.</span><span class="sxs-lookup"><span data-stu-id="f0dae-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0dae-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0dae-178">See also</span></span>

[<span data-ttu-id="f0dae-179">REF – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="f0dae-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="f0dae-180">Odkaz na sémantiku s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="f0dae-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
