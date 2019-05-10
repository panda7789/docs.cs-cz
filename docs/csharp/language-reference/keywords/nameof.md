---
title: nameof - C# odkaz
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: be60593ea5339db700140a6c7fb3fbd17af92912
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063795"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="54255-102">nameof (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="54255-102">nameof (C# Reference)</span></span>

<span data-ttu-id="54255-103">Používá k získání jednoduchého (nekvalifikovaného) řetězcového názvu proměnné, typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="54255-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>

<span data-ttu-id="54255-104">Při hlášení chyby v kódu, zapojování model-view-controller (MVC) odkazů, ohlásí změněné vlastnosti, události atd., často chcete zaznamenat název řetězce objektu metodu.</span><span class="sxs-lookup"><span data-stu-id="54255-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="54255-105">Pomocí `nameof` pomáhá udržovat váš kód platný při přejmenování definice.</span><span class="sxs-lookup"><span data-stu-id="54255-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="54255-106">Dříve jste museli používat řetězcové literály k odkazování na definice, které je třeba při přejmenování prvků kódu, protože nejste jisti nástroje ke kontrole tyto řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="54255-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>

<span data-ttu-id="54255-107">A `nameof` výrazu má tento tvar:</span><span class="sxs-lookup"><span data-stu-id="54255-107">A `nameof` expression has this form:</span></span>

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a><span data-ttu-id="54255-108">Případy použití klíčů</span><span class="sxs-lookup"><span data-stu-id="54255-108">Key Use Cases</span></span>

<span data-ttu-id="54255-109">Tyto příklady ukazují, případy použití klíče pro `nameof`.</span><span class="sxs-lookup"><span data-stu-id="54255-109">These examples show the key use cases for `nameof`.</span></span>

<span data-ttu-id="54255-110">Ověřte parametry:</span><span class="sxs-lookup"><span data-stu-id="54255-110">Validate parameters:</span></span>

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

<span data-ttu-id="54255-111">Odkazy na akce MVC:</span><span class="sxs-lookup"><span data-stu-id="54255-111">MVC Action links:</span></span>

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

<span data-ttu-id="54255-112">INotifyPropertyChanged:</span><span class="sxs-lookup"><span data-stu-id="54255-112">INotifyPropertyChanged:</span></span>

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

<span data-ttu-id="54255-113">Vlastnost závislosti XAML:</span><span class="sxs-lookup"><span data-stu-id="54255-113">XAML dependency property:</span></span>

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

<span data-ttu-id="54255-114">Protokolování:</span><span class="sxs-lookup"><span data-stu-id="54255-114">Logging:</span></span>

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

<span data-ttu-id="54255-115">Atributy:</span><span class="sxs-lookup"><span data-stu-id="54255-115">Attributes:</span></span>

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a><span data-ttu-id="54255-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="54255-116">Examples</span></span>

<span data-ttu-id="54255-117">Některé příklady jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="54255-117">Some C# examples:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="54255-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54255-118">Remarks</span></span>

<span data-ttu-id="54255-119">Argument `nameof` musí být jednoduchý název, úplný název, přístup ke členu, základní přístup pomocí zadaného člena nebo tento přístup pomocí zadaného člena.</span><span class="sxs-lookup"><span data-stu-id="54255-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="54255-120">Výraz argumentu identifikuje definice kódu, ale nikdy není vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="54255-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>

<span data-ttu-id="54255-121">Vzhledem k tomu, že argument musí být výraz syntakticky, existuje mnoho věcí zakázané, které nejsou vhodné seznamu.</span><span class="sxs-lookup"><span data-stu-id="54255-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="54255-122">Za zmínku, která způsobují chyby jsou následující: předdefinované typy (například `int` nebo `void`), typy připouštějící hodnotu Null (`Point?`), pole typů (`Customer[,]`), typy ukazatelů (`Buffer*`) kvalifikovaný alias (`A::B` ) a nevázaných obecných typů (`Dictionary<,>`), předzpracování symboly (`DEBUG`) a popisky (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="54255-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>

<span data-ttu-id="54255-123">Pokud je potřeba získat plně kvalifikovaný název, můžete použít `typeof` výrazu spolu s `nameof`.</span><span class="sxs-lookup"><span data-stu-id="54255-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="54255-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="54255-124">For example:</span></span>

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

<span data-ttu-id="54255-125">Bohužel `typeof` není konstantní výraz, stejně jako `nameof`, takže `typeof` nelze použít ve spojení s `nameof` ve stejné umístění jako `nameof`.</span><span class="sxs-lookup"><span data-stu-id="54255-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="54255-126">Následující by například způsobila chybu kompilace CS0182:</span><span class="sxs-lookup"><span data-stu-id="54255-126">For example, the following would cause a CS0182 compile error:</span></span>

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

<span data-ttu-id="54255-127">V příkladech se zobrazí, že můžete použít název typu a přístup k názvu metody instance.</span><span class="sxs-lookup"><span data-stu-id="54255-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="54255-128">Nemusíte mít instanci typu, jako požadavků ve vyhodnoceném výrazy.</span><span class="sxs-lookup"><span data-stu-id="54255-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="54255-129">Protože se právě odkazující na název a bez použití instance data, není potřeba contrive instanci proměnné nebo výrazu může být příliš pohodlné, v některých situacích a názvu typu.</span><span class="sxs-lookup"><span data-stu-id="54255-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>

<span data-ttu-id="54255-130">Můžete odkazovat na členy třídy ve výrazech atribut ve třídě.</span><span class="sxs-lookup"><span data-stu-id="54255-130">You can reference the members of a class in attribute expressions on the class.</span></span>

<span data-ttu-id="54255-131">Neexistuje žádný způsob, jak získat podpisy informace, jako "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="54255-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="54255-132">Jedním ze způsobů, který je použití výrazu `Expression e = () => A.B.Method1("s1", "s2")`a o přijetí změn MemberInfo z výsledný strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="54255-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="54255-133">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="54255-133">Language Specifications</span></span>

<span data-ttu-id="54255-134">Další informace najdete v tématu [výrazy Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54255-134">For more information, see [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="54255-135">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="54255-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="54255-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54255-136">See also</span></span>

- [<span data-ttu-id="54255-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54255-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="54255-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="54255-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="54255-139">typeof</span><span class="sxs-lookup"><span data-stu-id="54255-139">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
