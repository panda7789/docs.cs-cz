---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564871"
---
# <a name="xarguments-directive"></a><span data-ttu-id="4ac60-102">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="4ac60-102">x:Arguments Directive</span></span>
<span data-ttu-id="4ac60-103">Argumenty vytváření balíčků pro deklaraci jiné než výchozí konstruktor objektu element v jazyce XAML, nebo na prohlášení metoda objektu factory.</span><span class="sxs-lookup"><span data-stu-id="4ac60-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="4ac60-104">Použití elementu XAML (jiný než výchozí konstruktor)</span><span class="sxs-lookup"><span data-stu-id="4ac60-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="4ac60-105">Použití elementu XAML (metoda factory)</span><span class="sxs-lookup"><span data-stu-id="4ac60-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4ac60-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="4ac60-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="4ac60-107">Jeden či více elementů objektu, které určují argumenty, které mají být předány metodě zálohování jiné než výchozí konstruktor nebo objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="4ac60-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="4ac60-108">Typická využití je použití inicializace textu v rámci objektu elementy zadat argument skutečné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4ac60-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="4ac60-109">Viz část o příklady.</span><span class="sxs-lookup"><span data-stu-id="4ac60-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="4ac60-110">Je důležité pořadí elementů.</span><span class="sxs-lookup"><span data-stu-id="4ac60-110">The order of the elements is significant.</span></span> <span data-ttu-id="4ac60-111">Typy XAML v pořadí musí odpovídat typy a zadejte pořadí zálohování přetížení metody konstruktoru nebo objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="4ac60-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="4ac60-112">Název metoda factory, která se má zpracovat žádné `x:Arguments` argumenty.</span><span class="sxs-lookup"><span data-stu-id="4ac60-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="4ac60-113">Závislosti</span><span class="sxs-lookup"><span data-stu-id="4ac60-113">Dependencies</span></span>  
 <span data-ttu-id="4ac60-114">`x:FactoryMethod` můžete upravit obor a chování kde `x:Arguments` platí.</span><span class="sxs-lookup"><span data-stu-id="4ac60-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="4ac60-115">Pokud žádné `x:FactoryMethod` není zadaný, `x:Arguments` se vztahuje na alternativní podpisy (jiné než výchozí) z konstruktorů zálohování.</span><span class="sxs-lookup"><span data-stu-id="4ac60-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="4ac60-116">Pokud `x:FactoryMethod` není zadaný, `x:Arguments` se vztahuje na přetížení metodu s názvem.</span><span class="sxs-lookup"><span data-stu-id="4ac60-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ac60-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ac60-117">Remarks</span></span>  
 <span data-ttu-id="4ac60-118">XAML 2006 může podporovat jiné než výchozí inicializace prostřednictvím inicializace text.</span><span class="sxs-lookup"><span data-stu-id="4ac60-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="4ac60-119">Praktické aplikace inicializaci text konstrukce techniky je však omezená.</span><span class="sxs-lookup"><span data-stu-id="4ac60-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="4ac60-120">Inicializace textu je považován za jednoho textového řetězce; proto pouze přidá funkce pro jeden parametr inicializace pokud převaděče typu je definována pro vytváření chování, které mohou analyzovat položky vlastních informací a vlastní oddělovače z řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ac60-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="4ac60-121">Textový řetězec pro objekt logiky je také potenciálně převaděče typů nativní výchozí daný analyzátor jazyka XAML pro zpracování primitiv než řetězec hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="4ac60-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="4ac60-122">`x:Arguments` Použití XAML není použití elementu vlastnosti v typické smysl, protože kód direktivy neodkazuje typ obsahující objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="4ac60-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="4ac60-123">Je třeba více podobají jiné direktivy `x:Code` kde element demarks rozsahu, ve kterém by měl být kód interpretován jako jiné než výchozí podřízené obsah.</span><span class="sxs-lookup"><span data-stu-id="4ac60-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="4ac60-124">V takovém případě typ jazyka XAML jednotlivých prvků objekt komunikuje informace o typy argumentů, který je používán XAML analyzátory k určení signatury metody, které objekt pro vytváření konkrétní konstruktor `x:Arguments` využití se pokouší odkazovat.</span><span class="sxs-lookup"><span data-stu-id="4ac60-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="4ac60-125">`x:Arguments` pro element objektu musí vytvářen předcházet další vlastnosti prvky, obsah, vnitřní text nebo řetězce inicializace objektu elementu.</span><span class="sxs-lookup"><span data-stu-id="4ac60-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="4ac60-126">Objekt elementů v rámci `x:Arguments` může být atributy a inicializace řetězce podle typu XAML a jeho základní metoda konstruktoru nebo objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="4ac60-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="4ac60-127">U objektu nebo argumenty můžete zadat vlastní XAML nebo XAML typy, které jsou jinak mimo výchozí obor názvů jazyka XAML odkazem zavedených předponu mapování.</span><span class="sxs-lookup"><span data-stu-id="4ac60-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="4ac60-128">XAML procesorů pomocí následujících pokynů určete, jak jsou argumenty zadaný v `x:Arguments` se má použít k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="4ac60-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="4ac60-129">Pokud `x:FactoryMethod` není zadaný, se porovná informace do zadané `x:FactoryMethod` (Všimněte si, že hodnota `x:FactoryMethod` je název metody, a metodu s názvem může mít přetížení.</span><span class="sxs-lookup"><span data-stu-id="4ac60-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="4ac60-130">Pokud `x:FactoryMethod` není zadán, informace se porovná sadu všechny přetížení veřejný konstruktor objektu.</span><span class="sxs-lookup"><span data-stu-id="4ac60-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="4ac60-131">Logika zpracování XAML pak porovná počet parametrů a vybere přetížení s odpovídající Arita.</span><span class="sxs-lookup"><span data-stu-id="4ac60-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="4ac60-132">Pokud existuje více než jednu shodu, procesor XAML musí porovnat typy parametrů na základě typů XAML elementů zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="4ac60-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="4ac60-133">Pokud je stále více než jednu shodu, není definován chování procesoru XAML.</span><span class="sxs-lookup"><span data-stu-id="4ac60-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="4ac60-134">Pokud `x:FactoryMethod` je zadán, ale metodu nelze přeložit, procesor XAML by měla vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="4ac60-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="4ac60-135">Použití atributu XAML `<x:Arguments>string</x:Arguments>` je technicky možné.</span><span class="sxs-lookup"><span data-stu-id="4ac60-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="4ac60-136">Však tímto způsobem žádné možnosti nad rámec co lze provést v opačném případě prostřednictvím inicializace text a typ převaděče a pomocí této syntaxe není záměr návrhu funkcí metoda factory XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="4ac60-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4ac60-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="4ac60-137">Examples</span></span>  
 <span data-ttu-id="4ac60-138">Následující příklad ukazuje konstruktor jiné než výchozí podpisem, pak použití XAML `x:Arguments` který přistupuje k této podpis.</span><span class="sxs-lookup"><span data-stu-id="4ac60-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="4ac60-139">Následující příklad ukazuje podpis metoda cílový objekt pro vytváření a používání XAML `x:Arguments` který přistupuje k této podpis.</span><span class="sxs-lookup"><span data-stu-id="4ac60-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ac60-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ac60-140">See Also</span></span>  
 [<span data-ttu-id="4ac60-141">Definování vlastních typů pro práci s technologií .NET Framework XAML Services</span><span class="sxs-lookup"><span data-stu-id="4ac60-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="4ac60-142">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="4ac60-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
