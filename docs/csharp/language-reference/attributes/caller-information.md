---
title: 'C# Rezervované atributy: Sledování informací o volajícím'
ms.date: 04/09/2020
description: Tyto atributy pokyn kompilátor generovat informace o kódu, který volá člena. Pomocí CallerFilePath, CallerLineNumber a CallerMemberName můžete poskytnout podrobné informace o trasování
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389875"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="6d764-104">Vyhrazené atributy: Určení informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="6d764-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="6d764-105">Pomocí atributů info získáte informace o volajícím k metodě.</span><span class="sxs-lookup"><span data-stu-id="6d764-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="6d764-106">Získáte cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a jméno člena volajícího.</span><span class="sxs-lookup"><span data-stu-id="6d764-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="6d764-107">Chcete-li získat informace o volajícím člena, použijte atributy, které jsou použity pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="6d764-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="6d764-108">Každý volitelný parametr určuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d764-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="6d764-109">V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="6d764-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="6d764-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d764-110">Attribute</span></span>|<span data-ttu-id="6d764-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6d764-111">Description</span></span>|<span data-ttu-id="6d764-112">Typ</span><span class="sxs-lookup"><span data-stu-id="6d764-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="6d764-113">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="6d764-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="6d764-114">Úplná cesta je cesta v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6d764-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="6d764-115">Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.</span><span class="sxs-lookup"><span data-stu-id="6d764-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="6d764-116">Název metody nebo název vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="6d764-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="6d764-117">Tyto informace vám pomohou psát trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="6d764-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="6d764-118">Následující příklad ukazuje, jak používat atributy informací o volajícím.</span><span class="sxs-lookup"><span data-stu-id="6d764-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="6d764-119">Při každém volání `TraceMessage` metody informace o volajícím je nahrazen jako argumenty volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="6d764-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="6d764-120">Pro každý volitelný parametr zadáte explicitní výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6d764-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="6d764-121">Atributy informací o volajícím nelze použít na parametry, které nejsou zadány jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="6d764-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="6d764-122">Atributy informací o volajícím nedělají parametr volitelným.</span><span class="sxs-lookup"><span data-stu-id="6d764-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="6d764-123">Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.</span><span class="sxs-lookup"><span data-stu-id="6d764-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="6d764-124">Hodnoty informací o volajícím jsou vyzařovány jako literály do zprostředkujícího jazyka (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="6d764-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="6d764-125">Na rozdíl od <xref:System.Exception.StackTrace%2A> výsledků vlastnosti pro výjimky nejsou ovlivněny obfuskace.</span><span class="sxs-lookup"><span data-stu-id="6d764-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="6d764-126">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="6d764-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="6d764-127">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="6d764-127">Member names</span></span>

<span data-ttu-id="6d764-128">Atribut můžete `CallerMemberName` použít, abyste se vyhnuli `String` zadání názvu člena jako argumentu volané metody.</span><span class="sxs-lookup"><span data-stu-id="6d764-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="6d764-129">Pomocí této techniky se vyhnete problému, že **rename refaktoring** nezmění `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6d764-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="6d764-130">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="6d764-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="6d764-131">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="6d764-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="6d764-132">Implementace rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> při vazby dat.</span><span class="sxs-lookup"><span data-stu-id="6d764-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="6d764-133">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="6d764-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="6d764-134">Bez `CallerMemberName` atributu je nutné zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="6d764-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="6d764-135">Následující graf zobrazuje názvy členů, které `CallerMemberName` jsou vráceny při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="6d764-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="6d764-136">Volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="6d764-136">Calls occur within</span></span>|<span data-ttu-id="6d764-137">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="6d764-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="6d764-138">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="6d764-138">Method, property, or event</span></span>|<span data-ttu-id="6d764-139">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="6d764-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="6d764-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="6d764-140">Constructor</span></span>|<span data-ttu-id="6d764-141">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="6d764-141">The string ".ctor"</span></span>|
|<span data-ttu-id="6d764-142">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="6d764-142">Static constructor</span></span>|<span data-ttu-id="6d764-143">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="6d764-143">The string ".cctor"</span></span>|
|<span data-ttu-id="6d764-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="6d764-144">Destructor</span></span>|<span data-ttu-id="6d764-145">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="6d764-145">The string "Finalize"</span></span>|
|<span data-ttu-id="6d764-146">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="6d764-146">User-defined operators or conversions</span></span>|<span data-ttu-id="6d764-147">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="6d764-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="6d764-148">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="6d764-148">Attribute constructor</span></span>|<span data-ttu-id="6d764-149">Název metody nebo vlastnosti, na kterou je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="6d764-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="6d764-150">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="6d764-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="6d764-151">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="6d764-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="6d764-152">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="6d764-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6d764-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d764-153">See also</span></span>

- [<span data-ttu-id="6d764-154">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="6d764-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="6d764-155">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d764-155">Attributes</span></span>](../../../standard/attributes/index.md)
