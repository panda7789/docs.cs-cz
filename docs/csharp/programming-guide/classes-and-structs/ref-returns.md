---
title: Návratové hodnoty REF a ref lokální proměnné (Průvodce C#)
description: Zjistěte, jak definovat a použijte ref vrátit a místní hodnoty ref
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="18886-103">Vrátí REF a místní hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="18886-103">Ref returns and ref locals</span></span>

<span data-ttu-id="18886-104">Od verze jazyka C# 7, C# podporuje odkaz návratové hodnoty (ref vrátí).</span><span class="sxs-lookup"><span data-stu-id="18886-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="18886-105">Odkaz vrátí hodnotu umožňuje metodu pro odkaz na proměnnou, nikoli hodnotu, vrátí zpět do volající.</span><span class="sxs-lookup"><span data-stu-id="18886-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="18886-106">Volající může zvolte zacházet s Vrácená proměnná, jako kdyby byly vráceny, hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="18886-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="18886-107">Volající můžete vytvořit nové proměnné, který je sám odkaz na vrácené hodnoty, názvem ref místní.</span><span class="sxs-lookup"><span data-stu-id="18886-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="18886-108">Co je návratovou hodnotu odkazu?</span><span class="sxs-lookup"><span data-stu-id="18886-108">What is a reference return value?</span></span>

<span data-ttu-id="18886-109">Většina vývojářů obeznámeni s předáním argumentu volané metodě *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="18886-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="18886-110">Seznam obsahuje proměnnou předání odkazem a veškeré změny provedené zavolat metodu na hodnotu argumentu zavolat metodu je možné vysledovat volajícího.</span><span class="sxs-lookup"><span data-stu-id="18886-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="18886-111">A *odkazovat návratovou hodnotu* znamená, že metoda vrátí *odkaz* (nebo alias) některé proměnné jejichž oborem, který zahrnuje metodu a jejichž doba platnosti musíte rozšířit nad rámec návratový metody.</span><span class="sxs-lookup"><span data-stu-id="18886-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="18886-112">Úpravy návratovou hodnotu metody volajícího jsou vytvářeny proměnnou, kterou vrátí metodu.</span><span class="sxs-lookup"><span data-stu-id="18886-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="18886-113">Deklarace, který vrací metodu *odkazovat návratová hodnota* označuje, že metoda vrátí alias proměnné.</span><span class="sxs-lookup"><span data-stu-id="18886-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="18886-114">Návrh je často, volající kód mají mít přístup k této proměnné prostřednictvím alias, včetně jej upravit.</span><span class="sxs-lookup"><span data-stu-id="18886-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="18886-115">Vyplývá, že metody vrácení podle reference nemůže mít návratový typ `void`.</span><span class="sxs-lookup"><span data-stu-id="18886-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="18886-116">Existují některá omezení na výrazu, která vrací metodu jako návratová hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="18886-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="18886-117">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="18886-117">These include:</span></span>

- <span data-ttu-id="18886-118">Návratová hodnota musí mít životnost, který je delší než provádění metody.</span><span class="sxs-lookup"><span data-stu-id="18886-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="18886-119">Jinými slovy nemůže být místní proměnné v metodě, která vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="18886-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="18886-120">Dá se instanci nebo statické pole třídy, nebo může být argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="18886-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="18886-121">Probíhá pokus o vraťte se generuje chyba kompilátoru CS8168, místní proměnné "nemůže vrátit místní 'obj' odkazem protože se nejedná o místní ref."</span><span class="sxs-lookup"><span data-stu-id="18886-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="18886-122">Návratová hodnota nemůže být literál `null`.</span><span class="sxs-lookup"><span data-stu-id="18886-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="18886-123">Probíhá pokus o vrátit `null` vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="18886-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="18886-124">Metoda s návratovým ref může vrátit alias do proměnné, jehož hodnota je aktuálně hodnotu null (bez instancí) nebo [typ s možnou hodnotou Null](../nullable-types/index.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="18886-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="18886-125">Návratová hodnota nemůže být konstanta, člena výčtu, podle hodnota vrácená vlastnost nebo metoda `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="18886-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="18886-126">Na tyto vrácení vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="18886-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="18886-127">Kromě toho protože asynchronní metodu může vrátit před dokončením provádění, zatímco vrácená hodnota je stále neznámé, odkaz návratové hodnoty nejsou povoleny u asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="18886-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="18886-128">Definice návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="18886-128">Defining a ref return value</span></span>

<span data-ttu-id="18886-129">Definice návratové hodnoty ref přidáním [ref](../../language-reference/keywords/ref.md) – klíčové slovo k návratový typ podpis metody.</span><span class="sxs-lookup"><span data-stu-id="18886-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="18886-130">Například následující podpis znamená, že `GetContactInformation` vrátí odkaz na vlastnost `Person` objekt, který má volající:</span><span class="sxs-lookup"><span data-stu-id="18886-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="18886-131">Kromě toho název objektu vrácené každou [vrátit](../../language-reference/keywords/return.md) příkaz v těle metoda musí předcházet [ref](../../language-reference/keywords/ref.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="18886-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="18886-132">Například následující `return` příkaz vrátí odkaz na `Person` objekt s názvem `p`:</span><span class="sxs-lookup"><span data-stu-id="18886-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="18886-133">Využívání návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="18886-133">Consuming a ref return value</span></span>

<span data-ttu-id="18886-134">Ref vrátí, zda je hodnota alias jiné proměnné v oboru zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="18886-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="18886-135">Dokáže interpretovat jakékoli využití návratový ref jako použití proměnné ho aliasy:</span><span class="sxs-lookup"><span data-stu-id="18886-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="18886-136">Při přiřazení jeho hodnota se přiřazení hodnoty proměnné ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="18886-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="18886-137">Při čtení jeho hodnota se čtení hodnoty proměnné ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="18886-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="18886-138">Pokud se ji vrátíte *odkazem* alias se vrátíte k dané stejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="18886-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="18886-139">Pokud předáte na jinou metodu *odkazem* jsou předáním odkazu na proměnnou ho aliasy.</span><span class="sxs-lookup"><span data-stu-id="18886-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="18886-140">Pokud vytvoříte [ref místní](#ref-local) alias, provedete nový alias stejnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="18886-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="18886-141">Místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="18886-141">Ref locals</span></span>

<span data-ttu-id="18886-142">Předpokládejme, `GetContactInformation` metoda je deklarován jako ref návratový:</span><span class="sxs-lookup"><span data-stu-id="18886-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="18886-143">-Hodnota přiřazení čte hodnotu proměnné a přiřadí ji k nové proměnné:</span><span class="sxs-lookup"><span data-stu-id="18886-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="18886-144">Předchozí přiřazení deklaruje `p` jako místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="18886-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="18886-145">Počáteční hodnoty budou zkopírována z čtení hodnoty vrácené `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="18886-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="18886-146">Všechny budoucí přiřazení `p` nedojde ke změně hodnoty proměnné vrácený `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="18886-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="18886-147">Proměnná `p` již není alias proměnnou vrátila.</span><span class="sxs-lookup"><span data-stu-id="18886-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="18886-148">Deklarování *ref místní* proměnné pro kopírování alias na původní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18886-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="18886-149">V následující přiřazení `p` je alias proměnnou, kterou vrátil `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="18886-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="18886-150">Následné použití `p` je stejný jako použití proměnné vrácený `GetContactInformation` protože `p` je alias pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="18886-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="18886-151">Změny `p` změnit také proměnnou, kterou vrátil `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="18886-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="18886-152">Všimněte si, že `ref` – klíčové slovo se používá i před místní deklarace proměnné *a* před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="18886-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="18886-153">Hodnotu můžete přejít pomocí odkazu stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="18886-153">You can access a value by reference in the same way.</span></span> <span data-ttu-id="18886-154">V některých případech přístup k hodnotu odkazem zvyšuje výkon vyhnout potenciálně nákladné kopírování.</span><span class="sxs-lookup"><span data-stu-id="18886-154">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="18886-155">Například následující příkaz ukazuje, jak jeden můžete definovat ref místní hodnotu, která slouží k odkazování hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18886-155">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="18886-156">Všimněte si, že `ref` – klíčové slovo se používá i před místní deklarace proměnné *a* před hodnotu v druhém příkladu.</span><span class="sxs-lookup"><span data-stu-id="18886-156">Note that the `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="18886-157">Nepodařilo se současně obsahovat `ref` klíčová slova v deklarace proměnné a přiřazení v obou příklady výsledkem chyba kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="18886-157">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="18886-158">Vrátí REF a místní hodnoty ref: příklad</span><span class="sxs-lookup"><span data-stu-id="18886-158">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="18886-159">V následujícím příkladu definuje `NumberStore` třídu, která ukládá pole celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="18886-159">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="18886-160">`FindNumber` Metoda vrátí odkaz na číslo, kterým je větší než nebo rovná počtu předat jako argument.</span><span class="sxs-lookup"><span data-stu-id="18886-160">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="18886-161">Pokud žádné číslo větší než nebo rovna hodnotě argument, metoda vrátí číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="18886-161">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="18886-162">Následující příklad volání `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16.</span><span class="sxs-lookup"><span data-stu-id="18886-162">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="18886-163">Volající pak zdvojnásobí hodnota vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="18886-163">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="18886-164">Jak ukazuje výstup z příkladu, tato změna se projeví v hodnotě pole elementů `NumberStore` instance.</span><span class="sxs-lookup"><span data-stu-id="18886-164">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="18886-165">Bez podpory pro odkaz vrácené hodnoty tyto operace obvykle provádí vrácení index pole element společně s jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18886-165">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="18886-166">Volající potom můžete pomocí tohoto indexu změňte hodnotu v samostatné metodě volání.</span><span class="sxs-lookup"><span data-stu-id="18886-166">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="18886-167">Volající však můžete také upravit index pro přístup a které by mohly mít úpravy ostatní hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="18886-167">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="18886-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="18886-168">See also</span></span>

[<span data-ttu-id="18886-169">REF – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="18886-169">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="18886-170">Odkaz na sémantiku s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="18886-170">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
