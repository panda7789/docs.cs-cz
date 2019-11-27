---
title: Informace o volajícím
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 7c87b540a68f4d0219918fed66de6c1b635104a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349478"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="c0a9d-102">Informace o volajícím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0a9d-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="c0a9d-103">Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="c0a9d-104">Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="c0a9d-105">Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="c0a9d-106">Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="c0a9d-107">V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="c0a9d-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="c0a9d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0a9d-108">Attribute</span></span>|<span data-ttu-id="c0a9d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c0a9d-109">Description</span></span>|<span data-ttu-id="c0a9d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="c0a9d-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="c0a9d-111">Úplná cesta zdrojového souboru, který obsahuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="c0a9d-112">Toto je cesta k souboru v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="c0a9d-113">Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="c0a9d-114">Název metody nebo vlastnosti volajícího.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-114">Method or property name of the caller.</span></span> <span data-ttu-id="c0a9d-115">Viz [názvy členů](#MEMBERNAMES) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="c0a9d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0a9d-116">Example</span></span>  
 <span data-ttu-id="c0a9d-117">Následující příklad ukazuje způsob použití atributů Informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="c0a9d-118">Při každém volání metody `TraceMessage` jsou informace o volajícím nahrazeny jako argumenty nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0a9d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0a9d-119">Remarks</span></span>  
 <span data-ttu-id="c0a9d-120">Pro každý volitelný parametr je třeba zadat explicitní výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="c0a9d-121">Atributy Informace o volajícím nelze použít u parametrů, které nejsou uvedeny jako volitelné.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="c0a9d-122">Atributy Informace o volajícím neučiní parametr volitelným.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="c0a9d-123">Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="c0a9d-124">Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="c0a9d-125">Na rozdíl od výsledků vlastnosti <xref:System.Exception.StackTrace%2A> pro výjimky nejsou výsledky ovlivněny zmatením.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="c0a9d-126">Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="MEMBERNAMES"></a><span data-ttu-id="c0a9d-127">Názvy členů</span><span class="sxs-lookup"><span data-stu-id="c0a9d-127">Member Names</span></span>  
 <span data-ttu-id="c0a9d-128">Atribut `CallerMemberName` lze použít k zamezení zadání názvu člena jako `String` argumentu volané metody.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="c0a9d-129">Pomocí této techniky se vyhnete problému s tím, že **Refaktoring přejmenování** nemění hodnoty `String`.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="c0a9d-130">Tato výhoda se hodí zvláště v těchto úlohách:</span><span class="sxs-lookup"><span data-stu-id="c0a9d-130">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="c0a9d-131">Použití trasování a diagnostických rutin.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-131">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="c0a9d-132">Implementace rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> při vázání dat</span><span class="sxs-lookup"><span data-stu-id="c0a9d-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="c0a9d-133">Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="c0a9d-134">Bez atributu `CallerMemberName` musíte zadat název vlastnosti jako literál.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="c0a9d-135">Následující graf znázorňuje názvy členů, které jsou vráceny při použití atributu `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="c0a9d-136">K volání dochází v rámci</span><span class="sxs-lookup"><span data-stu-id="c0a9d-136">Calls occurs within</span></span>|<span data-ttu-id="c0a9d-137">Výsledek názvu členu</span><span class="sxs-lookup"><span data-stu-id="c0a9d-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="c0a9d-138">Metoda, vlastnost nebo událost</span><span class="sxs-lookup"><span data-stu-id="c0a9d-138">Method, property, or event</span></span>|<span data-ttu-id="c0a9d-139">Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="c0a9d-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="c0a9d-140">Constructor</span></span>|<span data-ttu-id="c0a9d-141">Řetězec „.ctor“</span><span class="sxs-lookup"><span data-stu-id="c0a9d-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="c0a9d-142">Statický konstruktor</span><span class="sxs-lookup"><span data-stu-id="c0a9d-142">Static constructor</span></span>|<span data-ttu-id="c0a9d-143">Řetězec „.cctor“</span><span class="sxs-lookup"><span data-stu-id="c0a9d-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="c0a9d-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="c0a9d-144">Destructor</span></span>|<span data-ttu-id="c0a9d-145">Řetězec „Finalize“</span><span class="sxs-lookup"><span data-stu-id="c0a9d-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="c0a9d-146">Operátory nebo převody definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="c0a9d-146">User-defined operators or conversions</span></span>|<span data-ttu-id="c0a9d-147">Vygenerovaný název pro člen, například „op_Addition“.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="c0a9d-148">Konstruktor atributu</span><span class="sxs-lookup"><span data-stu-id="c0a9d-148">Attribute constructor</span></span>|<span data-ttu-id="c0a9d-149">Název členu, na který se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="c0a9d-150">Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="c0a9d-151">Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)</span><span class="sxs-lookup"><span data-stu-id="c0a9d-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="c0a9d-152">Výchozí hodnota volitelného parametru.</span><span class="sxs-lookup"><span data-stu-id="c0a9d-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0a9d-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0a9d-153">See also</span></span>

- [<span data-ttu-id="c0a9d-154">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0a9d-154">Attributes (Visual Basic)</span></span>](../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="c0a9d-155">Společné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0a9d-155">Common Attributes (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="c0a9d-156">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="c0a9d-156">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="c0a9d-157">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0a9d-157">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
