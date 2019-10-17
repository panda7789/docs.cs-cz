---
title: Metody rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: d988ab36703bc20e6960d4b8ecc7a476d95ee9bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396016"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="657c4-102">Metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="657c4-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="657c4-103">Metody rozšíření umožňují vývojářům přidat vlastní funkce k datovým typům, které jsou již definovány bez vytváření nového odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="657c4-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="657c4-104">Rozšiřující metody umožňují napsat metodu, která může být volána, jako by šlo o metodu instance existujícího typu.</span><span class="sxs-lookup"><span data-stu-id="657c4-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="657c4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="657c4-105">Remarks</span></span>

<span data-ttu-id="657c4-106">Metoda rozšíření může být pouze procedura @no__t 0 nebo procedura `Function`.</span><span class="sxs-lookup"><span data-stu-id="657c4-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="657c4-107">Nelze definovat vlastnost rozšíření, pole nebo událost.</span><span class="sxs-lookup"><span data-stu-id="657c4-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="657c4-108">Všechny metody rozšíření musí být označené atributem rozšíření `<Extension>` z oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> a musí být definované v [modulu](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="657c4-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="657c4-109">Pokud je metoda rozšíření definována mimo modul, Visual Basic kompilátor vygeneruje chybu [BC36551](../../../misc/bc36551.md), "metody rozšíření mohou být definovány pouze v modulech".</span><span class="sxs-lookup"><span data-stu-id="657c4-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="657c4-110">První parametr v definici metody rozšíření určuje, který typ dat metoda rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="657c4-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="657c4-111">Při spuštění metody je první parametr svázán s instancí datového typu, který vyvolá metodu.</span><span class="sxs-lookup"><span data-stu-id="657c4-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="657c4-112">Atribut `Extension` lze použít pouze pro Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)nebo [`Function`](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="657c4-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="657c4-113">Použijete-li jej na `Class` nebo `Structure`, kompilátor Visual Basic generuje chybu [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), atribut Extension lze použít pouze v deklaracích Module, sub nebo Function.</span><span class="sxs-lookup"><span data-stu-id="657c4-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="657c4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="657c4-114">Example</span></span>

<span data-ttu-id="657c4-115">Následující příklad definuje rozšíření `Print` pro datový typ <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="657c4-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="657c4-116">Metoda používá `Console.WriteLine` k zobrazení řetězce.</span><span class="sxs-lookup"><span data-stu-id="657c4-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="657c4-117">Parametr metody `Print`, `aString`, určuje, že metoda rozšiřuje třídu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="657c4-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="657c4-118">Všimněte si, že definice rozšiřující metody je označena atributem rozšíření `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="657c4-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="657c4-119">Označení modulu, ve kterém je metoda definovaná, je volitelné, ale každá metoda rozšíření musí být označená.</span><span class="sxs-lookup"><span data-stu-id="657c4-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="657c4-120">aby bylo možné získat přístup k atributu rozšíření, musí být importována hodnota <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="657c4-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="657c4-121">Metody rozšíření mohou být deklarovány pouze v rámci modulů.</span><span class="sxs-lookup"><span data-stu-id="657c4-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="657c4-122">Modul, ve kterém je definována metoda rozšíření, obvykle není stejný modul jako ten, ve kterém je volána.</span><span class="sxs-lookup"><span data-stu-id="657c4-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="657c4-123">Místo toho je importován modul, který obsahuje metodu rozšíření, pokud je potřeba, aby se přenesl do rozsahu.</span><span class="sxs-lookup"><span data-stu-id="657c4-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="657c4-124">Po modulu, který obsahuje `Print` je v oboru, může být metoda volána, jako by šlo o běžnou metodu instance, která nepřijímá žádné argumenty, jako je například `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="657c4-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="657c4-125">Další příklad, `PrintAndPunctuate`, je také rozšíření pro <xref:System.String>. Tento čas je definován pomocí dvou parametrů.</span><span class="sxs-lookup"><span data-stu-id="657c4-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="657c4-126">První parametr `aString` stanoví, že rozšiřující metoda rozšiřuje <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="657c4-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="657c4-127">Druhý parametr `punc` má být řetězec interpunkční znaménka, která je předána jako argument při volání metody.</span><span class="sxs-lookup"><span data-stu-id="657c4-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="657c4-128">Metoda zobrazí řetězec následovaný interpunkční znaménky.</span><span class="sxs-lookup"><span data-stu-id="657c4-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="657c4-129">Metoda je volána při odeslání do řetězcového argumentu pro `punc`: `example.PrintAndPunctuate(".")`.</span><span class="sxs-lookup"><span data-stu-id="657c4-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="657c4-130">Následující příklad ukazuje `Print` a `PrintAndPunctuate` definované a volané.</span><span class="sxs-lookup"><span data-stu-id="657c4-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="657c4-131"><xref:System.Runtime.CompilerServices> je importován v modulu definice, aby bylo možné povolit přístup k atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="657c4-132">Dále se rozšiřující metody přenesou do rozsahu a nazývají se:</span><span class="sxs-lookup"><span data-stu-id="657c4-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="657c4-133">Vše, co musí být schopné spustit tyto nebo podobné metody rozšíření, je, že jsou v oboru.</span><span class="sxs-lookup"><span data-stu-id="657c4-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="657c4-134">Pokud je modul obsahující metodu rozšíření v oboru, je viditelný v technologii IntelliSense a může být volána, jako by šlo o běžnou metodu instance.</span><span class="sxs-lookup"><span data-stu-id="657c4-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="657c4-135">Všimněte si, že při vyvolání metod není v parametru pro první parametr odeslán žádný argument.</span><span class="sxs-lookup"><span data-stu-id="657c4-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="657c4-136">Parametr `aString` v předchozích definicích metod je vázán na `example`, instanci `String`, která je volá.</span><span class="sxs-lookup"><span data-stu-id="657c4-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="657c4-137">Kompilátor použije `example` jako argument odeslaný do prvního parametru.</span><span class="sxs-lookup"><span data-stu-id="657c4-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="657c4-138">Pokud je volána metoda rozšíření pro objekt, který je nastaven na `Nothing`, metoda rozšíření se spustí.</span><span class="sxs-lookup"><span data-stu-id="657c4-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="657c4-139">To se nevztahuje na běžné metody instance.</span><span class="sxs-lookup"><span data-stu-id="657c4-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="657c4-140">V metodě rozšíření můžete explicitně vyhledat `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="657c4-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="657c4-141">Typy, které lze rozšířit</span><span class="sxs-lookup"><span data-stu-id="657c4-141">Types that can be extended</span></span>

<span data-ttu-id="657c4-142">Můžete definovat metodu rozšíření pro většinu typů, které mohou být reprezentovány v seznamu parametrů Visual Basic, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="657c4-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="657c4-143">Třídy (typy odkazů)</span><span class="sxs-lookup"><span data-stu-id="657c4-143">Classes (reference types)</span></span>
- <span data-ttu-id="657c4-144">Struktury (typy hodnot)</span><span class="sxs-lookup"><span data-stu-id="657c4-144">Structures (value types)</span></span>
- <span data-ttu-id="657c4-145">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="657c4-145">Interfaces</span></span>
- <span data-ttu-id="657c4-146">Delegáty</span><span class="sxs-lookup"><span data-stu-id="657c4-146">Delegates</span></span>
- <span data-ttu-id="657c4-147">Argumenty ByRef a ByVal</span><span class="sxs-lookup"><span data-stu-id="657c4-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="657c4-148">Parametry obecné metody</span><span class="sxs-lookup"><span data-stu-id="657c4-148">Generic method parameters</span></span>
- <span data-ttu-id="657c4-149">Pole</span><span class="sxs-lookup"><span data-stu-id="657c4-149">Arrays</span></span>

<span data-ttu-id="657c4-150">Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřující metoda rozšiřuje, je požadován a nemůže být volitelný.</span><span class="sxs-lookup"><span data-stu-id="657c4-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="657c4-151">Z tohoto důvodu parametry `Optional` a parametry `ParamArray` nemůžou být prvním parametrem v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="657c4-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="657c4-152">Metody rozšíření nejsou v pozdní vazbě zvažovány.</span><span class="sxs-lookup"><span data-stu-id="657c4-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="657c4-153">V následujícím příkladu příkaz `anObject.PrintMe()` vyvolává výjimku <xref:System.MissingMemberException>, stejná výjimka jako v případě odstranění druhé definice metody rozšíření `PrintMe`.</span><span class="sxs-lookup"><span data-stu-id="657c4-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="657c4-154">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="657c4-154">Best practices</span></span>

<span data-ttu-id="657c4-155">Metody rozšíření poskytují pohodlný a účinný způsob, jak rozšířit existující typ.</span><span class="sxs-lookup"><span data-stu-id="657c4-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="657c4-156">Pokud je však chcete úspěšně použít, je třeba vzít v úvahu několik bodů.</span><span class="sxs-lookup"><span data-stu-id="657c4-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="657c4-157">Tyto požadavky platí hlavně pro autory knihoven tříd, ale mohou ovlivnit jakoukoli aplikaci, která používá metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="657c4-158">Obecně platí, že metody rozšíření, které přidáte do typů, které nevlastníte, jsou zranitelnější než metody rozšíření přidané do typů, které ovládáte.</span><span class="sxs-lookup"><span data-stu-id="657c4-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="657c4-159">Ve třídách, které nevlastníte, může dojít k několika akcím, které mohou narušovat vaše metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="657c4-160">Pokud existuje nějaký přístupný člen instance, který má signaturu kompatibilní s argumenty v příkazu volání, bez zúžení převodů vyžadovaných v argumentu pro parametr, metoda instance bude použita v preference pro jakoukoliv metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="657c4-161">Proto pokud je příslušná metoda instance přidána do třídy v nějakém okamžiku, existující člen rozšíření, ke kterému jste se spoléhali, může být nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="657c4-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="657c4-162">Autor metody rozšíření nemůže zabránit jiným programátorům v zápisu konfliktních metod rozšíření, které mohou mít přednost před původním rozšířením.</span><span class="sxs-lookup"><span data-stu-id="657c4-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="657c4-163">Můžete zvýšit odolnost tím, že umístíte rozšiřující metody do svého vlastního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="657c4-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="657c4-164">Příjemci vaší knihovny mohou potom zahrnout obor názvů nebo vyloučit z něj nebo vybrat mezi obory názvů odděleně od ostatních knihoven.</span><span class="sxs-lookup"><span data-stu-id="657c4-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="657c4-165">Může být bezpečnější pro rozšiřování rozhraní, než je rozšiřování tříd, zejména v případě, že nevlastníte rozhraní nebo třídu.</span><span class="sxs-lookup"><span data-stu-id="657c4-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="657c4-166">Změna rozhraní má vliv na každou třídu, která ji implementuje.</span><span class="sxs-lookup"><span data-stu-id="657c4-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="657c4-167">Proto může být autor méně pravděpodobný přidat nebo změnit metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="657c4-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="657c4-168">Nicméně pokud třída implementuje dvě rozhraní, která mají metody rozšíření se stejnou signaturou, není žádná metoda rozšíření viditelná.</span><span class="sxs-lookup"><span data-stu-id="657c4-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="657c4-169">Zvětšete konkrétní typ, který můžete.</span><span class="sxs-lookup"><span data-stu-id="657c4-169">Extend the most specific type you can.</span></span> <span data-ttu-id="657c4-170">Pokud v hierarchii typů vyberete typ, ze kterého je odvozeno mnoho dalších typů, existují různé úrovně možností pro zavedení instančních metod nebo jiných rozšiřujících metod, které mohou kolidovat s vámi.</span><span class="sxs-lookup"><span data-stu-id="657c4-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="657c4-171">Metody rozšíření, metody instance a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="657c4-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="657c4-172">Pokud má metoda instance v rámci oboru signaturu, která je kompatibilní s argumenty volání příkazu, je metoda instance zvolena v předvolbách libovolné metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="657c4-173">Metoda instance má přednost, i když je rozšiřující metoda lepší shoda.</span><span class="sxs-lookup"><span data-stu-id="657c4-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="657c4-174">V následujícím příkladu `ExampleClass` obsahuje metodu instance nazvanou `ExampleMethod`, která má jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="657c4-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="657c4-175">Metoda rozšíření `ExampleMethod` rozšiřuje `ExampleClass` a má jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="657c4-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="657c4-176">První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a je kompatibilní pouze s parametrem `Long` v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="657c4-177">Druhé volání `ExampleMethod` má argument `Integer`, `arg2` a volá metodu instance.</span><span class="sxs-lookup"><span data-stu-id="657c4-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="657c4-178">Nyní obrátíte datové typy parametrů ze dvou metod:</span><span class="sxs-lookup"><span data-stu-id="657c4-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="657c4-179">Tentokrát kód v `Main` volá metodu instance několikrát.</span><span class="sxs-lookup"><span data-stu-id="657c4-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="657c4-180">Důvodem je, že `arg1` i `arg2` mají rozšiřující převod na `Long` a metoda instance má v obou případech přednost před metodou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="657c4-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="657c4-181">Proto metoda rozšíření nemůže nahradit existující metodu instance.</span><span class="sxs-lookup"><span data-stu-id="657c4-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="657c4-182">Nicméně, pokud má metoda rozšíření stejný název jako metoda instance, ale signatury nekolidují, obě metody jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="657c4-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="657c4-183">Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod`, která nepřijímá žádné argumenty, metody rozšíření se stejným názvem, ale různé podpisy jsou povoleny, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="657c4-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="657c4-184">Výstup z tohoto kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="657c4-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="657c4-185">Tato situace je jednodušší s vlastnostmi: Pokud má rozšiřující metoda stejný název jako vlastnost třídy, kterou rozšiřuje, není metoda rozšíření viditelná a nelze k ní mít přístup.</span><span class="sxs-lookup"><span data-stu-id="657c4-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="657c4-186">Priorita metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="657c4-186">Extension method precedence</span></span>

<span data-ttu-id="657c4-187">V případě, že dvě metody rozšíření, které mají stejné signatury, jsou v oboru a přístupné, bude vyvolána ta s vyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="657c4-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="657c4-188">Priorita metody rozšíření je založena na mechanismu, který je použit k převedení metody do rozsahu.</span><span class="sxs-lookup"><span data-stu-id="657c4-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="657c4-189">Následující seznam zobrazuje hierarchii priority od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="657c4-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="657c4-190">Metody rozšíření definované v aktuálním modulu.</span><span class="sxs-lookup"><span data-stu-id="657c4-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="657c4-191">Rozšiřující metody definované uvnitř datových typů v aktuálním oboru názvů nebo kterémkoli z jeho nadřazených objektů s podřízenými obory názvů s vyšší prioritou než nadřazené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="657c4-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="657c4-192">Rozšiřující metody definované uvnitř libovolných importů typu v aktuálním souboru.</span><span class="sxs-lookup"><span data-stu-id="657c4-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="657c4-193">Rozšiřující metody definované uvnitř libovolných importů oboru názvů v aktuálním souboru.</span><span class="sxs-lookup"><span data-stu-id="657c4-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="657c4-194">Rozšiřující metody definované uvnitř všech importů typu na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="657c4-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="657c4-195">Rozšiřující metody definované uvnitř libovolných importů oboru názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="657c4-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="657c4-196">Pokud priorita nejednoznačnosti nevyřeší, můžete použít plně kvalifikovaný název k určení volané metody.</span><span class="sxs-lookup"><span data-stu-id="657c4-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="657c4-197">Pokud je metoda `Print` v předchozím příkladu definována v modulu s názvem `StringExtensions`, plně kvalifikovaný název je `StringExtensions.Print(example)` namísto `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="657c4-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="657c4-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="657c4-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="657c4-199">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="657c4-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="657c4-200">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="657c4-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="657c4-201">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="657c4-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="657c4-202">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="657c4-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="657c4-203">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="657c4-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="657c4-204">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="657c4-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="657c4-205">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="657c4-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
