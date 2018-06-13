---
title: Metody rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 1cc2ccef09dd027c6f1e82f60ed4ac5f50db6ebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655281"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="b9113-102">Metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9113-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="b9113-103">Rozšiřující metody umožňují vývojářům přidání vlastních funkcí k typy dat, které jsou již definováni bez vytvoření nového odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="b9113-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="b9113-104">Rozšiřující metody umožňují napíše metoda, kterou lze volat, jako by šlo metodu instance existující typu.</span><span class="sxs-lookup"><span data-stu-id="b9113-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9113-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9113-105">Remarks</span></span>  
 <span data-ttu-id="b9113-106">Metody rozšíření může být pouze `Sub` postup nebo `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="b9113-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="b9113-107">Nelze definovat vlastnost rozšíření, pole nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="b9113-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="b9113-108">Všechny metody rozšíření musí být označen atributem rozšíření `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b9113-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="b9113-109">První parametr v definici – metoda rozšíření určuje, jaký typ dat metoda rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="b9113-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="b9113-110">Při spuštění metody první parametr je vázána na instanci typu dat, který vyvolá metodu.</span><span class="sxs-lookup"><span data-stu-id="b9113-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9113-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9113-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b9113-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b9113-112">Description</span></span>  
 <span data-ttu-id="b9113-113">V následujícím příkladu definuje `Print` rozšíření pro <xref:System.String> datového typu.</span><span class="sxs-lookup"><span data-stu-id="b9113-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="b9113-114">Používá metodu `Console.WriteLine` zobrazíte řetězec.</span><span class="sxs-lookup"><span data-stu-id="b9113-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="b9113-115">Parametr `Print` metody `aString`, určuje, že metoda rozšiřuje <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="b9113-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 <span data-ttu-id="b9113-116">Všimněte si, že metoda definice rozšíření je označen atributem rozšíření `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="b9113-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="b9113-117">Označení modul, ve kterém je definovaný metodu je volitelné, ale každá metoda rozšíření musí být označen.</span><span class="sxs-lookup"><span data-stu-id="b9113-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="b9113-118"><xref:System.Runtime.CompilerServices> musí být importovány pro přístup atribut rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-118"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="b9113-119">Rozšiřující metody lze deklarovat pouze v rámci moduly.</span><span class="sxs-lookup"><span data-stu-id="b9113-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="b9113-120">Modul, ve kterém je definovaný rozšiřující metodu obvykle není modul stejný jako ten, ve kterém je volána.</span><span class="sxs-lookup"><span data-stu-id="b9113-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="b9113-121">Místo toho se importuje modul, který obsahuje metodě rozšíření, pokud je nutné, aby do oboru.</span><span class="sxs-lookup"><span data-stu-id="b9113-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="b9113-122">Po modul, který obsahuje `Print` je v oboru, lze volat metodu, jako by šlo metodu obyčejnou instance, které nepřijímá žádné argumenty, jako například `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="b9113-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 <span data-ttu-id="b9113-123">Další příklad `PrintAndPunctuate`, je také rozšíření <xref:System.String>, tentokrát definovaný s dva parametry.</span><span class="sxs-lookup"><span data-stu-id="b9113-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="b9113-124">První parametr `aString`, určuje, že metoda rozšíření rozšiřuje <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b9113-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="b9113-125">Druhý parametr `punc`, měl být řetězec interpunkční znaménka, který je předán v jako argument při volání metody.</span><span class="sxs-lookup"><span data-stu-id="b9113-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="b9113-126">Metoda zobrazí řetězce, za nímž následuje interpunkčních znamének.</span><span class="sxs-lookup"><span data-stu-id="b9113-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 <span data-ttu-id="b9113-127">Je volána metoda odesláním v argument řetězce pro `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="b9113-127">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="b9113-128">Následující příklad ukazuje `Print` a `PrintAndPunctuate` definované a volat.</span><span class="sxs-lookup"><span data-stu-id="b9113-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="b9113-129"><xref:System.Runtime.CompilerServices> v modulu definice se naimportují Chcete-li povolit přístup k atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-129"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b9113-130">Kód</span><span class="sxs-lookup"><span data-stu-id="b9113-130">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="b9113-131">Rozšiřující metody jsou v dalším kroku začlenění do oboru a volat.</span><span class="sxs-lookup"><span data-stu-id="b9113-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="b9113-132">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b9113-132">Comments</span></span>  
 <span data-ttu-id="b9113-133">Všechny možnosti, které je potřeba ji moci spouštět tyto nebo podobné metody rozšíření je, že jejich být v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b9113-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="b9113-134">Pokud modul, který obsahuje metody rozšíření nachází v oboru, se zobrazí na IntelliSense a může být volána, jako by šlo metodu obyčejnou instance.</span><span class="sxs-lookup"><span data-stu-id="b9113-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="b9113-135">Všimněte si, že po vyvolání metody se žádný argument se neodesílají prvního parametru.</span><span class="sxs-lookup"><span data-stu-id="b9113-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="b9113-136">Parametr `aString` v předchozí metoda definice vázán na `example`, instanci `String` , který je volá.</span><span class="sxs-lookup"><span data-stu-id="b9113-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="b9113-137">Kompilátor použije `example` jako argument posílá první parametr.</span><span class="sxs-lookup"><span data-stu-id="b9113-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="b9113-138">Pokud je volat metody rozšíření pro objekt, který je nastaven na `Nothing`, metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="b9113-139">To neplatí obyčejnou metod, které.</span><span class="sxs-lookup"><span data-stu-id="b9113-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="b9113-140">Můžete zkontrolovat explicitně pro `Nothing` v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="b9113-141">Typy, které lze rozšířit</span><span class="sxs-lookup"><span data-stu-id="b9113-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="b9113-142">Metody rozšíření můžete definovat na většinu typů, které může být reprezentován v seznamu parametrů jazyka Visual Basic, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="b9113-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="b9113-143">Třídy (odkazové typy)</span><span class="sxs-lookup"><span data-stu-id="b9113-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="b9113-144">Struktury (typy hodnot)</span><span class="sxs-lookup"><span data-stu-id="b9113-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="b9113-145">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9113-145">Interfaces</span></span>  
  
-   <span data-ttu-id="b9113-146">Delegáty</span><span class="sxs-lookup"><span data-stu-id="b9113-146">Delegates</span></span>  
  
-   <span data-ttu-id="b9113-147">ByRef a ByVal argumenty</span><span class="sxs-lookup"><span data-stu-id="b9113-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="b9113-148">Obecná metoda parametry</span><span class="sxs-lookup"><span data-stu-id="b9113-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="b9113-149">Pole</span><span class="sxs-lookup"><span data-stu-id="b9113-149">Arrays</span></span>  
  
 <span data-ttu-id="b9113-150">Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřuje metodě rozšíření, je vyžadován a nemůže být volitelné.</span><span class="sxs-lookup"><span data-stu-id="b9113-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="b9113-151">Z tohoto důvodu `Optional` parametry a `ParamArray` parametry nemohou mít první parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="b9113-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="b9113-152">Metody rozšíření nejsou zahrnuty do pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="b9113-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="b9113-153">V následujícím příkladu příkaz `anObject.PrintMe()` vyvolá <xref:System.MissingMemberException> výjimky, bude stejná výjimka se zobrazí, pokud druhý `PrintMe` definice rozšíření metoda byly odstraněny.</span><span class="sxs-lookup"><span data-stu-id="b9113-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a><span data-ttu-id="b9113-154">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="b9113-154">Best Practices</span></span>  
 <span data-ttu-id="b9113-155">Metody rozšíření poskytují výkonný a pohodlný způsob, jak rozšířit existující typ.</span><span class="sxs-lookup"><span data-stu-id="b9113-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="b9113-156">Úspěšně používat, jsou ale některé body vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="b9113-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="b9113-157">Tyto aspekty platí především pro autory knihovny tříd, ale mohou ovlivnit všechny aplikace, která používá rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="b9113-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="b9113-158">Rozšiřující metody, které přidáte do typy, které nevlastníte jsou nejvíce obecně zranitelnější než rozšiřující metody, které jsou přidány do typy, které řídíte.</span><span class="sxs-lookup"><span data-stu-id="b9113-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="b9113-159">Existuje řada věcí se může objevit v třídy, které nevlastníte, jež mohou narušit rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="b9113-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="b9113-160">Pokud existuje kteréhokoli člena dostupné instance, které má podpis, který je kompatibilní s argumenty příkazu volání s žádné zužující převody požadované z argument na parametr, metodu instance se použije přednostně libovolné metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="b9113-161">Proto pokud přidáte metodu odpovídající instance třídy v určitém okamžiku existujícího člena rozšíření, která závisí na může být nedostupný.</span><span class="sxs-lookup"><span data-stu-id="b9113-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="b9113-162">Autor metody rozšíření nelze jinými programátory zabránit zápisu konfliktní rozšiřující metody, které může mají přednost před původní přípona.</span><span class="sxs-lookup"><span data-stu-id="b9113-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="b9113-163">Robustnost lze vylepšit uvedení rozšiřující metody v vlastní obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b9113-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="b9113-164">Příjemci knihovny potom můžete zahrnout obor názvů nebo vyloučit nebo vyberte mezi obory názvů, odděleně od zbytku knihovny.</span><span class="sxs-lookup"><span data-stu-id="b9113-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="b9113-165">To může být bezpečnější než je rozšíření třídy, zvlášť pokud nejste vlastníkem rozhraní nebo třída rozšíření rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b9113-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="b9113-166">Změnu rozhraní ovlivňuje všechny třídy, která implementuje ho.</span><span class="sxs-lookup"><span data-stu-id="b9113-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="b9113-167">Proto může být Autor méně pravděpodobné, že chcete přidat nebo změnit metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b9113-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="b9113-168">Ale pokud třída implementuje dvě rozhraní, které mají rozšiřující metody se stejným podpisem, metoda ani rozšíření je viditelný.</span><span class="sxs-lookup"><span data-stu-id="b9113-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="b9113-169">Většina specifický typ, který můžete rozšiřte.</span><span class="sxs-lookup"><span data-stu-id="b9113-169">Extend the most specific type you can.</span></span> <span data-ttu-id="b9113-170">V hierarchii typů Pokud vyberete typ, ze které jsou odvozeny mnoho dalších typů, jsou vrstvy možností, jak zavedení instance metody nebo jiné rozšiřující metody, které může kolidovat s vaším.</span><span class="sxs-lookup"><span data-stu-id="b9113-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="b9113-171">Rozšiřující metody, instanci metody a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9113-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="b9113-172">Pokud metoda v oboru instance podpisu, který je kompatibilní s argumenty volání příkazu, metodu instance je zvolen přednostně libovolné metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="b9113-173">Metoda instance má vyšší prioritu, i když metoda rozšíření je lepší shodu.</span><span class="sxs-lookup"><span data-stu-id="b9113-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="b9113-174">V následujícím příkladu `ExampleClass` obsahuje metodu instance s názvem `ExampleMethod` který má jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b9113-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="b9113-175">Metody rozšíření `ExampleMethod` rozšiřuje `ExampleClass`, a má jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="b9113-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 <span data-ttu-id="b9113-176">První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a jsou kompatibilní jenom s `Long` parametr v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b9113-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="b9113-177">Druhé volání `ExampleMethod` má `Integer` argument, `arg2`, a volá metodu instance.</span><span class="sxs-lookup"><span data-stu-id="b9113-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 <span data-ttu-id="b9113-178">Nyní reverse datové typy parametrů v tyto dvě metody:</span><span class="sxs-lookup"><span data-stu-id="b9113-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 <span data-ttu-id="b9113-179">V tuto chvíli kód v `Main` volá metodu instance obou časy.</span><span class="sxs-lookup"><span data-stu-id="b9113-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="b9113-180">Důvodem je, že oba `arg1` a `arg2` rozšiřující převod do mají `Long`, a metodu instance má přednost před metodě rozšíření v obou případech.</span><span class="sxs-lookup"><span data-stu-id="b9113-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 <span data-ttu-id="b9113-181">Metody rozšíření proto nelze nahradit existující instance metodu.</span><span class="sxs-lookup"><span data-stu-id="b9113-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="b9113-182">Když metody rozšíření má stejný název jako metodu instance podpisů nejsou v konfliktu, ale je možné přistupovat obě metody.</span><span class="sxs-lookup"><span data-stu-id="b9113-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="b9113-183">Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod` které nepřijímá žádné argumenty, rozšiřující metody se stejným názvem, ale jiné podpisy jsou povoleny, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b9113-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 <span data-ttu-id="b9113-184">Výstup z tohoto kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="b9113-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="b9113-185">Situaci je jednodušší s vlastnostmi: Pokud metody rozšíření má stejný název jako vlastnost třídy ji rozšiřuje, metoda rozšíření není viditelná a není přístupný.</span><span class="sxs-lookup"><span data-stu-id="b9113-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="b9113-186">Priorita rozšíření – metoda</span><span class="sxs-lookup"><span data-stu-id="b9113-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="b9113-187">Pokud dvě metody rozšíření, které mají stejné podpisy jsou v oboru a dostupné, jeden s vyšší prioritou bude volána.</span><span class="sxs-lookup"><span data-stu-id="b9113-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="b9113-188">Metody rozšíření priorita je založena na mechanismu používá k zajištění metodu oboru.</span><span class="sxs-lookup"><span data-stu-id="b9113-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="b9113-189">V následujícím seznamu jsou přednost hierarchii, postupně od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="b9113-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="b9113-190">Rozšiřující metody definované uvnitř aktuální modul.</span><span class="sxs-lookup"><span data-stu-id="b9113-190">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="b9113-191">Rozšiřující metody definované uvnitř datové typy v aktuálním oboru názvů nebo kterékoli z jeho nadřazených objektů, s podřízené obory názvů s vyšší prioritou než nadřazené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b9113-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="b9113-192">Rozšiřující metody definované uvnitř žádné typ importy v aktuální soubor.</span><span class="sxs-lookup"><span data-stu-id="b9113-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="b9113-193">Rozšiřující metody definované uvnitř žádné importy oboru názvů z aktuálního souboru.</span><span class="sxs-lookup"><span data-stu-id="b9113-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="b9113-194">Rozšiřující metody definované uvnitř žádné importy typ úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="b9113-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="b9113-195">Rozšiřující metody definované uvnitř žádné importy oboru názvů úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="b9113-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="b9113-196">Pokud přednost nejednoznačnosti nevyřeší, můžete zadat metodu, která jsou volání plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="b9113-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="b9113-197">Pokud `Print` metoda v předchozím příkladu je definována v modulu s názvem `StringExtensions`, je plně kvalifikovaný název `StringExtensions.Print(example)` místo `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="b9113-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9113-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9113-198">See Also</span></span>  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="b9113-199">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="b9113-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="b9113-200">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="b9113-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="b9113-201">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="b9113-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b9113-202">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="b9113-202">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="b9113-203">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="b9113-203">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="b9113-204">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="b9113-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="b9113-205">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9113-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
