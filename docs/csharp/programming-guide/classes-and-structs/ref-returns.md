---
title: "Návratové hodnoty REF a ref lokální proměnné (Průvodce C#)"
description: "Zjistěte, jak definovat a použijte ref vrátit a místní hodnoty ref"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="0aeba-103">Vrátí REF a místní hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="0aeba-103">Ref returns and ref locals</span></span>

<span data-ttu-id="0aeba-104">Od verze jazyka C# 7, C# podporuje odkaz návratové hodnoty (ref vrátí).</span><span class="sxs-lookup"><span data-stu-id="0aeba-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="0aeba-105">Odkaz vrátí hodnotu umožňuje metodu pro odkaz na objekt, nikoli hodnotu, vrátí zpět do volající.</span><span class="sxs-lookup"><span data-stu-id="0aeba-105">A reference return value allows a method to return a reference to an object, rather than a value, back to a caller.</span></span> <span data-ttu-id="0aeba-106">Volající může zvolte zacházet s vráceného objektu vrácena jako v případě, že byly vráceny, hodnotou nebo odkazem.</span><span class="sxs-lookup"><span data-stu-id="0aeba-106">The caller can then choose to treat the returned object returned as if it were returned by value or by reference.</span></span> <span data-ttu-id="0aeba-107">Hodnota vrácená odkazem, volající zpracovává jako referenční místo místní ref je hodnota.</span><span class="sxs-lookup"><span data-stu-id="0aeba-107">A value returned by reference that the caller handles as a reference rather than a value is a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="0aeba-108">Co je návratovou hodnotu odkazu?</span><span class="sxs-lookup"><span data-stu-id="0aeba-108">What is a reference return value?</span></span>

<span data-ttu-id="0aeba-109">Většina vývojářů obeznámeni s předáním argumentu volané metodě *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="0aeba-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="0aeba-110">Seznam obsahuje hodnotu předanou odkaz a veškeré změny provedené zavolat metodu na jeho hodnotu argumentu zavolat metodu jsou vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-110">A called method's argument list includes a value passed by reference, and any changes made to its value by the called method are returned to the caller.</span></span> <span data-ttu-id="0aeba-111">A *odkazovat návratovou hodnotu* protikladem:</span><span class="sxs-lookup"><span data-stu-id="0aeba-111">A *reference return value* is the opposite:</span></span>

- <span data-ttu-id="0aeba-112">Vrácená hodnota zavolat metodu, místo, předaný argument je odkaz.</span><span class="sxs-lookup"><span data-stu-id="0aeba-112">The called method's return value, rather than an argument passed to it, is a reference.</span></span>

- <span data-ttu-id="0aeba-113">Volající, nikoli zavolat metodu, můžete upravit hodnota vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="0aeba-113">The caller, rather than the called method, can modify the value returned by the method.</span></span>

- <span data-ttu-id="0aeba-114">Místo úpravy k argumentu, které se projeví v stav objektu na volajícího se projeví změny návratovou hodnotu metody volajícího ve stavu objektu, jehož metoda byla volána.</span><span class="sxs-lookup"><span data-stu-id="0aeba-114">Instead of modifications to the argument that are reflected in state of the object on the caller, modifications to the method's return value by the caller are reflected in the state of the object whose method was called.</span></span>

<span data-ttu-id="0aeba-115">Návratové hodnoty odkaz můžete vytvořit kompaktnější kódu, jakož i povolit vystavit pouze jednotlivé datové položky, jako je například k elementu pole, které jsou důležité pro volající objekt.</span><span class="sxs-lookup"><span data-stu-id="0aeba-115">Reference return values can produce more compact code, as well as allow an object to expose only the individual data items, such as an array element, that are of interest to the caller.</span></span> <span data-ttu-id="0aeba-116">Tím se snižuje pravděpodobnost, že volající nechtěně změnit stav objektu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-116">This reduces the likelihood that the caller will inadvertently modify the object's state.</span></span>

<span data-ttu-id="0aeba-117">Existují některá omezení na hodnotu, která metoda může vrátit jako návratová hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-117">There are some restrictions on the value that a method can return as a reference return value.</span></span> <span data-ttu-id="0aeba-118">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="0aeba-118">These include:</span></span>

- <span data-ttu-id="0aeba-119">Návratová hodnota nemůže být `void`.</span><span class="sxs-lookup"><span data-stu-id="0aeba-119">The return value cannot be `void`.</span></span> <span data-ttu-id="0aeba-120">Probíhá pokus o definovat metodu s `void` návratovou hodnotu odkazu vygeneruje Chyba kompilátoru CS1547, "– klíčové slovo 'void' nelze v tomto kontextu použít."</span><span class="sxs-lookup"><span data-stu-id="0aeba-120">Attempting to define a method with a `void` reference return value generates compiler error CS1547, "Keyword 'void' cannot be used in this context."</span></span>
 
- <span data-ttu-id="0aeba-121">Návratová hodnota nemůže být místní proměnné v metodu, která vrátí. musí mít obor, který je mimo metodu, která vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="0aeba-121">The return value cannot be a local variable in the method that returns it; it must have a scope that is outside the method that returns it.</span></span> <span data-ttu-id="0aeba-122">Dá se instanci nebo statické pole třídy, nebo může být argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="0aeba-122">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="0aeba-123">Probíhá pokus o vraťte se generuje chyba kompilátoru CS8168, místní proměnné "nemůže vrátit místní 'obj' odkazem protože se nejedná o místní ref."</span><span class="sxs-lookup"><span data-stu-id="0aeba-123">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="0aeba-124">Návratová hodnota nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="0aeba-124">The return value cannot be a `null`.</span></span> <span data-ttu-id="0aeba-125">Probíhá pokus o vrátit `null` vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="0aeba-125">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="0aeba-126">Pokud metoda s návratovým ref musí vrátit hodnotu null, můžete buď vrátit hodnotu null (bez instancí) pro typ odkaz nebo [typ s možnou hodnotou Null](../nullable-types/index.md) pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0aeba-126">If a method with a ref return needs to return a null value, you can either return a null (uninstantiated) value for a reference type or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="0aeba-127">Návratová hodnota nemůže být konstanta, člena výčtu nebo vlastnost `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="0aeba-127">The return value cannot be a constant, an enumeration member, or a property of a `class` or `struct`.</span></span> <span data-ttu-id="0aeba-128">Na tyto vrácení vygeneruje Chyba kompilátoru CS8156, "výraz nelze použít v tomto kontextu, protože nemusí být vrátil odkazem."</span><span class="sxs-lookup"><span data-stu-id="0aeba-128">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="0aeba-129">Kromě toho protože asynchronní metodu může vrátit před dokončením provádění, zatímco vrácená hodnota je stále neznámé, odkaz návratové hodnoty nejsou povoleny u asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-129">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="0aeba-130">Definice návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="0aeba-130">Defining a ref return value</span></span>

<span data-ttu-id="0aeba-131">Definice návratové hodnoty ref přidáním [ref](../../language-reference/keywords/ref.md) – klíčové slovo k návratový typ podpis metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-131">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="0aeba-132">Například následující podpis znamená, že `GetContactInformation` vrátí odkaz na vlastnost `Person` objekt, který má volající:</span><span class="sxs-lookup"><span data-stu-id="0aeba-132">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="0aeba-133">Kromě toho název objektu vrácené každou [vrátit](../../language-reference/keywords/return.md) příkaz v těle metoda musí předcházet [ref](../../language-reference/keywords/ref.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0aeba-133">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="0aeba-134">Například následující `return` příkaz vrátí `Person` objekt s názvem `p` odkazem:</span><span class="sxs-lookup"><span data-stu-id="0aeba-134">For example, the following `return` statement returns a `Person` object named `p` by reference:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="0aeba-135">Využívání návratové hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="0aeba-135">Consuming a ref return value</span></span>

<span data-ttu-id="0aeba-136">Volající může zpracovat ref návratovou hodnotu v některém ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="0aeba-136">A caller can handle a ref return value in either of two ways:</span></span>

- <span data-ttu-id="0aeba-137">Jako obyčejnou hodnota vrácená metodou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0aeba-137">As an ordinary value returned by value from a method.</span></span> <span data-ttu-id="0aeba-138">Volající můžete ignorovat, že návratová hodnota je odkaz návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-138">The caller can choose to ignore that the return value is a reference return value.</span></span> <span data-ttu-id="0aeba-139">V takovém případě změny provedené v hodnoty vrácené volání metody, které se neprojeví v stav volané typu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-139">In this case, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span> <span data-ttu-id="0aeba-140">Pokud typ hodnoty vrácené hodnoty, všechny změny hodnoty vrácené volání metody, které se neprojeví v stav volané typu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-140">If the returned value is a value type, any changes made to the value returned by the method call are not reflected in the state of the called type.</span></span>

- <span data-ttu-id="0aeba-141">Jako referenci vrátíte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-141">As a reference return value.</span></span> <span data-ttu-id="0aeba-142">Volající musí definovat proměnnou, ke kterému je přiřazen návratovou hodnotu odkazu jako [ref místní](#ref-local), a všechny změny na hodnoty vrácené volání metody, které se projeví ve stavu volané typu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-142">The caller must define the variable to which the reference return value is assigned as a [ref local](#ref-local), and any changes to the value returned by the method call are reflected in the state of the called type.</span></span> 

## <a name="ref-locals"></a><span data-ttu-id="0aeba-143">Místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="0aeba-143">Ref locals</span></span>

<span data-ttu-id="0aeba-144">Pro zpracování návratovou hodnotu odkazu jako odkaz, volající musí deklarovat hodnota, která má být *ref místní* pomocí `ref` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0aeba-144">To handle the reference return value as a reference, the caller must declare the value to be a *ref local* by using the `ref` keyword.</span></span> <span data-ttu-id="0aeba-145">Například pokud je hodnota vrácené `Person.GetContactInfomation` metoda má být využívány jako odkaz, nikoli hodnotu, volání metody, které se zobrazí jako:</span><span class="sxs-lookup"><span data-stu-id="0aeba-145">For example, if the value returned by the `Person.GetContactInfomation` method is to be consumed as a reference rather than a value, the method call appears as:</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="0aeba-146">Všimněte si, že `ref` – klíčové slovo se používá i před místní deklarace proměnné *a* před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-146">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> <span data-ttu-id="0aeba-147">Nepodařilo se současně obsahovat `ref` klíčová slova v deklarace proměnné a přiřazení má za následek chyby kompilátoru CS8172, "nelze inicializovat proměnnou podle odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="0aeba-147">Failure to include both `ref` keywords in the variable declaration and assignment results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
<span data-ttu-id="0aeba-148">Následné změny `Person` objekt vrácený metodou, se projeví v `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-148">Subsequent changes to the `Person` object returned by the method are reflected in the `contacts` object.</span></span>

<span data-ttu-id="0aeba-149">Pokud `p` není definován jako místní ref pomocí `ref` – klíčové slovo, všechny změny provedené v `p` volajícího se neprojeví v `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-149">If `p` is not defined as a ref local by using the `ref` keyword, any changes made to `p` by the caller are not reflected in the `contacts` object.</span></span>
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="0aeba-150">Vrátí REF a místní hodnoty ref: příklad</span><span class="sxs-lookup"><span data-stu-id="0aeba-150">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="0aeba-151">V následujícím příkladu definuje `NumberStore` třídu, která ukládá pole celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0aeba-151">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="0aeba-152">`FindNumber` Metoda vrátí odkaz na číslo, kterým je větší než nebo rovná počtu předat jako argument.</span><span class="sxs-lookup"><span data-stu-id="0aeba-152">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="0aeba-153">Pokud žádné číslo větší než nebo rovna hodnotě argument, metoda vrátí číslo v indexu 0.</span><span class="sxs-lookup"><span data-stu-id="0aeba-153">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="0aeba-154">Následující příklad volání `NumberStore.FindNumber` metoda načíst první hodnotu, která je větší než nebo rovný 16.</span><span class="sxs-lookup"><span data-stu-id="0aeba-154">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="0aeba-155">Volající pak zdvojnásobí hodnota vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="0aeba-155">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="0aeba-156">Jak ukazuje výstup z příkladu, tato změna se projeví v hodnotě pole elementů `NumberStore` instance.</span><span class="sxs-lookup"><span data-stu-id="0aeba-156">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="0aeba-157">Bez podpory pro odkaz vrácené hodnoty tyto operace obvykle provádí vrácení index pole element společně s jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0aeba-157">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="0aeba-158">Volající potom můžete pomocí tohoto indexu změňte hodnotu v samostatné metodě volání.</span><span class="sxs-lookup"><span data-stu-id="0aeba-158">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="0aeba-159">Volající však můžete také upravit index pro přístup a které by mohly mít úpravy ostatní hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="0aeba-159">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="0aeba-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="0aeba-160">See also</span></span>

[<span data-ttu-id="0aeba-161">REF – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="0aeba-161">ref keyword</span></span>](../../language-reference/keywords/ref.md)
