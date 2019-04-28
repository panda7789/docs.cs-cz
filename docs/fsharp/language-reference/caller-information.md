---
title: Informace o volajícím
description: Popisuje způsob použití atributů Argument informace o volajícím získat informace o volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 13092df453b684d3ed4a93c842ea49c066157cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703163"
---
# <a name="caller-information"></a><span data-ttu-id="2bf65-103">Informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="2bf65-103">Caller information</span></span>

<span data-ttu-id="2bf65-104">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="2bf65-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="2bf65-105">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="2bf65-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="2bf65-106">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2bf65-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="2bf65-107">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2bf65-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="2bf65-108">V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) obor názvů:</span><span class="sxs-lookup"><span data-stu-id="2bf65-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="2bf65-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="2bf65-109">Attribute</span></span>|<span data-ttu-id="2bf65-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2bf65-110">Description</span></span>|<span data-ttu-id="2bf65-111">Type</span><span class="sxs-lookup"><span data-stu-id="2bf65-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="2bf65-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="2bf65-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="2bf65-113">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="2bf65-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="2bf65-114">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2bf65-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="2bf65-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="2bf65-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="2bf65-116">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="2bf65-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="2bf65-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="2bf65-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="2bf65-118">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="2bf65-118">Method or property name of the caller.</span></span> <span data-ttu-id="2bf65-119">Dále v tomto tématu v části názvy členů.</span><span class="sxs-lookup"><span data-stu-id="2bf65-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="2bf65-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bf65-120">Example</span></span>

<span data-ttu-id="2bf65-121">Následující příklad ukazuje, jak můžete použít tyto atributy pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="2bf65-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a><span data-ttu-id="2bf65-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bf65-122">Remarks</span></span>

<span data-ttu-id="2bf65-123">Atributy informace o volajícím můžete použít jenom pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="2bf65-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="2bf65-124">Atributy informace o volajícím způsobit, že kompilátor pro zápis správné hodnoty pro každý volitelný parametr upravené pomocí atributu informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="2bf65-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="2bf65-125">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2bf65-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="2bf65-126">Na rozdíl od výsledků [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) pro výjimky, výsledky nejsou ovlivněny obfuskací.</span><span class="sxs-lookup"><span data-stu-id="2bf65-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="2bf65-127">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="2bf65-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="2bf65-128">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="2bf65-128">Member names</span></span>

<span data-ttu-id="2bf65-129">Můžete použít [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut vyhnout zadávání názvu členu jako `String` argumentů volané metody.</span><span class="sxs-lookup"><span data-stu-id="2bf65-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="2bf65-130">Tímto způsobem se vyhnete problému, která se refaktoring přejmenování nezmění `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bf65-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="2bf65-131">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="2bf65-131">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="2bf65-132">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="2bf65-132">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="2bf65-133">Implementace [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) rozhraní při vytvoření vazby mezi daty.</span><span class="sxs-lookup"><span data-stu-id="2bf65-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="2bf65-134">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="2bf65-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="2bf65-135">Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut, musíte zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="2bf65-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="2bf65-136">Následující graf ukazuje názvy, které jsou vráceny při použití atributu CallerMemberName členů.</span><span class="sxs-lookup"><span data-stu-id="2bf65-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="2bf65-137">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="2bf65-137">Calls occurs within</span></span>|<span data-ttu-id="2bf65-138">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="2bf65-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="2bf65-139">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="2bf65-139">Method, property, or event</span></span>|<span data-ttu-id="2bf65-140">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="2bf65-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="2bf65-141">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="2bf65-141">Constructor</span></span>|<span data-ttu-id="2bf65-142">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="2bf65-142">The string ".ctor"</span></span>|
|<span data-ttu-id="2bf65-143">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="2bf65-143">Static constructor</span></span>|<span data-ttu-id="2bf65-144">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="2bf65-144">The string ".cctor"</span></span>|
|<span data-ttu-id="2bf65-145">Destruktor</span><span class="sxs-lookup"><span data-stu-id="2bf65-145">Destructor</span></span>|<span data-ttu-id="2bf65-146">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="2bf65-146">The string "Finalize"</span></span>|
|<span data-ttu-id="2bf65-147">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="2bf65-147">User-defined operators or conversions</span></span>|<span data-ttu-id="2bf65-148">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="2bf65-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="2bf65-149">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="2bf65-149">Attribute constructor</span></span>|<span data-ttu-id="2bf65-150">Název členu, na který se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="2bf65-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="2bf65-151">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="2bf65-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="2bf65-152">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="2bf65-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="2bf65-153">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="2bf65-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2bf65-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bf65-154">See also</span></span>

- [<span data-ttu-id="2bf65-155">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bf65-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="2bf65-156">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="2bf65-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="2bf65-157">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="2bf65-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
