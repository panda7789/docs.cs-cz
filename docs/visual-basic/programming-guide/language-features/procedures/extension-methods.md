---
title: Metody rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 9e005d0dc7da154fbaffbf7e02c55445a1213195
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296235"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="15ed5-102">Metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15ed5-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="15ed5-103">Rozšiřující metody umožňují vývojářům přidat vlastní funkce pro datové typy, které jsou již definovány, bez vytváření nového odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="15ed5-104">Rozšiřující metody umožňují napsat metodu, kterou lze volat jako by šlo metodu instance existujícího typu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15ed5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15ed5-105">Remarks</span></span>  
 <span data-ttu-id="15ed5-106">Metody rozšíření lze pouze `Sub` procedury nebo `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="15ed5-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="15ed5-107">Nelze definovat vlastnost rozšíření, pole nebo události.</span><span class="sxs-lookup"><span data-stu-id="15ed5-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="15ed5-108">Všechny metody rozšíření musí být označená pomocí atributu rozšíření `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15ed5-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="15ed5-109">První parametr v metodě rozšíření určuje, jaký typ dat metoda rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="15ed5-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="15ed5-110">Při spuštění metody je první parametr vázán k instanci datového typu, který vyvolá metodu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15ed5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="15ed5-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="15ed5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="15ed5-112">Description</span></span>  
 <span data-ttu-id="15ed5-113">Následující příklad definuje `Print` rozšíření <xref:System.String> datového typu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="15ed5-114">Metoda používá `Console.WriteLine` pro zobrazení řetězce.</span><span class="sxs-lookup"><span data-stu-id="15ed5-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="15ed5-115">Parametr `Print` metody `aString`, stanoví, že metody rozšíří <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="15ed5-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 <span data-ttu-id="15ed5-116">Všimněte si, že definice metody rozšíření je označena atributem rozšíření `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="15ed5-116">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="15ed5-117">Označení modulu, ve kterém je definována metoda, je volitelný, ale každá metoda rozšíření musí být označeny.</span><span class="sxs-lookup"><span data-stu-id="15ed5-117">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <xref:System.Runtime.CompilerServices> <span data-ttu-id="15ed5-118">musí být importovány pro přístup k atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-118">must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="15ed5-119">Metody rozšíření lze deklarovat jen v modulech.</span><span class="sxs-lookup"><span data-stu-id="15ed5-119">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="15ed5-120">Modul, ve kterém je definována rozšiřující metoda obvykle není stejný modul jako ten, ve kterém je volána.</span><span class="sxs-lookup"><span data-stu-id="15ed5-120">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="15ed5-121">Místo toho se importuje modul, který obsahuje metodu rozšíření, pokud musí se jednat o, pro přivedení do rozsahu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-121">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="15ed5-122">Jakmile bude modul obsahující `Print` je v oboru, lze volat metodu, jako by šlo o běžnou metodu instance, která nepřijímá žádné argumenty, jako například `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="15ed5-122">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 <span data-ttu-id="15ed5-123">Následující příklad `PrintAndPunctuate`, je také rozšíření <xref:System.String>, tentokrát definováno se dvěma parametry.</span><span class="sxs-lookup"><span data-stu-id="15ed5-123">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="15ed5-124">První parametr `aString`, stanoví, že metoda rozšíření rozšiřuje <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="15ed5-124">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="15ed5-125">Druhý parametr `punc`, je určen jako řetězec interpunkčního, které je předáno jako argument při volání metody.</span><span class="sxs-lookup"><span data-stu-id="15ed5-125">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="15ed5-126">Metoda zobrazí řetězec následovaný interpunkčními znaménky.</span><span class="sxs-lookup"><span data-stu-id="15ed5-126">The method displays the string followed by the punctuation marks.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 <span data-ttu-id="15ed5-127">Je volána metoda odesláním v argumentu řetězce pro `punc`:</span><span class="sxs-lookup"><span data-stu-id="15ed5-127">The method is called by sending in a string argument for `punc`:</span></span> `example.PrintAndPunctuate(".")`  
  
 <span data-ttu-id="15ed5-128">Následující příklad ukazuje `Print` a `PrintAndPunctuate` definované a volané.</span><span class="sxs-lookup"><span data-stu-id="15ed5-128">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <xref:System.Runtime.CompilerServices> <span data-ttu-id="15ed5-129">je importován v modulu definice Chcete-li povolit přístup k atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-129">is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="15ed5-130">Kód</span><span class="sxs-lookup"><span data-stu-id="15ed5-130">Code</span></span>  
  
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
  
 <span data-ttu-id="15ed5-131">V dalším kroku jsou metody rozšíření přeneseny do rozsahu a volá.</span><span class="sxs-lookup"><span data-stu-id="15ed5-131">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="15ed5-132">Komentáře</span><span class="sxs-lookup"><span data-stu-id="15ed5-132">Comments</span></span>  
 <span data-ttu-id="15ed5-133">Všechny možnosti, které je potřeba mít možnost ke spouštění těchto nebo podobných metod rozšíření stačí, aby byly v oboru.</span><span class="sxs-lookup"><span data-stu-id="15ed5-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="15ed5-134">Pokud modul, který obsahuje metodu rozšíření se nachází v oboru, je zobrazen v technologii IntelliSense a může být volána, jako by šlo o běžnou metodu instance.</span><span class="sxs-lookup"><span data-stu-id="15ed5-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="15ed5-135">Všimněte si, že když jsou metody vyvolány, žádný argument se posílá ve pro první parametr.</span><span class="sxs-lookup"><span data-stu-id="15ed5-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="15ed5-136">Parametr `aString` v metodě předchozí definice je vázán na `example`, instanci `String` , která je volá.</span><span class="sxs-lookup"><span data-stu-id="15ed5-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="15ed5-137">Kompilátor použije `example` jako argument odeslaný na první parametr.</span><span class="sxs-lookup"><span data-stu-id="15ed5-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="15ed5-138">Pokud rozšiřující metoda je volána pro objekt, který je nastaven `Nothing`, metoda rozšíření se zavolá.</span><span class="sxs-lookup"><span data-stu-id="15ed5-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="15ed5-139">To se nevztahuje na běžné metody instancí.</span><span class="sxs-lookup"><span data-stu-id="15ed5-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="15ed5-140">Můžete explicitně zjišťovat `Nothing` v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-140">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="15ed5-141">Typy, které je možné rozšířit</span><span class="sxs-lookup"><span data-stu-id="15ed5-141">Types That Can Be Extended</span></span>  
 <span data-ttu-id="15ed5-142">Můžete definovat rozšiřující metodu pro většinu typů, které mohou být zastoupeny v seznamu parametrů jazyka Visual Basic, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="15ed5-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="15ed5-143">Třídy (typy odkazů)</span><span class="sxs-lookup"><span data-stu-id="15ed5-143">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="15ed5-144">Struktury (typy hodnot)</span><span class="sxs-lookup"><span data-stu-id="15ed5-144">Structures (value types)</span></span>  
  
-   <span data-ttu-id="15ed5-145">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="15ed5-145">Interfaces</span></span>  
  
-   <span data-ttu-id="15ed5-146">Delegáty</span><span class="sxs-lookup"><span data-stu-id="15ed5-146">Delegates</span></span>  
  
-   <span data-ttu-id="15ed5-147">Argumenty ByRef a ByVal</span><span class="sxs-lookup"><span data-stu-id="15ed5-147">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="15ed5-148">Obecné parametry metody</span><span class="sxs-lookup"><span data-stu-id="15ed5-148">Generic method parameters</span></span>  
  
-   <span data-ttu-id="15ed5-149">Pole</span><span class="sxs-lookup"><span data-stu-id="15ed5-149">Arrays</span></span>  
  
 <span data-ttu-id="15ed5-150">Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřující metoda rozšiřuje, je vyžadován a nemůže být nepovinný.</span><span class="sxs-lookup"><span data-stu-id="15ed5-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="15ed5-151">Z tohoto důvodu `Optional` parametry a `ParamArray` parametry nemohou být první parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="15ed5-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="15ed5-152">Rozšiřující metody nejsou považovány za v pozdní vazbě.</span><span class="sxs-lookup"><span data-stu-id="15ed5-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="15ed5-153">V následujícím příkladu příkaz `anObject.PrintMe()` vyvolá <xref:System.MissingMemberException> výjimku, kterou byste viděli stejnou výjimku druhý `PrintMe` definici metody rozšíření se odstranily.</span><span class="sxs-lookup"><span data-stu-id="15ed5-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a><span data-ttu-id="15ed5-154">Doporučené postupy</span><span class="sxs-lookup"><span data-stu-id="15ed5-154">Best Practices</span></span>  
 <span data-ttu-id="15ed5-155">Rozšiřující metody poskytují pohodlný a účinný způsob, jak rozšířit existující typ.</span><span class="sxs-lookup"><span data-stu-id="15ed5-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="15ed5-156">Však úspěšně používat, existují některé body ke zvážení.</span><span class="sxs-lookup"><span data-stu-id="15ed5-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="15ed5-157">Tyto úvahy platí hlavně pro autory knihoven tříd, ale mohou ovlivnit jakékoli aplikace, které používají rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="15ed5-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="15ed5-158">Obecně jsou zranitelnější než metody rozšíření přidané do typů, které řídíte rozšiřující metody, které přidáte na typy, které nevlastníte.</span><span class="sxs-lookup"><span data-stu-id="15ed5-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="15ed5-159">V mnoha může dojít ve třídách, které nevlastníte, jež mohou narušit vaše metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="15ed5-160">Pokud existuje kterýkoli přístupný instanční člen, který má stejný podpis kompatibilní s argumenty v příkazu volání, bez zužujících převodů požadovaných argumentem pro parametr, použije se instanční metoda před jakoukoli metodou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="15ed5-161">Proto pokud metoda příslušné instance je přidána do třídy v určitém okamžiku, existující člen rozšíření, která závisí na může být nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="15ed5-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="15ed5-162">Autor metody rozšíření nemůže ostatním programátorům zabránit ve vytváření konfliktních metod rozšíření, které mohou mít přednost před původním rozšířením.</span><span class="sxs-lookup"><span data-stu-id="15ed5-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="15ed5-163">Můžete zlepšit odolnost vložením rozšiřujících metod ve vlastním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15ed5-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="15ed5-164">Spotřebitelé knihovny potom můžete zahrnout oboru názvů nebo vyloučit nebo volit mezi obory názvů odděleně od zbytku knihovny.</span><span class="sxs-lookup"><span data-stu-id="15ed5-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="15ed5-165">Může být bezpečnější rozšířit rozhraní než rozšířit třídy, zejména v případě, že není vlastníkem rozhraní nebo třídu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="15ed5-166">Změna v rozhraní se týká každé třídy, který jej implementuje.</span><span class="sxs-lookup"><span data-stu-id="15ed5-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="15ed5-167">Proto že autor bude méně pravděpodobné, že chcete přidat nebo změnit metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15ed5-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="15ed5-168">Nicméně pokud třída implementuje dvě rozhraní, které mají stejnou signaturu metody rozšíření, žádná rozšiřující metoda není viditelná.</span><span class="sxs-lookup"><span data-stu-id="15ed5-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="15ed5-169">Rozšiřte co nejspecifičtější typ., můžete.</span><span class="sxs-lookup"><span data-stu-id="15ed5-169">Extend the most specific type you can.</span></span> <span data-ttu-id="15ed5-170">V hierarchii typů vyberete typ, ze které jsou odvozeny mnoho jiných typů, existují vrstvy možností pro zavedení metody instance nebo jiných rozšiřujících metod, které by mohou narušovat vaše.</span><span class="sxs-lookup"><span data-stu-id="15ed5-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="15ed5-171">Rozšiřující metody, metody Instance a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="15ed5-171">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="15ed5-172">Pokud metoda příslušné instance má podpis, který je kompatibilní s argumenty volání příkazu, metoda instance bude zvolena v preferenci jakoukoli metodou rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="15ed5-173">Instanční metoda má přednost, i když rozšiřující metoda představuje lepší shodu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="15ed5-174">V následujícím příkladu `ExampleClass` obsahuje metodu instance pojmenovanou `ExampleMethod` , který má jeden parametr typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="15ed5-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="15ed5-175">Metoda rozšíření `ExampleMethod` rozšiřuje `ExampleClass`, a má jeden parametr typu `Long`.</span><span class="sxs-lookup"><span data-stu-id="15ed5-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 <span data-ttu-id="15ed5-176">První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a je kompatibilní jenom s `Long` parametr v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="15ed5-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="15ed5-177">Druhé volání `ExampleMethod` má `Integer` argument, `arg2`, a volá metodu instance.</span><span class="sxs-lookup"><span data-stu-id="15ed5-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 <span data-ttu-id="15ed5-178">Nyní obraťte datové typy parametrů ve dvou metod:</span><span class="sxs-lookup"><span data-stu-id="15ed5-178">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 <span data-ttu-id="15ed5-179">Tentokrát kód v `Main` volá metodu instance obou časů.</span><span class="sxs-lookup"><span data-stu-id="15ed5-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="15ed5-180">Důvodem je, že oba `arg1` a `arg2` mít rozšiřitelný převod `Long`, a instanční metoda má přednost před metodu rozšíření v obou případech.</span><span class="sxs-lookup"><span data-stu-id="15ed5-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 <span data-ttu-id="15ed5-181">Proto rozšiřující metoda nemůže nahradit stávající metodu instance.</span><span class="sxs-lookup"><span data-stu-id="15ed5-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="15ed5-182">Ale když rozšiřující metoda má stejný název jako metoda instance, ale podpisy nejsou v rozporu, obě metody jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="15ed5-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="15ed5-183">Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod` , která nebere žádné argumenty, rozšiřující metody se stejným názvem, ale různými podpisy, jsou povoleny, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 <span data-ttu-id="15ed5-184">Výstup tohoto kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="15ed5-184">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="15ed5-185">Situace je jednodušší s vlastnostmi: Pokud rozšiřující metoda má stejný název jako vlastnost třídy, kterou rozšiřuje, rozšiřující metoda není viditelná a přístupná.</span><span class="sxs-lookup"><span data-stu-id="15ed5-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="15ed5-186">Priorita rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="15ed5-186">Extension Method Precedence</span></span>  
 <span data-ttu-id="15ed5-187">Když dvě rozšiřující metody, které mají stejné podpisy jsou v oboru a přístupné, bude vyvolána ta s vyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="15ed5-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="15ed5-188">Přednost metody rozšíření je založena na mechanismu použitém k uvedení metody do oboru.</span><span class="sxs-lookup"><span data-stu-id="15ed5-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="15ed5-189">Následující seznam obsahuje hierarchii priority od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="15ed5-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1. <span data-ttu-id="15ed5-190">Rozšiřující metody definované uvnitř aktuálního modulu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-190">Extension methods defined inside the current module.</span></span>  
  
2. <span data-ttu-id="15ed5-191">Rozšiřující metody definované uvnitř datových typů v aktuálním oboru názvů, nebo v jednom z jeho rodičů s podřízenými obory názvů mají vyšší prioritu než nadřazené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="15ed5-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3. <span data-ttu-id="15ed5-192">Rozšiřující metody definované uvnitř libovolných importů typu v aktuálním souboru.</span><span class="sxs-lookup"><span data-stu-id="15ed5-192">Extension methods defined inside any type imports in the current file.</span></span>  
  
4. <span data-ttu-id="15ed5-193">Rozšiřující metody definované uvnitř libovolných importů oboru názvu v aktuálním souboru.</span><span class="sxs-lookup"><span data-stu-id="15ed5-193">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5. <span data-ttu-id="15ed5-194">Rozšiřující metody definované uvnitř libovolných importů typu na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-194">Extension methods defined inside any project-level type imports.</span></span>  
  
6. <span data-ttu-id="15ed5-195">Rozšiřující metody definované uvnitř libovolných importů oboru názvu na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="15ed5-195">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="15ed5-196">Pokud přednost nevyřeší nejednoznačnosti, můžete určit metodu, kterou voláte plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="15ed5-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="15ed5-197">Pokud `Print` metoda v předchozím příkladu je definována v modulu s názvem `StringExtensions`, je plně kvalifikovaný název `StringExtensions.Print(example)` místo `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="15ed5-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ed5-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15ed5-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="15ed5-199">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="15ed5-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="15ed5-200">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="15ed5-200">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="15ed5-201">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="15ed5-201">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="15ed5-202">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="15ed5-202">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="15ed5-203">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="15ed5-203">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="15ed5-204">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="15ed5-204">Attributes overview</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="15ed5-205">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15ed5-205">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
