---
title: 'Informace o volajícím (F #)'
description: Popisuje způsob použití atributů Argument informace o volajícím získat informace o volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 0f2f4b16804d9156d234cc29d1f72ebe80a5b556
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577568"
---
# <a name="caller-information"></a><span data-ttu-id="fce74-103">Informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="fce74-103">Caller information</span></span>

<span data-ttu-id="fce74-104">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="fce74-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="fce74-105">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="fce74-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="fce74-106">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="fce74-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="fce74-107">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fce74-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="fce74-108">V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) obor názvů:</span><span class="sxs-lookup"><span data-stu-id="fce74-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="fce74-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="fce74-109">Attribute</span></span>|<span data-ttu-id="fce74-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fce74-110">Description</span></span>|<span data-ttu-id="fce74-111">Typ</span><span class="sxs-lookup"><span data-stu-id="fce74-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="fce74-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="fce74-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="fce74-113">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="fce74-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="fce74-114">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fce74-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="fce74-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="fce74-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="fce74-116">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="fce74-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="fce74-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="fce74-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="fce74-118">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="fce74-118">Method or property name of the caller.</span></span> <span data-ttu-id="fce74-119">Dále v tomto tématu v části názvy členů.</span><span class="sxs-lookup"><span data-stu-id="fce74-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="fce74-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="fce74-120">Example</span></span>

<span data-ttu-id="fce74-121">Následující příklad ukazuje, jak můžete použít tyto atributy pro sledování účastníka.</span><span class="sxs-lookup"><span data-stu-id="fce74-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="fce74-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fce74-122">Remarks</span></span>

<span data-ttu-id="fce74-123">Atributy informace o volajícím můžete použít jenom pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="fce74-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="fce74-124">Je třeba zadat explicitní hodnotu pro každý volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="fce74-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="fce74-125">Atributy informace o volajícím způsobit, že kompilátor pro zápis správné hodnoty pro každý volitelný parametr upravené pomocí atributu informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="fce74-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="fce74-126">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fce74-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="fce74-127">Na rozdíl od výsledků [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) pro výjimky, výsledky nejsou ovlivněny obfuskací.</span><span class="sxs-lookup"><span data-stu-id="fce74-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="fce74-128">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="fce74-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="fce74-129">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="fce74-129">Member names</span></span>

<span data-ttu-id="fce74-130">Můžete použít [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut vyhnout zadávání názvu členu jako `String` argumentů volané metody.</span><span class="sxs-lookup"><span data-stu-id="fce74-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="fce74-131">Tímto způsobem se vyhnete problému, která se refaktoring přejmenování nezmění `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fce74-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="fce74-132">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="fce74-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="fce74-133">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="fce74-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="fce74-134">Implementace [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) rozhraní při vytvoření vazby mezi daty.</span><span class="sxs-lookup"><span data-stu-id="fce74-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="fce74-135">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="fce74-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="fce74-136">Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut, musíte zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="fce74-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="fce74-137">Následující graf ukazuje názvy, které jsou vráceny při použití atributu CallerMemberName členů.</span><span class="sxs-lookup"><span data-stu-id="fce74-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="fce74-138">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="fce74-138">Calls occurs within</span></span>|<span data-ttu-id="fce74-139">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="fce74-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="fce74-140">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="fce74-140">Method, property, or event</span></span>|<span data-ttu-id="fce74-141">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="fce74-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="fce74-142">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="fce74-142">Constructor</span></span>|<span data-ttu-id="fce74-143">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="fce74-143">The string ".ctor"</span></span>|
|<span data-ttu-id="fce74-144">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="fce74-144">Static constructor</span></span>|<span data-ttu-id="fce74-145">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="fce74-145">The string ".cctor"</span></span>|
|<span data-ttu-id="fce74-146">Destruktor</span><span class="sxs-lookup"><span data-stu-id="fce74-146">Destructor</span></span>|<span data-ttu-id="fce74-147">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="fce74-147">The string "Finalize"</span></span>|
|<span data-ttu-id="fce74-148">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="fce74-148">User-defined operators or conversions</span></span>|<span data-ttu-id="fce74-149">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="fce74-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="fce74-150">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="fce74-150">Attribute constructor</span></span>|<span data-ttu-id="fce74-151">Název členu, na který se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="fce74-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="fce74-152">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="fce74-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="fce74-153">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="fce74-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="fce74-154">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="fce74-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fce74-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fce74-155">See also</span></span>

- [<span data-ttu-id="fce74-156">Atributy</span><span class="sxs-lookup"><span data-stu-id="fce74-156">Attributes</span></span>](attributes.md)  
- [<span data-ttu-id="fce74-157">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="fce74-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
- [<span data-ttu-id="fce74-158">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="fce74-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
