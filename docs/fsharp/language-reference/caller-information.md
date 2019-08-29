---
title: Informace o volajícím
description: Popisuje způsob použití atributů argumentu informace o volajícím k získání informací o volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: e7bbc3830a95bd25cfc2fb369b204d367b775815
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106583"
---
# <a name="caller-information"></a><span data-ttu-id="67522-103">Informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="67522-103">Caller information</span></span>

<span data-ttu-id="67522-104">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="67522-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="67522-105">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="67522-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="67522-106">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="67522-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="67522-107">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="67522-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="67522-108">V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v oboru názvů [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :</span><span class="sxs-lookup"><span data-stu-id="67522-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="67522-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="67522-109">Attribute</span></span>|<span data-ttu-id="67522-110">Popis</span><span class="sxs-lookup"><span data-stu-id="67522-110">Description</span></span>|<span data-ttu-id="67522-111">type</span><span class="sxs-lookup"><span data-stu-id="67522-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="67522-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="67522-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="67522-113">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="67522-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="67522-114">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="67522-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="67522-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="67522-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="67522-116">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="67522-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="67522-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="67522-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="67522-118">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="67522-118">Method or property name of the caller.</span></span> <span data-ttu-id="67522-119">Viz část názvy členů dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="67522-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="67522-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="67522-120">Example</span></span>

<span data-ttu-id="67522-121">Následující příklad ukazuje, jak můžete tyto atributy použít k trasování volajícího.</span><span class="sxs-lookup"><span data-stu-id="67522-121">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="67522-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67522-122">Remarks</span></span>

<span data-ttu-id="67522-123">Atributy informací o volajícím se dají použít jenom u volitelných parametrů.</span><span class="sxs-lookup"><span data-stu-id="67522-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="67522-124">Atributy informace o volajícím způsobí, že kompilátor zapíše správnou hodnotu pro každý volitelný parametr upravený pomocí atributu info volajícího.</span><span class="sxs-lookup"><span data-stu-id="67522-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="67522-125">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="67522-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="67522-126">Na rozdíl od výsledků vlastnosti [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) pro výjimky nejsou výsledky ovlivněny zmatením.</span><span class="sxs-lookup"><span data-stu-id="67522-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="67522-127">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="67522-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="67522-128">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="67522-128">Member names</span></span>

<span data-ttu-id="67522-129">[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) Atribut lze použít k zamezení zadání názvu člena `String` jako argumentu volané metody.</span><span class="sxs-lookup"><span data-stu-id="67522-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="67522-130">Pomocí této techniky se vyhnete problému s tím, že Refaktoring přejmenování `String` hodnoty nemění.</span><span class="sxs-lookup"><span data-stu-id="67522-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="67522-131">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="67522-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="67522-132">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="67522-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="67522-133">Implementace rozhraní [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) při vázání dat</span><span class="sxs-lookup"><span data-stu-id="67522-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="67522-134">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="67522-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="67522-135">[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) Bez atributu je nutné zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="67522-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="67522-136">Následující graf znázorňuje názvy členů, které jsou vráceny při použití atributu CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="67522-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="67522-137">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="67522-137">Calls occurs within</span></span>|<span data-ttu-id="67522-138">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="67522-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="67522-139">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="67522-139">Method, property, or event</span></span>|<span data-ttu-id="67522-140">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="67522-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="67522-141">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="67522-141">Constructor</span></span>|<span data-ttu-id="67522-142">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="67522-142">The string ".ctor"</span></span>|
|<span data-ttu-id="67522-143">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="67522-143">Static constructor</span></span>|<span data-ttu-id="67522-144">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="67522-144">The string ".cctor"</span></span>|
|<span data-ttu-id="67522-145">Destruktor</span><span class="sxs-lookup"><span data-stu-id="67522-145">Destructor</span></span>|<span data-ttu-id="67522-146">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="67522-146">The string "Finalize"</span></span>|
|<span data-ttu-id="67522-147">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="67522-147">User-defined operators or conversions</span></span>|<span data-ttu-id="67522-148">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="67522-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="67522-149">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="67522-149">Attribute constructor</span></span>|<span data-ttu-id="67522-150">Název členu, na který se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="67522-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="67522-151">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="67522-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="67522-152">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="67522-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="67522-153">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="67522-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="67522-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67522-154">See also</span></span>

- [<span data-ttu-id="67522-155">Atributy</span><span class="sxs-lookup"><span data-stu-id="67522-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="67522-156">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="67522-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="67522-157">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="67522-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
