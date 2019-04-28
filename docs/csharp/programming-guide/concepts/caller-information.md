---
title: Informace o volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4a0e4d6ecad1863832a33ba91485d0c12675cd57
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668598"
---
# <a name="caller-information-c"></a><span data-ttu-id="0577a-102">Informace o volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="0577a-102">Caller Information (C#)</span></span>

<span data-ttu-id="0577a-103">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="0577a-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="0577a-104">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="0577a-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="0577a-105">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0577a-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="0577a-106">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0577a-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="0577a-107">V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="0577a-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="0577a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0577a-108">Attribute</span></span>|<span data-ttu-id="0577a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0577a-109">Description</span></span>|<span data-ttu-id="0577a-110">Type</span><span class="sxs-lookup"><span data-stu-id="0577a-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="0577a-111">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="0577a-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="0577a-112">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0577a-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="0577a-113">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="0577a-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="0577a-114">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="0577a-114">Method or property name of the caller.</span></span> <span data-ttu-id="0577a-115">Zobrazit [názvy členů](#member-names) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0577a-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="0577a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="0577a-116">Example</span></span>

<span data-ttu-id="0577a-117">Následující příklad ukazuje způsob použití atributů Informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="0577a-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="0577a-118">Pro všechna volání `TraceMessage` metoda, informace o subjektu volajícím nahrazeny v podobě argumentů pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="0577a-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0577a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0577a-119">Remarks</span></span>

<span data-ttu-id="0577a-120">Pro každý volitelný parametr je třeba zadat explicitní výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0577a-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="0577a-121">Atributy Informace o volajícím nelze použít u parametrů, které nejsou uvedeny jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="0577a-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="0577a-122">Atributy Informace o volajícím neučiní parametr volitelným.</span><span class="sxs-lookup"><span data-stu-id="0577a-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="0577a-123">Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.</span><span class="sxs-lookup"><span data-stu-id="0577a-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="0577a-124">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0577a-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="0577a-125">Na rozdíl od výsledků <xref:System.Exception.StackTrace%2A> pro výjimky, výsledky nejsou ovlivněny obfuskací.</span><span class="sxs-lookup"><span data-stu-id="0577a-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="0577a-126">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="0577a-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="0577a-127">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="0577a-127">Member names</span></span>

<span data-ttu-id="0577a-128">Můžete použít `CallerMemberName` atribut vyhnout zadávání názvu členu jako `String` argumentů volané metody.</span><span class="sxs-lookup"><span data-stu-id="0577a-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="0577a-129">Tímto způsobem se vyhnete problému, který **refaktoring přejmenování** nedojde ke změně `String` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0577a-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="0577a-130">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="0577a-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="0577a-131">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="0577a-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="0577a-132">Implementace <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní při vytvoření vazby mezi daty.</span><span class="sxs-lookup"><span data-stu-id="0577a-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="0577a-133">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="0577a-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="0577a-134">Bez `CallerMemberName` atribut, musíte zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="0577a-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="0577a-135">Následující graf ukazuje názvy, které jsou vráceny při použití členů `CallerMemberName` atribut.</span><span class="sxs-lookup"><span data-stu-id="0577a-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="0577a-136">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="0577a-136">Calls occurs within</span></span>|<span data-ttu-id="0577a-137">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="0577a-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="0577a-138">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="0577a-138">Method, property, or event</span></span>|<span data-ttu-id="0577a-139">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="0577a-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="0577a-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="0577a-140">Constructor</span></span>|<span data-ttu-id="0577a-141">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="0577a-141">The string ".ctor"</span></span>|
|<span data-ttu-id="0577a-142">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="0577a-142">Static constructor</span></span>|<span data-ttu-id="0577a-143">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="0577a-143">The string ".cctor"</span></span>|
|<span data-ttu-id="0577a-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="0577a-144">Destructor</span></span>|<span data-ttu-id="0577a-145">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="0577a-145">The string "Finalize"</span></span>|
|<span data-ttu-id="0577a-146">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="0577a-146">User-defined operators or conversions</span></span>|<span data-ttu-id="0577a-147">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="0577a-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="0577a-148">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="0577a-148">Attribute constructor</span></span>|<span data-ttu-id="0577a-149">Název metody nebo vlastnosti, ke kterému se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="0577a-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="0577a-150">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="0577a-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="0577a-151">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="0577a-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="0577a-152">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="0577a-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0577a-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0577a-153">See also</span></span>

- [<span data-ttu-id="0577a-154">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="0577a-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="0577a-155">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="0577a-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="0577a-156">Pojmenované a nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="0577a-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="0577a-157">Koncepty programování (C#)</span><span class="sxs-lookup"><span data-stu-id="0577a-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
