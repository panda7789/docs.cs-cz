---
title: Statické konstruktory – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 7b8171e75bbd27a1079f2c6cc1b7aef6400d7419
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115757"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="6971d-102">Statické konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6971d-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="6971d-103">Statický konstruktor slouží k inicializaci libovolných [statických](../../language-reference/keywords/static.md) dat nebo k provedení určité akce, kterou je třeba provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="6971d-103">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="6971d-104">Je volána automaticky před vytvořením první instance nebo odkazem na statické členy.</span><span class="sxs-lookup"><span data-stu-id="6971d-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a><span data-ttu-id="6971d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6971d-105">Remarks</span></span>
<span data-ttu-id="6971d-106">Statické konstruktory mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6971d-106">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="6971d-107">Statický konstruktor nepřijímá modifikátory přístupu ani parametry.</span><span class="sxs-lookup"><span data-stu-id="6971d-107">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="6971d-108">Třída nebo struktura může mít pouze jeden statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6971d-108">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="6971d-109">Statické konstruktory nemůžou být zděděné nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="6971d-109">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="6971d-110">Statický konstruktor nelze volat přímo a je určen pouze pro volání modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6971d-110">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="6971d-111">Je vyvoláno automaticky.</span><span class="sxs-lookup"><span data-stu-id="6971d-111">It is invoked automatically.</span></span>

- <span data-ttu-id="6971d-112">Uživatel nemá žádné řízení při spuštění statického konstruktoru v programu.</span><span class="sxs-lookup"><span data-stu-id="6971d-112">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="6971d-113">Statický konstruktor se nazývá automaticky pro inicializaci [třídy](../../language-reference/keywords/class.md) před vytvořením první instance nebo odkazováním na všechny statické členy.</span><span class="sxs-lookup"><span data-stu-id="6971d-113">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="6971d-114">Statický konstruktor se spustí před konstruktorem instance.</span><span class="sxs-lookup"><span data-stu-id="6971d-114">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="6971d-115">Statický konstruktor typu je volán, když je vyvolána statická metoda přiřazená události nebo delegátu a nikoli při jejím přiřazení.</span><span class="sxs-lookup"><span data-stu-id="6971d-115">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="6971d-116">Pokud jsou Inicializátory proměnných statického pole přítomny ve třídě statického konstruktoru, budou spuštěny v textovém pořadí, ve kterém jsou uvedeny v deklaraci třídy bezprostředně před provedením statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6971d-116">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="6971d-117">Pokud neposkytnete statický konstruktor pro inicializaci statických polí, všechna statická pole jsou inicializována na výchozí hodnotu, jak je uvedeno ve [výchozích C# hodnotách typů](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="6971d-117">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="6971d-118">Pokud statický konstruktor vyvolá výjimku, modul runtime je nespustí podruhé a typ zůstane Neinicializovaný po dobu života domény aplikace, ve které je program spuštěn.</span><span class="sxs-lookup"><span data-stu-id="6971d-118">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="6971d-119">Nejčastěji je výjimka <xref:System.TypeInitializationException> vyvolána, když statický konstruktor není schopen vytvořit instanci typu nebo pro neošetřenou výjimku, ke které dochází v rámci statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6971d-119">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="6971d-120">U implicitních statických konstruktorů, které nejsou explicitně definovány ve zdrojovém kódu, může řešení potíží vyžadovat kontrolu kódu zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="6971d-120">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="6971d-121">Přítomnost statického konstruktoru zabraňuje přidání atributu <xref:System.Reflection.TypeAttributes.BeforeFieldInit>ho typu.</span><span class="sxs-lookup"><span data-stu-id="6971d-121">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="6971d-122">To omezuje optimalizaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="6971d-122">This limits runtime optimization.</span></span>

- <span data-ttu-id="6971d-123">Pole deklarované jako `static readonly` lze přiřadit pouze v rámci deklarace nebo ve statickém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6971d-123">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="6971d-124">Pokud není vyžadován explicitní statický konstruktor, inicializujte statická pole v deklaraci, nikoli prostřednictvím statického konstruktoru pro lepší optimalizaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6971d-124">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="6971d-125">I když není přímo přístupný, měla by být popsána přítomnost explicitního statického konstruktoru, který pomáhá řešit výjimky inicializace.</span><span class="sxs-lookup"><span data-stu-id="6971d-125">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="6971d-126">Použití</span><span class="sxs-lookup"><span data-stu-id="6971d-126">Usage</span></span>

- <span data-ttu-id="6971d-127">Typické použití statických konstruktorů je v případě, že třída používá soubor protokolu a konstruktor je použit k zápisu položek do tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="6971d-127">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="6971d-128">Statické konstruktory jsou užitečné také při vytváření obálkových tříd pro nespravovaný kód, pokud konstruktor může volat metodu `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="6971d-128">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="6971d-129">Statické konstruktory jsou také pohodlným místem pro vynutit kontroly za běhu u parametru typu, který nelze kontrolovat v době kompilace prostřednictvím omezení (omezení parametrů typu).</span><span class="sxs-lookup"><span data-stu-id="6971d-129">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="6971d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="6971d-130">Example</span></span>
 <span data-ttu-id="6971d-131">V tomto příkladu třída `Bus` má statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6971d-131">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="6971d-132">Když je vytvořena první instance `Bus` (`bus1`), je vyvolán statický konstruktor pro inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="6971d-132">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="6971d-133">Ukázkový výstup ověřuje, zda se statický konstruktor spouští pouze jednou, i když jsou vytvořeny dvě instance `Bus` a že je spuštěn před spuštěním konstruktoru instance.</span><span class="sxs-lookup"><span data-stu-id="6971d-133">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a><span data-ttu-id="6971d-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6971d-134">C# language specification</span></span>
<span data-ttu-id="6971d-135">Další informace naleznete v části [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6971d-135">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6971d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6971d-136">See also</span></span>

- [<span data-ttu-id="6971d-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6971d-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6971d-138">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="6971d-138">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="6971d-139">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="6971d-139">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="6971d-140">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="6971d-140">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="6971d-141">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="6971d-141">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="6971d-142">Pokyny pro návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="6971d-142">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="6971d-143">Upozornění zabezpečení – CA2121: statické konstruktory by měly být privátní</span><span class="sxs-lookup"><span data-stu-id="6971d-143">Security Warning - CA2121: Static constructors should be private</span></span>](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
