---
title: Metody – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 8348e080d833e79dd364aee511ac7d05fb53d1cc
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543557"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="acb38-102">Metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="acb38-102">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="acb38-103">Metoda je blok kódu, který obsahuje řadu příkazů.</span><span class="sxs-lookup"><span data-stu-id="acb38-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="acb38-104">Program způsobí, že budou příkazy provedeny voláním metody a zadáním požadovaných argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="acb38-105">V C#je každá spuštěná instrukce provedena v kontextu metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="acb38-106">Metoda `Main` je vstupním bodem pro každou C# aplikaci a je volána modulem CLR (Common Language Runtime) při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="acb38-106">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="acb38-107">Tento článek popisuje pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-107">This article discusses named methods.</span></span> <span data-ttu-id="acb38-108">Informace o anonymních funkcích naleznete v tématu [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-108">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="acb38-109">Signatury metod</span><span class="sxs-lookup"><span data-stu-id="acb38-109">Method signatures</span></span>

<span data-ttu-id="acb38-110">Metody jsou deklarovány ve [třídě](../../language-reference/keywords/class.md), [struktuře](../../language-reference/keywords/struct.md)nebo [rozhraní](../interfaces/index.md) zadáním úrovně přístupu, jako je například `public` nebo `private`, volitelné modifikátory, jako je například `abstract` nebo `sealed`, návratová hodnota, název metody a všechny parametry metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-110">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/keywords/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="acb38-111">Tyto části jsou společně signaturou metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-111">These parts together are the signature of the method.</span></span>

> [!NOTE]
> <span data-ttu-id="acb38-112">Návratový typ metody není součástí signatury metody pro účely přetěžování metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="acb38-113">Je však součástí signatury metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="acb38-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="acb38-114">Parametry metody jsou uzavřeny v závorkách a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="acb38-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="acb38-115">Prázdné kulaté závorky označují, že metoda nepožaduje žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="acb38-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="acb38-116">Tato třída obsahuje čtyři metody:</span><span class="sxs-lookup"><span data-stu-id="acb38-116">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="acb38-117">Přístup k metodě</span><span class="sxs-lookup"><span data-stu-id="acb38-117">Method access</span></span>

<span data-ttu-id="acb38-118">Volání metody v objektu se podobá přístupu k poli.</span><span class="sxs-lookup"><span data-stu-id="acb38-118">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="acb38-119">Za název objektu přidejte tečku, název metody a závorky.</span><span class="sxs-lookup"><span data-stu-id="acb38-119">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="acb38-120">Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="acb38-120">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="acb38-121">Metody třídy `Motorcycle` lze proto volat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="acb38-121">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="acb38-122">Parametry metody vs. argumenty</span><span class="sxs-lookup"><span data-stu-id="acb38-122">Method parameters vs. arguments</span></span>

<span data-ttu-id="acb38-123">Definice metody určuje názvy a typy parametrů, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="acb38-123">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="acb38-124">Když volání kódu volá metodu, poskytuje konkrétní hodnoty nazvané argumenty pro každý parametr.</span><span class="sxs-lookup"><span data-stu-id="acb38-124">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="acb38-125">Argumenty musí být kompatibilní s typem parametru, ale název argumentu (pokud existuje) použitý v volajícím kódu nemusí být stejný jako parametr s názvem definovaným v metodě.</span><span class="sxs-lookup"><span data-stu-id="acb38-125">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="acb38-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="acb38-126">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="acb38-127">Předávání odkazem vs. předání podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="acb38-127">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="acb38-128">Ve výchozím nastavení, když je instance [hodnotového typu](../../language-reference/builtin-types/value-types.md) předána metodě, je její kopie předána namísto samotné instance.</span><span class="sxs-lookup"><span data-stu-id="acb38-128">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="acb38-129">Proto změny argumentu nemají žádný vliv na původní instanci v volání metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-129">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="acb38-130">Chcete-li předat instanci typu hodnoty odkazem, použijte klíčové slovo `ref`.</span><span class="sxs-lookup"><span data-stu-id="acb38-130">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="acb38-131">Další informace naleznete v tématu [předávání parametrů typu hodnoty](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-131">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="acb38-132">Je-li objekt typu odkazu předán metodě, odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="acb38-132">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="acb38-133">To znamená, že metoda nepřijímá samotný objekt, ale argument, který označuje umístění objektu.</span><span class="sxs-lookup"><span data-stu-id="acb38-133">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="acb38-134">Pokud změníte člena objektu pomocí tohoto odkazu, změna se projeví v argumentu volající metody, a to i v případě, že předáte objekt podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="acb38-134">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="acb38-135">Typ odkazu vytvoříte pomocí klíčového slova `class`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="acb38-135">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="acb38-136">Nyní Pokud předáte objekt, který je založen na tomto typu pro metodu, odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="acb38-136">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="acb38-137">Následující příklad předává objekt typu `SampleRefType` do metody `ModifyObject`:</span><span class="sxs-lookup"><span data-stu-id="acb38-137">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="acb38-138">Příklad v podstatě totéž jako předchozí příklad v tom, že předává argument podle hodnoty metodě.</span><span class="sxs-lookup"><span data-stu-id="acb38-138">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="acb38-139">Ale vzhledem k tomu, že se používá typ odkazu, je výsledek jiný.</span><span class="sxs-lookup"><span data-stu-id="acb38-139">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="acb38-140">Úpravy, které jsou provedeny v `ModifyObject` `value` pole parametru, `obj`, také mění `value` pole argumentu, `rt`v metodě `TestRefType`.</span><span class="sxs-lookup"><span data-stu-id="acb38-140">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="acb38-141">Metoda `TestRefType` zobrazí jako výstup 33.</span><span class="sxs-lookup"><span data-stu-id="acb38-141">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="acb38-142">Další informace o tom, jak předat typy odkazu odkazem a podle hodnoty, naleznete v tématu [předávání parametrů typu odkazu](./passing-reference-type-parameters.md) a [odkazových typů](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-142">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="acb38-143">Vrácené hodnoty</span><span class="sxs-lookup"><span data-stu-id="acb38-143">Return values</span></span>

<span data-ttu-id="acb38-144">Metody mohou vracet hodnotu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="acb38-144">Methods can return a value to the caller.</span></span> <span data-ttu-id="acb38-145">Pokud návratový typ, typ uvedený před názvem metody, není `void`, metoda může vracet hodnotu pomocí klíčového slova `return`.</span><span class="sxs-lookup"><span data-stu-id="acb38-145">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="acb38-146">Příkaz s klíčovým slovem `return` následovaný hodnotou, která odpovídá návratový typ, vrátí tuto hodnotu volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-146">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="acb38-147">Hodnota může být vrácena volajícímu podle hodnoty nebo, počínaje C# 7,0, [odkazem](ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-147">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="acb38-148">Hodnoty se vrátí volajícímu pomocí odkazu, pokud je klíčové slovo `ref` použito v signatuře metody a následuje za každým `return` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="acb38-148">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="acb38-149">Například následující signatura metody a příkaz return označují, že metoda vrátí názvy proměnných `estDistance` odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="acb38-149">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="acb38-150">Klíčové slovo `return` také zastaví provádění metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-150">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="acb38-151">Pokud je návratový typ `void`, je příkaz `return` bez hodnoty stále užitečný k zastavení provádění metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-151">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="acb38-152">Bez klíčového slova `return`, Metoda zastaví provádění, když dosáhne konce bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="acb38-152">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="acb38-153">Pro použití klíčového slova `return` k vrácení hodnoty jsou vyžadovány metody s návratovým typem, který není typu void.</span><span class="sxs-lookup"><span data-stu-id="acb38-153">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="acb38-154">Například tyto dvě metody používají klíčové slovo `return` k vrácení celých čísel:</span><span class="sxs-lookup"><span data-stu-id="acb38-154">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="acb38-155">Chcete-li použít hodnotu vrácenou metodou, volající metoda může použít samotné volání metody kdekoli kdekoliv, kde bude stačit hodnota stejného typu.</span><span class="sxs-lookup"><span data-stu-id="acb38-155">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="acb38-156">Vrácenou hodnotu můžete také přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="acb38-156">You can also assign the return value to a variable.</span></span> <span data-ttu-id="acb38-157">Například následující dva příklady kódu mají stejný cíl:</span><span class="sxs-lookup"><span data-stu-id="acb38-157">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="acb38-158">Použití místní proměnné, v tomto případě `result`pro uložení hodnoty je volitelné.</span><span class="sxs-lookup"><span data-stu-id="acb38-158">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="acb38-159">Může to usnadnit čitelnost kódu nebo může být nutné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-159">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="acb38-160">Chcete-li použít hodnotu vrácenou odkazem z metody, je nutné deklarovat [místní proměnnou ref](ref-returns.md#ref-locals) , pokud máte v úmyslu změnit její hodnotu.</span><span class="sxs-lookup"><span data-stu-id="acb38-160">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="acb38-161">Například pokud metoda `Planet.GetEstimatedDistance` vrátí hodnotu <xref:System.Double> odkazem, můžete ji definovat jako místní proměnnou ref s kódem podobným následujícímu:</span><span class="sxs-lookup"><span data-stu-id="acb38-161">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="acb38-162">Vrácení multidimenzionálního pole z metody, `M`, která upraví obsah pole, není nutné, pokud volající funkce předala pole do `M`.</span><span class="sxs-lookup"><span data-stu-id="acb38-162">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="acb38-163">Výsledné pole můžete vracet z `M` pro dobrý styl nebo funkční tok hodnot, ale není to nutné, protože C# předává všechny odkazové typy podle hodnoty a hodnota odkazu na pole je ukazatel na pole.</span><span class="sxs-lookup"><span data-stu-id="acb38-163">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="acb38-164">V metodě `M`jsou všechny změny obsahu pole pozorovatelně pozorovatelný kódem, který má odkaz na pole, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="acb38-164">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

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

<span data-ttu-id="acb38-165">Další informace naleznete v tématu [return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-165">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="acb38-166">Asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="acb38-166">Async methods</span></span>

<span data-ttu-id="acb38-167">Pomocí asynchronní funkce můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ruční rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="acb38-167">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="acb38-168">Pokud označíte metodu pomocí modifikátoru [Async](../../language-reference/keywords/async.md) , můžete použít operátor [await](../../language-reference/operators/await.md) v metodě.</span><span class="sxs-lookup"><span data-stu-id="acb38-168">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="acb38-169">Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek se vrátí volajícímu a průběh v metodě je pozastaven, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="acb38-169">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="acb38-170">Po dokončení úlohy může provádění pokračovat v metodě.</span><span class="sxs-lookup"><span data-stu-id="acb38-170">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="acb38-171">Asynchronní metoda se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo získá na konec asynchronní metody, podle toho, co nastane dříve.</span><span class="sxs-lookup"><span data-stu-id="acb38-171">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="acb38-172">Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>nebo void.</span><span class="sxs-lookup"><span data-stu-id="acb38-172">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="acb38-173">Typ vrácené hodnoty void slouží hlavně k definování obslužných rutin událostí, kde je požadován návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="acb38-173">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="acb38-174">Asynchronní metoda, která vrací typ void, nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="acb38-174">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="acb38-175">V následujícím příkladu je `DelayAsync` asynchronní metodou, která má návratový typ <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="acb38-175">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="acb38-176">`DelayAsync` má příkaz `return`, který vrací celé číslo.</span><span class="sxs-lookup"><span data-stu-id="acb38-176">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="acb38-177">Proto deklarace metody `DelayAsync` musí mít návratový typ `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="acb38-177">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="acb38-178">Vzhledem k tomu, že návratový typ je `Task<int>`, vyhodnocení výrazu `await` v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující příkaz: `int result = await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="acb38-178">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="acb38-179">Metoda `startButton_Click` je příkladem asynchronní metody, která má návratový typ void.</span><span class="sxs-lookup"><span data-stu-id="acb38-179">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="acb38-180">Vzhledem k tomu, že `DoSomethingAsync` je asynchronní metoda, musí být úloha volání `DoSomethingAsync` očekávána, jak ukazuje následující příkaz: `await DoSomethingAsync();`.</span><span class="sxs-lookup"><span data-stu-id="acb38-180">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="acb38-181">Metoda `startButton_Click` musí být definována modifikátorem `async`, protože metoda má výraz `await`.</span><span class="sxs-lookup"><span data-stu-id="acb38-181">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

<span data-ttu-id="acb38-182">Asynchronní metoda nemůže deklarovat všechny parametry [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) , ale může volat metody, které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="acb38-182">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="acb38-183">Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await](../concepts/async/index.md), [řízení toku v asynchronních programech](../concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-183">For more information about async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md), [Control Flow in Async Programs](../concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="acb38-184">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="acb38-184">Expression body definitions</span></span>

<span data-ttu-id="acb38-185">Je běžné mít definice metod, které se jednoduše vrátí s výsledkem výrazu nebo které mají jediný příkaz jako tělo metody.</span><span class="sxs-lookup"><span data-stu-id="acb38-185">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="acb38-186">Pro definování takových metod pomocí `=>`je k dispozici zástupce syntaxe:</span><span class="sxs-lookup"><span data-stu-id="acb38-186">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="acb38-187">Pokud metoda vrátí `void` nebo je asynchronní metoda, pak tělo metody musí být výraz příkazu (totéž jako u výrazů lambda).</span><span class="sxs-lookup"><span data-stu-id="acb38-187">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="acb38-188">U vlastností a indexerů musí být jen pro čtení a nepoužívejte klíčové slovo přistupující objekt `get`.</span><span class="sxs-lookup"><span data-stu-id="acb38-188">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="acb38-189">Iterátory</span><span class="sxs-lookup"><span data-stu-id="acb38-189">Iterators</span></span>

<span data-ttu-id="acb38-190">Iterátor provádí vlastní iteraci v kolekci, jako je například seznam nebo pole.</span><span class="sxs-lookup"><span data-stu-id="acb38-190">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="acb38-191">Iterátor používá příkaz [yield return](../../language-reference/keywords/yield.md) k vrácení každého elementu v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="acb38-191">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="acb38-192">Při dosažení příkazu [yield return](../../language-reference/keywords/yield.md) se aktuální umístění v kódu pamatuje.</span><span class="sxs-lookup"><span data-stu-id="acb38-192">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="acb38-193">Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.</span><span class="sxs-lookup"><span data-stu-id="acb38-193">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="acb38-194">Můžete zavolat iterátor z klientského kódu pomocí příkazu [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="acb38-194">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="acb38-195">Návratový typ iterátoru může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="acb38-195">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="acb38-196">Další informace najdete v tématu [iterátory](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="acb38-196">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="acb38-197">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="acb38-197">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="acb38-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acb38-198">See also</span></span>

- [<span data-ttu-id="acb38-199">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="acb38-199">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="acb38-200">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="acb38-200">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="acb38-201">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="acb38-201">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="acb38-202">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="acb38-202">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="acb38-203">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="acb38-203">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="acb38-204">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="acb38-204">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="acb38-205">params</span><span class="sxs-lookup"><span data-stu-id="acb38-205">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="acb38-206">return</span><span class="sxs-lookup"><span data-stu-id="acb38-206">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="acb38-207">out</span><span class="sxs-lookup"><span data-stu-id="acb38-207">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="acb38-208">ref</span><span class="sxs-lookup"><span data-stu-id="acb38-208">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="acb38-209">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="acb38-209">Passing Parameters</span></span>](passing-parameters.md)
