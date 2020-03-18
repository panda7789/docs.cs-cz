---
title: Statické konstruktory – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170114"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="d6213-102">Statické konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d6213-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="d6213-103">Statický konstruktor se používá k inicializaci [všech statických](../../language-reference/keywords/static.md) dat nebo k provedení určité akce, kterou je třeba provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="d6213-103">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="d6213-104">Je volána automaticky před vytvořením první instance nebo jsou odkazovány na statické členy.</span><span class="sxs-lookup"><span data-stu-id="d6213-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a><span data-ttu-id="d6213-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6213-105">Remarks</span></span>
<span data-ttu-id="d6213-106">Statické konstruktory mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d6213-106">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="d6213-107">Statický konstruktor nepřijímá modifikátory přístupu nebo má parametry.</span><span class="sxs-lookup"><span data-stu-id="d6213-107">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="d6213-108">Třída nebo struktura může mít pouze jeden statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d6213-108">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="d6213-109">Statické konstruktory nelze zdědit nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="d6213-109">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="d6213-110">Statický konstruktor nelze volat přímo a je určen pouze pro volání clr (common language runtime).</span><span class="sxs-lookup"><span data-stu-id="d6213-110">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="d6213-111">Je vyvolána automaticky.</span><span class="sxs-lookup"><span data-stu-id="d6213-111">It is invoked automatically.</span></span>

- <span data-ttu-id="d6213-112">Uživatel nemá žádnou kontrolu nad tím, kdy je statický konstruktor spuštěn v programu.</span><span class="sxs-lookup"><span data-stu-id="d6213-112">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="d6213-113">Statický konstruktor je volán automaticky k inicializaci [třídy](../../language-reference/keywords/class.md) před vytvořením první instance nebo jsou odkazovány na statické členy.</span><span class="sxs-lookup"><span data-stu-id="d6213-113">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="d6213-114">Statický konstruktor bude spuštěn před konstruktorem instance.</span><span class="sxs-lookup"><span data-stu-id="d6213-114">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="d6213-115">Statický konstruktor typu je volán, když je vyvolána statická metoda přiřazená události nebo delegátovi, nikoli při jeho přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d6213-115">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="d6213-116">Pokud statické pole proměnné inicializátory jsou přítomny ve třídě statickékonstruktor, budou provedeny v textovém pořadí, ve kterém se zobrazí v deklaraci třídy bezprostředně před spuštěním statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d6213-116">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="d6213-117">Pokud nezadáte statický konstruktor pro inicializaci statických polí, všechna statická pole jsou inicializována na výchozí hodnotu uvedenou v [výchozích hodnotách typů Jazyka C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="d6213-117">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="d6213-118">Pokud statický konstruktor vyvolá výjimku, runtime ji nevyvolá podruhé a typ zůstane neinicializován po dobu životnosti domény aplikace, ve které je program spuštěn.</span><span class="sxs-lookup"><span data-stu-id="d6213-118">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="d6213-119">Nejčastěji je <xref:System.TypeInitializationException> vyvolána výjimka, když statický konstruktor není schopen vytvořit instanci typu nebo pro neošetřenou výjimku, ke které dochází v rámci statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d6213-119">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="d6213-120">Pro implicitní statické konstruktory, které nejsou explicitně definovány ve zdrojovém kódu, může řešení potíží vyžadovat kontrolu kódu zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="d6213-120">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="d6213-121">Přítomnost statického konstruktoru zabraňuje přidání <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atributu type.</span><span class="sxs-lookup"><span data-stu-id="d6213-121">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="d6213-122">To omezuje optimalizaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="d6213-122">This limits runtime optimization.</span></span>

- <span data-ttu-id="d6213-123">Pole deklarované jako `static readonly` může být přiřazeno pouze jako součást jeho deklarace nebo ve statickém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d6213-123">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="d6213-124">Pokud explicitní statický konstruktor není vyžadován, inicializovat statická pole na deklaraci, nikoli prostřednictvím statického konstruktoru pro lepší optimalizaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="d6213-124">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="d6213-125">Ačkoli není přímo přístupné, přítomnost explicitní statický konstruktor by měl být dokumentován pomoci při řešení potíží s výjimkami inicializace.</span><span class="sxs-lookup"><span data-stu-id="d6213-125">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="d6213-126">Využití</span><span class="sxs-lookup"><span data-stu-id="d6213-126">Usage</span></span>

- <span data-ttu-id="d6213-127">Typické použití statických konstruktorů je, když třída používá soubor protokolu a konstruktor se používá k zápisu položek do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="d6213-127">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="d6213-128">Statické konstruktory jsou také užitečné při vytváření tříd obálky pro nespravovaný kód, když konstruktor může volat metodu. `LoadLibrary`</span><span class="sxs-lookup"><span data-stu-id="d6213-128">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="d6213-129">Statické konstruktory jsou také vhodné místo pro vynucení kontroly za běhu na parametr typu, který nelze zkontrolovat v době kompilace pomocí omezení (Omezení parametru typu).</span><span class="sxs-lookup"><span data-stu-id="d6213-129">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="d6213-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6213-130">Example</span></span>
 <span data-ttu-id="d6213-131">V tomto příkladu má třída `Bus` statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d6213-131">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="d6213-132">Při vytvoření první `Bus` instance`bus1`( ), statický konstruktor je vyvolána k inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="d6213-132">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="d6213-133">Ukázkový výstup ověří, že statický konstruktor spustí pouze jednou, `Bus` i když jsou vytvořeny dvě instance a že je spuštěn před spuštěním konstruktoru instance.</span><span class="sxs-lookup"><span data-stu-id="d6213-133">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="d6213-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6213-134">C# language specification</span></span>
<span data-ttu-id="d6213-135">Další informace naleznete v části [Statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d6213-135">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d6213-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6213-136">See also</span></span>

- [<span data-ttu-id="d6213-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6213-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d6213-138">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="d6213-138">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d6213-139">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d6213-139">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="d6213-140">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="d6213-140">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="d6213-141">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="d6213-141">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="d6213-142">Pokyny pro návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="d6213-142">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="d6213-143">Upozornění zabezpečení - CA2121: Statické konstruktory by měly být soukromé</span><span class="sxs-lookup"><span data-stu-id="d6213-143">Security Warning - CA2121: Static constructors should be private</span></span>](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
