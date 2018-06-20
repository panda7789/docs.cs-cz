---
title: nameof (referenční dokumentace jazyka C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 2695095aa4bf2035d8766f3cbcb82f4fbb290e22
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208347"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="d46fc-102">nameof (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d46fc-102">nameof (C# Reference)</span></span>

<span data-ttu-id="d46fc-103">Použít k získání jednoduchým řetězcem (neúplné) název proměnné, typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="d46fc-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>  

<span data-ttu-id="d46fc-104">Při zasílání zpráv o chybách v kódu zapojování odkazy model-view-controller (MVC), která iniciovala změněné vlastnosti události, atd., často chcete zaznamenat název řetězce objektu metodu.</span><span class="sxs-lookup"><span data-stu-id="d46fc-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="d46fc-105">Pomocí `nameof` pomáhá udržovat kódu platný při přejmenování definice.</span><span class="sxs-lookup"><span data-stu-id="d46fc-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="d46fc-106">Před jste museli používat řetězcové literály odkazovat na definice, což je křehká při přejmenování elementy kódu, protože nástroje neznáte Zkontrolujte tyto textové literály.</span><span class="sxs-lookup"><span data-stu-id="d46fc-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>  
  
 <span data-ttu-id="d46fc-107">A `nameof` výraz má tento formát:</span><span class="sxs-lookup"><span data-stu-id="d46fc-107">A `nameof` expression has this form:</span></span>  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a><span data-ttu-id="d46fc-108">Případy použití klíče</span><span class="sxs-lookup"><span data-stu-id="d46fc-108">Key Use Cases</span></span>  
 <span data-ttu-id="d46fc-109">Tyto příklady ukazují případů použití klíče pro `nameof`.</span><span class="sxs-lookup"><span data-stu-id="d46fc-109">These examples show the key use cases for `nameof`.</span></span>  
  
 <span data-ttu-id="d46fc-110">Ověření parametrů:</span><span class="sxs-lookup"><span data-stu-id="d46fc-110">Validate parameters:</span></span>  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 <span data-ttu-id="d46fc-111">Akce MVC odkazy:</span><span class="sxs-lookup"><span data-stu-id="d46fc-111">MVC Action links:</span></span>  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 <span data-ttu-id="d46fc-112">Rozhraní INotifyPropertyChanged.:</span><span class="sxs-lookup"><span data-stu-id="d46fc-112">INotifyPropertyChanged:</span></span>  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 <span data-ttu-id="d46fc-113">Vlastnost závislosti XAML:</span><span class="sxs-lookup"><span data-stu-id="d46fc-113">XAML dependency property:</span></span>  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 <span data-ttu-id="d46fc-114">Protokolování:</span><span class="sxs-lookup"><span data-stu-id="d46fc-114">Logging:</span></span>  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 <span data-ttu-id="d46fc-115">Atributy:</span><span class="sxs-lookup"><span data-stu-id="d46fc-115">Attributes:</span></span>  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a><span data-ttu-id="d46fc-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="d46fc-116">Examples</span></span>  
 <span data-ttu-id="d46fc-117">Příklady C#:</span><span class="sxs-lookup"><span data-stu-id="d46fc-117">Some C# examples:</span></span>  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
class Test {  
    static void Main (string[] args) {  
        Console.WriteLine(nameof(C)); // -> "C"  
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"  
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"  
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]  
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"  
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]  
        Console.WriteLine(nameof(f)); // -> "f"  
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]  
        // Console.WriteLine(nameof(f<>)); -> [syntax error]  
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]  
    }
}
```  
  
## <a name="remarks"></a><span data-ttu-id="d46fc-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d46fc-118">Remarks</span></span>  
 <span data-ttu-id="d46fc-119">Argument `nameof` musí být jednoduchý název, kvalifikovaný název, přístup ke členu, přístupu na základě s zadaného člena nebo tento přístup pomocí zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="d46fc-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="d46fc-120">Výraz argumentu identifikuje definici kód, ale nikdy vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="d46fc-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>  
  
 <span data-ttu-id="d46fc-121">Protože argument musí být výraz syntakticky, existují celou řadu věcí, které jsou povoleny a které nejsou užitečné k zobrazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="d46fc-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="d46fc-122">Toto jsou důležité zmínit, které způsobují chyby: předdefinované typy (například `int` nebo `void`), typy s možnou hodnotou Null (`Point?`), pole typů (`Customer[,]`), typy ukazatelů (`Buffer*`) kvalifikovaný alias (`A::B` ) a nevázaných obecných typů (`Dictionary<,>`), předzpracování symboly (`DEBUG`) a popisky (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="d46fc-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>  
  
 <span data-ttu-id="d46fc-123">Pokud potřebujete získat plně kvalifikovaný název, můžete použít `typeof` výraz spolu s `nameof`.</span><span class="sxs-lookup"><span data-stu-id="d46fc-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="d46fc-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d46fc-124">For example:</span></span>
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 <span data-ttu-id="d46fc-125">Bohužel `typeof` není konstantní výraz jako `nameof`, takže `typeof` nelze použít ve spojení s `nameof` ve stejné umístí jako `nameof`.</span><span class="sxs-lookup"><span data-stu-id="d46fc-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="d46fc-126">Například následující způsobí chybu kompilace CS0182:</span><span class="sxs-lookup"><span data-stu-id="d46fc-126">For example, the following would cause a CS0182 compile error:</span></span>
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 <span data-ttu-id="d46fc-127">V příkladech uvidíte, že můžete použít název typu a přístup k metoda název instance.</span><span class="sxs-lookup"><span data-stu-id="d46fc-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="d46fc-128">Není nutné mít instanci typu, jako v požadovaných vyhodnotí výrazy.</span><span class="sxs-lookup"><span data-stu-id="d46fc-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="d46fc-129">Protože se právě odkazující na název a nepoužíváte instance data, není nutné contrive proměnné instance nebo výraz může být velmi praktické, v některých situacích a použití název typu.</span><span class="sxs-lookup"><span data-stu-id="d46fc-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>  
  
 <span data-ttu-id="d46fc-130">Členy třídy ve výrazech atribut na třídu, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="d46fc-130">You can reference the members of a class in attribute expressions on the class.</span></span>  
  
 <span data-ttu-id="d46fc-131">Neexistuje žádný způsob, jak získat podpisy informace, jako "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="d46fc-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="d46fc-132">Je možné provést pomocí výrazu, `Expression e = () => A.B.Method1("s1", "s2")`a MemberInfo – ze stromu výsledný výraz pro vyžádání obsahu.</span><span class="sxs-lookup"><span data-stu-id="d46fc-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="d46fc-133">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="d46fc-133">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d46fc-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d46fc-134">See Also</span></span>  
 [<span data-ttu-id="d46fc-135">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d46fc-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d46fc-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d46fc-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d46fc-137">typeof</span><span class="sxs-lookup"><span data-stu-id="d46fc-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 
