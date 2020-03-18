---
title: Informace o volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595349"
---
# <a name="caller-information-c"></a><span data-ttu-id="4233c-102">Informace o volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="4233c-102">Caller Information (C#)</span></span>

<span data-ttu-id="4233c-103">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="4233c-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="4233c-104">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="4233c-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="4233c-105">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="4233c-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="4233c-106">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4233c-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="4233c-107">V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="4233c-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="4233c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4233c-108">Attribute</span></span>|<span data-ttu-id="4233c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4233c-109">Description</span></span>|<span data-ttu-id="4233c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="4233c-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="4233c-111">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="4233c-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="4233c-112">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4233c-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="4233c-113">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="4233c-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="4233c-114">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="4233c-114">Method or property name of the caller.</span></span> <span data-ttu-id="4233c-115">Viz [Jména členů](#member-names) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4233c-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="4233c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4233c-116">Example</span></span>

<span data-ttu-id="4233c-117">Následující příklad ukazuje způsob použití atributů Informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="4233c-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="4233c-118">Při každém volání `TraceMessage` metody informace o volajícím je nahrazen jako argumenty volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="4233c-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="4233c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4233c-119">Remarks</span></span>

<span data-ttu-id="4233c-120">Pro každý volitelný parametr je třeba zadat explicitní výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4233c-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="4233c-121">Atributy Informace o volajícím nelze použít u parametrů, které nejsou uvedeny jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="4233c-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="4233c-122">Atributy Informace o volajícím neučiní parametr volitelným.</span><span class="sxs-lookup"><span data-stu-id="4233c-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="4233c-123">Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.</span><span class="sxs-lookup"><span data-stu-id="4233c-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="4233c-124">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4233c-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="4233c-125">Na rozdíl od <xref:System.Exception.StackTrace%2A> výsledků vlastnosti pro výjimky nejsou ovlivněny obfuskace.</span><span class="sxs-lookup"><span data-stu-id="4233c-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="4233c-126">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="4233c-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="4233c-127">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="4233c-127">Member names</span></span>

<span data-ttu-id="4233c-128">Atribut můžete `CallerMemberName` použít, abyste se vyhnuli `String` zadání názvu člena jako argumentu volané metody.</span><span class="sxs-lookup"><span data-stu-id="4233c-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="4233c-129">Pomocí této techniky se vyhnete problému, že **rename refaktoring** nezmění `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4233c-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="4233c-130">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="4233c-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="4233c-131">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="4233c-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="4233c-132">Implementace rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> při vazby dat.</span><span class="sxs-lookup"><span data-stu-id="4233c-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="4233c-133">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="4233c-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="4233c-134">Bez `CallerMemberName` atributu je nutné zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="4233c-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="4233c-135">Následující graf zobrazuje názvy členů, které `CallerMemberName` jsou vráceny při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="4233c-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="4233c-136">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="4233c-136">Calls occurs within</span></span>|<span data-ttu-id="4233c-137">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="4233c-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="4233c-138">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="4233c-138">Method, property, or event</span></span>|<span data-ttu-id="4233c-139">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="4233c-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="4233c-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="4233c-140">Constructor</span></span>|<span data-ttu-id="4233c-141">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="4233c-141">The string ".ctor"</span></span>|
|<span data-ttu-id="4233c-142">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="4233c-142">Static constructor</span></span>|<span data-ttu-id="4233c-143">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="4233c-143">The string ".cctor"</span></span>|
|<span data-ttu-id="4233c-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="4233c-144">Destructor</span></span>|<span data-ttu-id="4233c-145">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="4233c-145">The string "Finalize"</span></span>|
|<span data-ttu-id="4233c-146">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="4233c-146">User-defined operators or conversions</span></span>|<span data-ttu-id="4233c-147">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="4233c-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="4233c-148">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="4233c-148">Attribute constructor</span></span>|<span data-ttu-id="4233c-149">Název metody nebo vlastnosti, na kterou je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="4233c-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="4233c-150">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="4233c-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="4233c-151">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="4233c-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="4233c-152">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="4233c-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4233c-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="4233c-153">See also</span></span>

- [<span data-ttu-id="4233c-154">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="4233c-154">Attributes (C#)</span></span>](./attributes/index.md)
- [<span data-ttu-id="4233c-155">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="4233c-155">Common Attributes (C#)</span></span>](./attributes/common-attributes.md)
- [<span data-ttu-id="4233c-156">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="4233c-156">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="4233c-157">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="4233c-157">Programming Concepts (C#)</span></span>](./index.md)
