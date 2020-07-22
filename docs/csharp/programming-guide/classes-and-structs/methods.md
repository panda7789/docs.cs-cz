---
title: Metody – Průvodce programováním v C#
description: Metoda v jazyce C# je blok kódu, který obsahuje řadu příkazů. Program spouští příkazy voláním metody a zadáním argumentů.
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: db35b48d4d7e70a54b38342e79fa2881b3857bd7
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864147"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="6d78d-104">Metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6d78d-104">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="6d78d-105">Metoda je blok kódu, který obsahuje řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="6d78d-105">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="6d78d-106">Program způsobí, že budou příkazy provedeny voláním metody a zadáním požadovaných argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-106">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="6d78d-107">V jazyce C# je každé spuštění instrukcí provedeno v kontextu metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-107">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="6d78d-108">`Main`Metoda je vstupním bodem pro každou aplikaci jazyka C# a je volána modulem CLR (Common Language Runtime) při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-108">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="6d78d-109">Tento článek popisuje pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-109">This article discusses named methods.</span></span> <span data-ttu-id="6d78d-110">Informace o anonymních funkcích naleznete v tématu [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-110">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="6d78d-111">Signatury metod</span><span class="sxs-lookup"><span data-stu-id="6d78d-111">Method signatures</span></span>

<span data-ttu-id="6d78d-112">Metody jsou deklarovány ve [třídě](../../language-reference/keywords/class.md), [struktuře](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../interfaces/index.md) zadáním úrovně přístupu, jako jsou `public` nebo, volitelné modifikátory, jako je například `private` `abstract` nebo `sealed` , návratová hodnota, název metody a všechny parametry metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-112">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="6d78d-113">Tyto části jsou společně signaturou metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-113">These parts together are the signature of the method.</span></span>

> [!NOTE]
> <span data-ttu-id="6d78d-114">Návratový typ metody není součástí signatury metody pro účely přetěžování metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-114">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="6d78d-115">Je však součástí signatury metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="6d78d-115">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="6d78d-116">Parametry metody jsou uzavřeny v závorkách a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="6d78d-116">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="6d78d-117">Prázdné kulaté závorky označují, že metoda nepožaduje žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="6d78d-117">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="6d78d-118">Tato třída obsahuje čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="6d78d-118">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="6d78d-119">Přístup k metodě</span><span class="sxs-lookup"><span data-stu-id="6d78d-119">Method access</span></span>

<span data-ttu-id="6d78d-120">Volání metody v objektu se podobá přístupu k poli.</span><span class="sxs-lookup"><span data-stu-id="6d78d-120">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="6d78d-121">Za název objektu přidejte tečku, název metody a závorky.</span><span class="sxs-lookup"><span data-stu-id="6d78d-121">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="6d78d-122">Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="6d78d-122">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="6d78d-123">Metody `Motorcycle` třídy lze proto volat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d78d-123">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="6d78d-124">Parametry metody vs. argumenty</span><span class="sxs-lookup"><span data-stu-id="6d78d-124">Method parameters vs. arguments</span></span>

<span data-ttu-id="6d78d-125">Definice metody určuje názvy a typy parametrů, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="6d78d-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="6d78d-126">Když volání kódu volá metodu, poskytuje konkrétní hodnoty nazvané argumenty pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="6d78d-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="6d78d-127">Argumenty musí být kompatibilní s typem parametru, ale název argumentu (pokud existuje) použitý v volajícím kódu nemusí být stejný jako parametr s názvem definovaným v metodě.</span><span class="sxs-lookup"><span data-stu-id="6d78d-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="6d78d-128">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6d78d-128">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="6d78d-129">Předávání odkazem vs. předání podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="6d78d-129">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="6d78d-130">Ve výchozím nastavení, když je instance [hodnotového typu](../../language-reference/builtin-types/value-types.md) předána metodě, je její kopie předána namísto samotné instance.</span><span class="sxs-lookup"><span data-stu-id="6d78d-130">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="6d78d-131">Proto změny argumentu nemají žádný vliv na původní instanci v volání metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-131">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="6d78d-132">Chcete-li předat instanci typu hodnoty odkazem, použijte `ref` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6d78d-132">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="6d78d-133">Další informace naleznete v tématu [předávání parametrů typu hodnoty](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-133">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="6d78d-134">Je-li objekt typu odkazu předán metodě, odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="6d78d-134">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="6d78d-135">To znamená, že metoda nepřijímá samotný objekt, ale argument, který označuje umístění objektu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-135">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="6d78d-136">Pokud změníte člena objektu pomocí tohoto odkazu, změna se projeví v argumentu volající metody, a to i v případě, že předáte objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6d78d-136">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="6d78d-137">Můžete vytvořit odkazový typ pomocí `class` klíčového slova, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="6d78d-137">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="6d78d-138">Nyní Pokud předáte objekt, který je založen na tomto typu pro metodu, odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="6d78d-138">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="6d78d-139">Následující příklad předává objekt typu `SampleRefType` metodě `ModifyObject` :</span><span class="sxs-lookup"><span data-stu-id="6d78d-139">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="6d78d-140">Příklad v podstatě totéž jako předchozí příklad v tom, že předává argument podle hodnoty metodě.</span><span class="sxs-lookup"><span data-stu-id="6d78d-140">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="6d78d-141">Ale vzhledem k tomu, že se používá typ odkazu, je výsledek jiný.</span><span class="sxs-lookup"><span data-stu-id="6d78d-141">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="6d78d-142">Úpravy, které jsou provedeny v `ModifyObject` `value` poli parametru, `obj` , také změní `value` pole argumentu `rt` v `TestRefType` metodě.</span><span class="sxs-lookup"><span data-stu-id="6d78d-142">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="6d78d-143">`TestRefType`Metoda zobrazí 33 jako výstup.</span><span class="sxs-lookup"><span data-stu-id="6d78d-143">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="6d78d-144">Další informace o tom, jak předat typy odkazu odkazem a podle hodnoty, naleznete v tématu [předávání parametrů typu odkazu](./passing-reference-type-parameters.md) a [odkazových typů](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-144">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="6d78d-145">Vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="6d78d-145">Return values</span></span>

<span data-ttu-id="6d78d-146">Metody mohou vracet hodnotu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-146">Methods can return a value to the caller.</span></span> <span data-ttu-id="6d78d-147">Pokud návratový typ, typ uvedený před názvem metody, není `void` , metoda může vracet hodnotu pomocí `return` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="6d78d-147">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="6d78d-148">Příkaz s `return` klíčovým slovem následovaným hodnotou, která odpovídá typu vrácené hodnoty, vrátí tuto hodnotu volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-148">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="6d78d-149">Hodnota může být vrácena volajícímu podle hodnoty nebo počínaje jazykem C# 7,0 [odkazem](ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-149">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="6d78d-150">Hodnoty se vrátí volajícímu pomocí odkazu, pokud `ref` se klíčové slovo používá v signatuře metody a následuje za každým `return` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="6d78d-150">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="6d78d-151">Například následující signatura metody a příkaz return označují, že metoda vrací názvy proměnných `estDistance` odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="6d78d-151">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="6d78d-152">`return`Klíčové slovo také zastaví provádění metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-152">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="6d78d-153">Pokud je návratový typ `void` , `return` příkaz bez hodnoty je stále užitečný k zastavení provádění metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-153">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="6d78d-154">Bez `return` klíčového slova, Metoda zastaví provádění, když dosáhne konce bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-154">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="6d78d-155">Metody s návratovým typem, který není typu void, jsou vyžadovány k použití `return` klíčového slova k vrácení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6d78d-155">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="6d78d-156">Například tyto dvě metody používají `return` klíčové slovo k vrácení celých čísel:</span><span class="sxs-lookup"><span data-stu-id="6d78d-156">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="6d78d-157">Chcete-li použít hodnotu vrácenou metodou, volající metoda může použít samotné volání metody kdekoli kdekoliv, kde bude stačit hodnota stejného typu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-157">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="6d78d-158">Vrácenou hodnotu můžete také přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="6d78d-158">You can also assign the return value to a variable.</span></span> <span data-ttu-id="6d78d-159">Například následující dva příklady kódu mají stejný cíl:</span><span class="sxs-lookup"><span data-stu-id="6d78d-159">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="6d78d-160">Použití místní proměnné v tomto případě `result` pro uložení hodnoty je volitelné.</span><span class="sxs-lookup"><span data-stu-id="6d78d-160">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="6d78d-161">Může to usnadnit čitelnost kódu nebo může být nutné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-161">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="6d78d-162">Chcete-li použít hodnotu vrácenou odkazem z metody, je nutné deklarovat [místní proměnnou ref](ref-returns.md#ref-locals) , pokud máte v úmyslu změnit její hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-162">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="6d78d-163">Například pokud `Planet.GetEstimatedDistance` Metoda vrátí <xref:System.Double> hodnotu odkazem, můžete ji definovat jako místní proměnnou ref s kódem podobným následujícímu:</span><span class="sxs-lookup"><span data-stu-id="6d78d-163">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="6d78d-164">Vrácení multidimenzionálního pole z metody, `M` které upraví obsah pole, není nutné, pokud volající funkce předala pole do `M` .</span><span class="sxs-lookup"><span data-stu-id="6d78d-164">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="6d78d-165">Výsledné pole můžete vracet z `M` pro dobrý styl nebo funkční tok hodnot, ale není nutné, protože C# předává všechny typy odkazů podle hodnoty a hodnota odkazu na pole je ukazatel na pole.</span><span class="sxs-lookup"><span data-stu-id="6d78d-165">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="6d78d-166">V metodě `M` jsou jakékoli změny v obsahu pole pozorovatelované jakýmkoli kódem, který má odkaz na pole, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6d78d-166">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

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

<span data-ttu-id="6d78d-167">Další informace naleznete v tématu [return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-167">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="6d78d-168">Asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="6d78d-168">Async methods</span></span>

<span data-ttu-id="6d78d-169">Pomocí asynchronní funkce můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ruční rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="6d78d-169">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="6d78d-170">Pokud označíte metodu pomocí modifikátoru [Async](../../language-reference/keywords/async.md) , můžete použít operátor [await](../../language-reference/operators/await.md) v metodě.</span><span class="sxs-lookup"><span data-stu-id="6d78d-170">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="6d78d-171">Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh v metodě je pozastaven, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="6d78d-171">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="6d78d-172">Po dokončení úlohy může provádění pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="6d78d-172">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="6d78d-173">Asynchronní metoda se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo získá na konec asynchronní metody, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="6d78d-173">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="6d78d-174">Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.Task> nebo void.</span><span class="sxs-lookup"><span data-stu-id="6d78d-174">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="6d78d-175">Typ vrácené hodnoty void slouží hlavně k definování obslužných rutin událostí, kde je požadován návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="6d78d-175">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="6d78d-176">Asynchronní metoda, která vrací typ void, nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="6d78d-176">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="6d78d-177">V následujícím příkladu `DelayAsync` je asynchronní metoda, která má návratový typ <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="6d78d-177">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6d78d-178">`DelayAsync`obsahuje `return` příkaz, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6d78d-178">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="6d78d-179">Proto deklarace metody `DelayAsync` musí mít návratový typ `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="6d78d-179">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="6d78d-180">Vzhledem k tomu, že návratový typ je `Task<int>` , vyhodnocení `await` výrazu v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `int result = await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="6d78d-180">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="6d78d-181">`startButton_Click`Metoda je příkladem asynchronní metody, která má návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="6d78d-181">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="6d78d-182">Vzhledem k tomu `DoSomethingAsync` , že se jedná o asynchronní metodu, musí být úloha volání metody `DoSomethingAsync` očekávána, jak ukazuje následující příkaz: `await DoSomethingAsync();` .</span><span class="sxs-lookup"><span data-stu-id="6d78d-182">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="6d78d-183">`startButton_Click`Metoda musí být definována s `async` modifikátorem, protože metoda má `await` výraz.</span><span class="sxs-lookup"><span data-stu-id="6d78d-183">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

<span data-ttu-id="6d78d-184">Asynchronní metoda nemůže deklarovat všechny parametry [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) , ale může volat metody, které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="6d78d-184">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="6d78d-185">Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await](../concepts/async/index.md), [řízení toku v asynchronních programech](../concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-185">For more information about async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md), [Control Flow in Async Programs](../concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="6d78d-186">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="6d78d-186">Expression body definitions</span></span>

<span data-ttu-id="6d78d-187">Je běžné mít definice metod, které se jednoduše vrátí s výsledkem výrazu nebo které mají jediný příkaz jako tělo metody.</span><span class="sxs-lookup"><span data-stu-id="6d78d-187">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="6d78d-188">Pro definování takových metod je k dispozici zástupce syntaxe pomocí příkazu `=>` :</span><span class="sxs-lookup"><span data-stu-id="6d78d-188">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="6d78d-189">Pokud metoda vrátí `void` nebo je asynchronní metoda, pak tělo metody musí být výraz příkazu (totéž jako u výrazů lambda).</span><span class="sxs-lookup"><span data-stu-id="6d78d-189">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="6d78d-190">U vlastností a indexerů musí být jen pro čtení a nepoužívejte `get` klíčové slovo přistupující k objektu.</span><span class="sxs-lookup"><span data-stu-id="6d78d-190">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="6d78d-191">Iterátory</span><span class="sxs-lookup"><span data-stu-id="6d78d-191">Iterators</span></span>

<span data-ttu-id="6d78d-192">Iterátor provádí vlastní iteraci v kolekci, jako je například seznam nebo pole.</span><span class="sxs-lookup"><span data-stu-id="6d78d-192">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="6d78d-193">Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého elementu v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="6d78d-193">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="6d78d-194">Při dosažení příkazu [yield return](../../language-reference/keywords/yield.md) se aktuální umístění v kódu pamatuje.</span><span class="sxs-lookup"><span data-stu-id="6d78d-194">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="6d78d-195">Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6d78d-195">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="6d78d-196">Můžete zavolat iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="6d78d-196">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="6d78d-197">Návratový typ iterátoru může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="6d78d-197">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="6d78d-198">Další informace najdete v tématu [iterátory](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6d78d-198">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6d78d-199">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d78d-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6d78d-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d78d-200">See also</span></span>

- [<span data-ttu-id="6d78d-201">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6d78d-201">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6d78d-202">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="6d78d-202">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="6d78d-203">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="6d78d-203">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6d78d-204">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="6d78d-204">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="6d78d-205">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="6d78d-205">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="6d78d-206">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="6d78d-206">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="6d78d-207">params</span><span class="sxs-lookup"><span data-stu-id="6d78d-207">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="6d78d-208">return</span><span class="sxs-lookup"><span data-stu-id="6d78d-208">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="6d78d-209">mimo</span><span class="sxs-lookup"><span data-stu-id="6d78d-209">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="6d78d-210">ref</span><span class="sxs-lookup"><span data-stu-id="6d78d-210">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="6d78d-211">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="6d78d-211">Passing Parameters</span></span>](passing-parameters.md)
