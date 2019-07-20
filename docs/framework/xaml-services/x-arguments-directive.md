---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5bcd629e306169c1f7a61a316d76203827a2d0fe
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364264"
---
# <a name="xarguments-directive"></a><span data-ttu-id="9ebe6-102">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="9ebe6-102">x:Arguments Directive</span></span>
<span data-ttu-id="9ebe6-103">Argumenty konstrukce balíčků pro deklaraci elementu objektu konstruktoru bez parametrů v jazyce XAML nebo pro deklaraci objektu metody Factory.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="9ebe6-104">Použití prvku XAML (konstruktor bez parametrů)</span><span class="sxs-lookup"><span data-stu-id="9ebe6-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="9ebe6-105">Použití elementu XAML (metoda Factory)</span><span class="sxs-lookup"><span data-stu-id="9ebe6-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9ebe6-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="9ebe6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="9ebe6-107">Jeden nebo více prvků objektu, které určují argumenty, které mají být předány do back-konstruktoru bez parametrů nebo metody Factory.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="9ebe6-108">Typické použití je použití inicializačního textu v rámci prvků objektu k určení skutečných hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="9ebe6-109">Viz část příklady.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="9ebe6-110">Pořadí prvků je významné.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-110">The order of the elements is significant.</span></span> <span data-ttu-id="9ebe6-111">Typy XAML v pořadí musí odpovídat typům a pořadím typu konstruktoru zálohování nebo přetížení metody výroby.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="9ebe6-112">Název metody objektu pro vytváření, která by měla zpracovat `x:Arguments` jakékoli argumenty.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="9ebe6-113">Závislosti</span><span class="sxs-lookup"><span data-stu-id="9ebe6-113">Dependencies</span></span>  
 <span data-ttu-id="9ebe6-114">`x:FactoryMethod`může upravit rozsah a chování, kde `x:Arguments` platí.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="9ebe6-115">Pokud není zadán, `x:Arguments` platí pro alternativní (nevýchozí) podpisy záložních konstruktorů. `x:FactoryMethod`</span><span class="sxs-lookup"><span data-stu-id="9ebe6-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="9ebe6-116">Pokud `x:FactoryMethod` je zadáno, `x:Arguments` platí pro přetížení pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ebe6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ebe6-117">Remarks</span></span>  
 <span data-ttu-id="9ebe6-118">XAML 2006 může podporovat nevýchozí inicializaci prostřednictvím inicializačního textu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="9ebe6-119">Praktické použití techniky konstrukce inicializačního textu je však omezené.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="9ebe6-120">Inicializační text je považován za jeden textový řetězec; Proto přidává pouze schopnost pro inicializaci jednoho parametru, pokud není definován konvertor typu pro chování konstrukce, které může analyzovat vlastní položky informací a vlastní oddělovače z řetězce.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="9ebe6-121">Také textový řetězec do logiky objektu je potenciálně pro zpracování primitivních primitivních typů, které jsou jiné než skutečný řetězec, zadán z nativního převaděče pro kódování XAML.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="9ebe6-122">Použití `x:Arguments` jazyka XAML není použití prvku vlastností v typickém smyslu, protože označení direktivy neodkazuje na objekt obsahující typ elementu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="9ebe6-123">Je více podobají na jiné direktivy, jako `x:Code` například, kde element označuje rozsah, ve kterém by měly být značky interpretovány jako jiné než výchozí pro podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="9ebe6-124">V tomto případě typ XAML každého prvku objektu komunikuje informace o typech argumentů, které jsou používány analyzátory jazyka XAML k určení, které konkrétní konstruktory výrobní metody signatury `x:Arguments` se o použití pokouší odkazovat.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="9ebe6-125">`x:Arguments`pro konstruovaný prvek objektu musí předcházet libovolné jiné prvky vlastností, obsah, vnitřní text nebo inicializační řetězce elementu Object.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="9ebe6-126">Prvky objektu v rámci `x:Arguments` mohou zahrnovat atributy a inicializační řetězce, jak je povoleno tímto typem XAML a jeho záložní konstruktor nebo výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="9ebe6-127">Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo XAML, které jsou jinak mimo výchozí obor názvů XAML odkazem na zavedená mapování předpon.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="9ebe6-128">Procesory XAML používají následující pokyny k určení toho, jak by měly `x:Arguments` být použity argumenty určené v pro vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="9ebe6-129">Je `x:FactoryMethod` -li parametr zadán, jsou informace porovnány `x:FactoryMethod` se zadaným ( `x:FactoryMethod` Všimněte si, že hodnota je název metody a pojmenovaná metoda může mít přetížení.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="9ebe6-130">Není `x:FactoryMethod` -li parametr zadán, jsou informace porovnány se sadou všech přetížení veřejného konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="9ebe6-131">Logika zpracování XAML pak porovná počet parametrů a vybere přetížení se stejnou aritou.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="9ebe6-132">Pokud existuje více než jedna shoda, by měl procesor XAML porovnat typy parametrů založené na typech XAML zadaných prvků objektu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="9ebe6-133">Pokud je stále více než jedna shoda, chování procesoru XAML není definováno.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="9ebe6-134">`x:FactoryMethod` Pokud je zadán, ale metodu nelze vyřešit, procesor XAML by měl vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="9ebe6-135">Použití `<x:Arguments>string</x:Arguments>` atributu XAML je technicky možné.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="9ebe6-136">To však neposkytuje žádné možnosti nad rámec toho, co by bylo možné provést jinak prostřednictvím inicializačního textu a převaděčů typů, a použití této syntaxe není záměrem návrhu funkcí rozhraní XAML 2009 pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9ebe6-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="9ebe6-137">Examples</span></span>  
 <span data-ttu-id="9ebe6-138">Následující příklad ukazuje signaturu konstruktoru bez parametrů, pak použití jazyka XAML pro `x:Arguments` přístup k tomuto podpisu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 <span data-ttu-id="9ebe6-139">Následující příklad ukazuje cílový podpis metody výroby, potom použití `x:Arguments` XAML, který přistupuje k tomuto podpisu.</span><span class="sxs-lookup"><span data-stu-id="9ebe6-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ebe6-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ebe6-140">See also</span></span>

- [<span data-ttu-id="9ebe6-141">Definování vlastních typů pro práci s technologií .NET Framework XAML Services</span><span class="sxs-lookup"><span data-stu-id="9ebe6-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="9ebe6-142">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9ebe6-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
