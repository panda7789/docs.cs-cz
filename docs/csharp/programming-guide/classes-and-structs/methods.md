---
title: Metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 114fa2973c50be9a4199db9729e3cd9ea6122866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626526"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="a99eb-102">Metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a99eb-102">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="a99eb-103">Metoda je blok kódu, který obsahuje řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="a99eb-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="a99eb-104">Program způsobí, že příkazy, které mají být provedeny voláním metody a zadáním všechny argumenty požadované metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="a99eb-105">V C# každá provedená instrukce se provádí v kontextu metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="a99eb-106">Metoda `Main` je vstupníbod pro každou aplikaci Jazyka C# a je volána za běhu common jazyka (CLR) při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-106">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="a99eb-107">Tento článek popisuje pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-107">This article discusses named methods.</span></span> <span data-ttu-id="a99eb-108">Informace o anonymních funkcích naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-108">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="a99eb-109">Podpisy metod</span><span class="sxs-lookup"><span data-stu-id="a99eb-109">Method signatures</span></span>

<span data-ttu-id="a99eb-110">Metody jsou deklarovány ve [třídě](../../language-reference/keywords/class.md), [struktuře](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../interfaces/index.md) zadáním úrovně přístupu, jako `public` jsou nebo `private`, volitelné modifikátory, jako `abstract` jsou nebo `sealed`, vrácená hodnota, název metody a všechny parametry metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-110">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="a99eb-111">Tyto části dohromady jsou podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-111">These parts together are the signature of the method.</span></span>

> [!NOTE]
> <span data-ttu-id="a99eb-112">Návratový typ metody není součástí podpisu metody pro účely přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="a99eb-113">Je však součástí podpisu metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a99eb-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="a99eb-114">Parametry metody jsou uzavřeny v závorce a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="a99eb-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="a99eb-115">Prázdné závorky označují, že metoda nevyžaduje žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="a99eb-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="a99eb-116">Tato třída obsahuje čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="a99eb-116">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="a99eb-117">Přístup k metodě</span><span class="sxs-lookup"><span data-stu-id="a99eb-117">Method access</span></span>

<span data-ttu-id="a99eb-118">Volání metody na objekt je jako přístup k poli.</span><span class="sxs-lookup"><span data-stu-id="a99eb-118">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="a99eb-119">Za název objektu přidejte tečku, název metody a závorky.</span><span class="sxs-lookup"><span data-stu-id="a99eb-119">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="a99eb-120">Argumenty jsou uvedeny v závorce a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="a99eb-120">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="a99eb-121">Metody třídy `Motorcycle` proto lze volat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a99eb-121">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="a99eb-122">Parametry metody vs. argumenty</span><span class="sxs-lookup"><span data-stu-id="a99eb-122">Method parameters vs. arguments</span></span>

<span data-ttu-id="a99eb-123">Definice metody určuje názvy a typy všech požadovaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="a99eb-123">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="a99eb-124">Při volání kódu volá metodu, poskytuje konkrétní hodnoty nazývané argumenty pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="a99eb-124">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="a99eb-125">Argumenty musí být kompatibilní s typem parametru, ale název argumentu (pokud existuje) použitý v volajícím kódu nemusí být stejný jako parametr pojmenovaný definovaný v metodě.</span><span class="sxs-lookup"><span data-stu-id="a99eb-125">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="a99eb-126">Například:</span><span class="sxs-lookup"><span data-stu-id="a99eb-126">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="a99eb-127">Předání odkazem vs. předávání hodnotou</span><span class="sxs-lookup"><span data-stu-id="a99eb-127">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="a99eb-128">Ve výchozím nastavení, když je instance [typu hodnoty](../../language-reference/builtin-types/value-types.md) předána metodě, její kopie je předána namísto samotné instance.</span><span class="sxs-lookup"><span data-stu-id="a99eb-128">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="a99eb-129">Proto změny argumentu nemají žádný vliv na původní instance v volající metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-129">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="a99eb-130">Chcete-li předat instanci typu `ref` hodnoty odkazem, použijte klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a99eb-130">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="a99eb-131">Další informace naleznete [v tématu Předávání parametrů typu hodnoty](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-131">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="a99eb-132">Pokud je objekt typu odkazu předán metodě, je předán odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="a99eb-132">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="a99eb-133">To znamená, že metoda neobdrží samotný objekt, ale argument, který označuje umístění objektu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-133">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="a99eb-134">Pokud změníte člen objektu pomocí tohoto odkazu, změna se projeví v argumentu v volající metodě, i když objekt předáte hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a99eb-134">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="a99eb-135">Typ odkazu vytvoříte pomocí `class` klíčového slova, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a99eb-135">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="a99eb-136">Nyní pokud předáte objekt, který je založen na tomto typu metodě, je předán odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="a99eb-136">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="a99eb-137">Následující příklad předá objekt `SampleRefType` typu `ModifyObject`metodě :</span><span class="sxs-lookup"><span data-stu-id="a99eb-137">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="a99eb-138">Příklad dělá v podstatě totéž jako předchozí příklad v tom, že předá argument podle hodnoty metodě.</span><span class="sxs-lookup"><span data-stu-id="a99eb-138">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="a99eb-139">Ale protože se používá typ odkazu, výsledek je jiný.</span><span class="sxs-lookup"><span data-stu-id="a99eb-139">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="a99eb-140">Změna provedená v `ModifyObject` `value` poli parametru , `obj`také změní `value` pole argumentu `rt`, `TestRefType` v metodě.</span><span class="sxs-lookup"><span data-stu-id="a99eb-140">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="a99eb-141">Metoda `TestRefType` zobrazí 33 jako výstup.</span><span class="sxs-lookup"><span data-stu-id="a99eb-141">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="a99eb-142">Další informace o předávání typů odkazů odkazem a hodnotou naleznete [v tématu Předávání parametrů typu odkazu](./passing-reference-type-parameters.md) a typů [odkazů](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-142">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="a99eb-143">Vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="a99eb-143">Return values</span></span>

<span data-ttu-id="a99eb-144">Metody můžete vrátit hodnotu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-144">Methods can return a value to the caller.</span></span> <span data-ttu-id="a99eb-145">Pokud návratový typ, typ uvedený před názvem `void`metody, není , metoda `return` může vrátit hodnotu pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="a99eb-145">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="a99eb-146">Příkaz s `return` klíčovým slovem následovaný hodnotou, která odpovídá návratový typ vrátí tuto hodnotu volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-146">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="a99eb-147">Hodnota může být vrácena volajícímu podle hodnoty nebo, počínaje C# 7.0, [odkazem](ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-147">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="a99eb-148">Hodnoty jsou vráceny volajícímu `ref` odkazem, pokud je klíčové slovo `return` použito v podpisu metody a následuje každé klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a99eb-148">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="a99eb-149">Například následující metoda podpis a příkaz return označují, `estDistance` že metoda vrátí názvy proměnných odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="a99eb-149">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="a99eb-150">Klíčové `return` slovo také zastaví provádění metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-150">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="a99eb-151">Pokud je `void`návratový `return` typ , příkaz bez hodnoty je stále užitečné zastavit provádění metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-151">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="a99eb-152">Bez `return` klíčového slova se metoda zastaví při dosažení konce bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-152">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="a99eb-153">Metody s nevoid návratový typ jsou `return` nutné použít klíčové slovo vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-153">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="a99eb-154">Například tyto dvě metody `return` používají klíčové slovo k vrácení celá čísla:</span><span class="sxs-lookup"><span data-stu-id="a99eb-154">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="a99eb-155">Chcete-li použít hodnotu vrácenou z metody, může metoda volání použít metodu, která se nazývá kdekoli, že by stačila hodnota stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-155">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="a99eb-156">Návratovou hodnotu můžete také přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="a99eb-156">You can also assign the return value to a variable.</span></span> <span data-ttu-id="a99eb-157">Například následující dva příklady kódu dosáhnout stejného cíle:</span><span class="sxs-lookup"><span data-stu-id="a99eb-157">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="a99eb-158">Použití místní proměnné, v `result`tomto případě , k uložení hodnoty je volitelné.</span><span class="sxs-lookup"><span data-stu-id="a99eb-158">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="a99eb-159">Může pomoci čitelnost kódu nebo může být nezbytné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-159">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="a99eb-160">Chcete-li použít hodnotu vrácenou odkazem z metody, musíte deklarovat místní proměnnou [ref,](ref-returns.md#ref-locals) pokud máte v úmyslu změnit její hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-160">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="a99eb-161">Pokud například `Planet.GetEstimatedDistance` metoda vrátí <xref:System.Double> hodnotu odkazem, můžete ji definovat jako místní proměnnou ref s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a99eb-161">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="a99eb-162">Vrácení vícerozměrné pole z metody `M`, která upravuje obsah pole není nutné, pokud volající funkce `M`předána pole do .</span><span class="sxs-lookup"><span data-stu-id="a99eb-162">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="a99eb-163">Můžete vrátit výsledné pole `M` z pro dobrý styl nebo funkční tok hodnot, ale není nutné, protože C# předá všechny typy odkazů podle hodnoty a hodnota odkazu pole je ukazatel na pole.</span><span class="sxs-lookup"><span data-stu-id="a99eb-163">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="a99eb-164">V metodě `M`jsou všechny změny obsahu pole pozorovatelné libovolným kódem, který má odkaz na pole, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a99eb-164">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="a99eb-165">Další informace naleznete v tématu [return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-165">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="a99eb-166">Asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="a99eb-166">Async methods</span></span>

<span data-ttu-id="a99eb-167">Pomocí funkce async můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ručnírozdělení kódu mezi více metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="a99eb-167">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="a99eb-168">Pokud označíte metodu s [asynchronním](../../language-reference/keywords/async.md) modifikátorem, můžete použít operátor [await](../../language-reference/operators/await.md) v metodě.</span><span class="sxs-lookup"><span data-stu-id="a99eb-168">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="a99eb-169">Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh metody je pozastaven, dokud nebude dokončena očekávaná úloha.</span><span class="sxs-lookup"><span data-stu-id="a99eb-169">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="a99eb-170">Po dokončení úlohy může spuštění pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="a99eb-170">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="a99eb-171">Asynchronní metoda se vrátí volajícímu, když buď narazí na první očekávaný objekt, který ještě není dokončen, nebo se dostane na konec asynchronní metody, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="a99eb-171">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="a99eb-172">Asynchronní metoda může mít <xref:System.Threading.Tasks.Task%601>návratový typ , <xref:System.Threading.Tasks.Task>nebo void.</span><span class="sxs-lookup"><span data-stu-id="a99eb-172">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="a99eb-173">Typ vrácení void se používá především k definování obslužné rutiny událostí, kde je vyžadován prázdný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a99eb-173">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="a99eb-174">Asynchronní metoda, která vrátí void nelze čekat a volající metody vrácení void nemůže zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="a99eb-174">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="a99eb-175">V následujícím příkladu je asynchronní metoda, `DelayAsync` <xref:System.Threading.Tasks.Task%601>která má návratový typ .</span><span class="sxs-lookup"><span data-stu-id="a99eb-175">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a99eb-176">`DelayAsync`má `return` příkaz, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="a99eb-176">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="a99eb-177">Proto musí mít `DelayAsync` deklarace metody `Task<int>`návratový typ .</span><span class="sxs-lookup"><span data-stu-id="a99eb-177">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="a99eb-178">Vzhledem k `Task<int>`tomu, že `await` návratový `DoSomethingAsync` typ je , vyhodnocení výrazu v `int result = await delayTask`vytváří celé číslo jako následující příkaz ukazuje: .</span><span class="sxs-lookup"><span data-stu-id="a99eb-178">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="a99eb-179">Metoda `startButton_Click` je příkladem asynchronní metody, která má návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="a99eb-179">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="a99eb-180">Protože `DoSomethingAsync` je asynchronní metoda, `DoSomethingAsync` úkol pro volání musí být očekávány, `await DoSomethingAsync();`jak ukazuje následující příkaz: .</span><span class="sxs-lookup"><span data-stu-id="a99eb-180">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="a99eb-181">Metoda `startButton_Click` musí být definována modifikátorem, `async` protože metoda má `await` výraz.</span><span class="sxs-lookup"><span data-stu-id="a99eb-181">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

<span data-ttu-id="a99eb-182">Asynchronní metoda nemůže deklarovat žádné parametry [ref](../../language-reference/keywords/ref.md) nebo [out,](../../language-reference/keywords/out-parameter-modifier.md) ale může volat metody, které mají takové parametry.</span><span class="sxs-lookup"><span data-stu-id="a99eb-182">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="a99eb-183">Další informace o asynchronních metodách naleznete [v tématu Asynchronní programování s asynchronní a await](../concepts/async/index.md), [Řízení toku v asynchronních programech](../concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-183">For more information about async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md), [Control Flow in Async Programs](../concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="a99eb-184">Definice těla výrazu</span><span class="sxs-lookup"><span data-stu-id="a99eb-184">Expression body definitions</span></span>

<span data-ttu-id="a99eb-185">Je běžné mít definice metod, které jednoduše vrátit okamžitě s výsledkem výrazu nebo které mají jeden příkaz jako tělo metody.</span><span class="sxs-lookup"><span data-stu-id="a99eb-185">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="a99eb-186">Existuje zástupce syntaxe pro definování `=>`těchto metod pomocí :</span><span class="sxs-lookup"><span data-stu-id="a99eb-186">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="a99eb-187">Pokud metoda `void` vrátí nebo je asynchronní metoda, pak tělo metody musí být výraz příkazu (stejné jako u lambdas).</span><span class="sxs-lookup"><span data-stu-id="a99eb-187">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="a99eb-188">Pro vlastnosti a indexery musí být jen pro `get` čtení a nepoužíváte klíčové slovo přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="a99eb-188">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="a99eb-189">Iterátory</span><span class="sxs-lookup"><span data-stu-id="a99eb-189">Iterators</span></span>

<span data-ttu-id="a99eb-190">Iterátor provádí vlastní iteraci přes kolekci, jako je například seznam nebo pole.</span><span class="sxs-lookup"><span data-stu-id="a99eb-190">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="a99eb-191">Iterátor používá yield [return](../../language-reference/keywords/yield.md) prohlášení vrátit každý prvek jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="a99eb-191">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="a99eb-192">Když je dosaženo výnos [return](../../language-reference/keywords/yield.md) prohlášení, aktuální umístění v kódu je zapamatována.</span><span class="sxs-lookup"><span data-stu-id="a99eb-192">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="a99eb-193">Spuštění je restartován z tohoto umístění při restartování iterátoru při příštím volání.</span><span class="sxs-lookup"><span data-stu-id="a99eb-193">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="a99eb-194">Volání iterátoru z kódu klienta pomocí [foreach](../../language-reference/keywords/foreach-in.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="a99eb-194">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="a99eb-195">Návratový typ iterátoru může <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>být <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>, , nebo .</span><span class="sxs-lookup"><span data-stu-id="a99eb-195">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="a99eb-196">Další informace naleznete v tématu [Iterators](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="a99eb-196">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a99eb-197">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a99eb-197">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a99eb-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="a99eb-198">See also</span></span>

- [<span data-ttu-id="a99eb-199">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a99eb-199">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a99eb-200">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="a99eb-200">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="a99eb-201">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a99eb-201">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a99eb-202">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="a99eb-202">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="a99eb-203">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="a99eb-203">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="a99eb-204">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="a99eb-204">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="a99eb-205">params</span><span class="sxs-lookup"><span data-stu-id="a99eb-205">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="a99eb-206">return</span><span class="sxs-lookup"><span data-stu-id="a99eb-206">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="a99eb-207">ven</span><span class="sxs-lookup"><span data-stu-id="a99eb-207">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="a99eb-208">ref</span><span class="sxs-lookup"><span data-stu-id="a99eb-208">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="a99eb-209">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="a99eb-209">Passing Parameters</span></span>](passing-parameters.md)
