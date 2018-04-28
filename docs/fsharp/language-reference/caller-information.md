---
title: 'Informace o subjektu volajícím (F #)'
description: Popisuje, jak použít volající informace Argument atributy získat informace o subjektu volajícím z metody.
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 840c6c6308c55fe2a2dbefd52b159a32fb92f787
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="caller-information"></a><span data-ttu-id="272c2-103">Informace o subjektu volajícím</span><span class="sxs-lookup"><span data-stu-id="272c2-103">Caller information</span></span>

<span data-ttu-id="272c2-104">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="272c2-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="272c2-105">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="272c2-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="272c2-106">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="272c2-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="272c2-107">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="272c2-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="272c2-108">Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) obor názvů:</span><span class="sxs-lookup"><span data-stu-id="272c2-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="272c2-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="272c2-109">Attribute</span></span>|<span data-ttu-id="272c2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="272c2-110">Description</span></span>|<span data-ttu-id="272c2-111">Typ</span><span class="sxs-lookup"><span data-stu-id="272c2-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="272c2-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="272c2-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="272c2-113">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="272c2-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="272c2-114">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="272c2-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="272c2-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="272c2-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="272c2-116">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="272c2-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="272c2-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="272c2-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="272c2-118">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="272c2-118">Method or property name of the caller.</span></span> <span data-ttu-id="272c2-119">Najdete v části názvy členů později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="272c2-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="272c2-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="272c2-120">Example</span></span>

<span data-ttu-id="272c2-121">Následující příklad ukazuje, jak můžete pomocí těchto atributů pro trasování volající.</span><span class="sxs-lookup"><span data-stu-id="272c2-121">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="272c2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="272c2-122">Remarks</span></span>

<span data-ttu-id="272c2-123">Atributy s informacemi volající je použít jenom pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="272c2-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="272c2-124">Je třeba zadat explicitní hodnotu pro každý volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="272c2-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="272c2-125">Informace o volajícím atributy způsobit kompilátoru pro zápis správné hodnoty pro každý volitelný parametr dekorované s atributem volající informace.</span><span class="sxs-lookup"><span data-stu-id="272c2-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="272c2-126">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="272c2-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="272c2-127">Na rozdíl od výsledky [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) maskováním nemá vliv vlastnost pro výjimky, výsledky.</span><span class="sxs-lookup"><span data-stu-id="272c2-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="272c2-128">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="272c2-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="272c2-129">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="272c2-129">Member names</span></span>

<span data-ttu-id="272c2-130">Můžete použít [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut Vyhněte se zadání název člena jako `String` argument volané metodě.</span><span class="sxs-lookup"><span data-stu-id="272c2-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="272c2-131">Pomocí tohoto postupu se vyhnout problém, který přejmenovat refaktoring nezmění `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="272c2-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="272c2-132">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="272c2-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="272c2-133">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="272c2-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="272c2-134">Implementace [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) rozhraní při vytváření vazby data.</span><span class="sxs-lookup"><span data-stu-id="272c2-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="272c2-135">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="272c2-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="272c2-136">Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut, musíte zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="272c2-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="272c2-137">Následující graf zobrazuje názvy, které jsou vráceny při použití atributu CallerMemberName člena.</span><span class="sxs-lookup"><span data-stu-id="272c2-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="272c2-138">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="272c2-138">Calls occurs within</span></span>|<span data-ttu-id="272c2-139">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="272c2-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="272c2-140">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="272c2-140">Method, property, or event</span></span>|<span data-ttu-id="272c2-141">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="272c2-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="272c2-142">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="272c2-142">Constructor</span></span>|<span data-ttu-id="272c2-143">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="272c2-143">The string ".ctor"</span></span>|
|<span data-ttu-id="272c2-144">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="272c2-144">Static constructor</span></span>|<span data-ttu-id="272c2-145">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="272c2-145">The string ".cctor"</span></span>|
|<span data-ttu-id="272c2-146">Destruktor</span><span class="sxs-lookup"><span data-stu-id="272c2-146">Destructor</span></span>|<span data-ttu-id="272c2-147">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="272c2-147">The string "Finalize"</span></span>|
|<span data-ttu-id="272c2-148">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="272c2-148">User-defined operators or conversions</span></span>|<span data-ttu-id="272c2-149">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="272c2-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="272c2-150">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="272c2-150">Attribute constructor</span></span>|<span data-ttu-id="272c2-151">Název členu, na který se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="272c2-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="272c2-152">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="272c2-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="272c2-153">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="272c2-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="272c2-154">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="272c2-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="272c2-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="272c2-155">See also</span></span>
 [<span data-ttu-id="272c2-156">Atributy</span><span class="sxs-lookup"><span data-stu-id="272c2-156">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="272c2-157">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="272c2-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="272c2-158">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="272c2-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
