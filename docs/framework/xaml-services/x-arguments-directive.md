---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: d4cff4c2f95d1418371921a3ac992a3b243d1c07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490814"
---
# <a name="xarguments-directive"></a><span data-ttu-id="7a928-102">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="7a928-102">x:Arguments Directive</span></span>
<span data-ttu-id="7a928-103">Argumenty vytváření balíčků pro deklaraci jiného než výchozího konstruktoru objektu prvku v XAML nebo pro deklaraci objektu factory metody.</span><span class="sxs-lookup"><span data-stu-id="7a928-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="7a928-104">Použití elementu XAML (jiný než výchozí konstruktor)</span><span class="sxs-lookup"><span data-stu-id="7a928-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="7a928-105">Použití elementu XAML (výrobní metoda)</span><span class="sxs-lookup"><span data-stu-id="7a928-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7a928-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="7a928-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="7a928-107">Jeden nebo více elementů objektu, které určují argumenty, které mají být předány jiné než výchozí konstruktor nebo výrobní metoda zálohování.</span><span class="sxs-lookup"><span data-stu-id="7a928-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="7a928-108">Typické použití je použití inicializace textu v rámci elementů objektu určit skutečný argument hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a928-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="7a928-109">Viz část o příklady.</span><span class="sxs-lookup"><span data-stu-id="7a928-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="7a928-110">Je důležité pořadí prvků.</span><span class="sxs-lookup"><span data-stu-id="7a928-110">The order of the elements is significant.</span></span> <span data-ttu-id="7a928-111">Typy XAML v pořadí musí odpovídají typům a zadejte pořadí přetížení základní konstruktor nebo výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="7a928-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="7a928-112">Název metoda factory, který by měl zpracovat žádné `x:Arguments` argumenty.</span><span class="sxs-lookup"><span data-stu-id="7a928-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="7a928-113">Závislosti</span><span class="sxs-lookup"><span data-stu-id="7a928-113">Dependencies</span></span>  
 <span data-ttu-id="7a928-114">`x:FactoryMethod` můžete upravit rozsah a chování kde `x:Arguments` platí.</span><span class="sxs-lookup"><span data-stu-id="7a928-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="7a928-115">Pokud ne `x:FactoryMethod` není zadána, `x:Arguments` se vztahuje na alternativní podpisy (jiné než výchozí) Základní konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7a928-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="7a928-116">Pokud `x:FactoryMethod` není zadána, `x:Arguments` platí pro přetíženou metodu s názvem.</span><span class="sxs-lookup"><span data-stu-id="7a928-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a928-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a928-117">Remarks</span></span>  
 <span data-ttu-id="7a928-118">XAML 2006 můžete podporovat jiné než výchozí inicializace prostřednictvím inicializace text.</span><span class="sxs-lookup"><span data-stu-id="7a928-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="7a928-119">Praktické aplikace inicializaci text konstrukce postup je však omezená.</span><span class="sxs-lookup"><span data-stu-id="7a928-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="7a928-120">Inicializace text je považován za jeden řetězec textu; proto pouze přidá funkce pro inicializaci jediný parametr Pokud je definován konvertor typu pro konstrukce chování, které mohou analyzovat položky vlastních informací a vlastních oddělovačů z řetězce.</span><span class="sxs-lookup"><span data-stu-id="7a928-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="7a928-121">Textový řetězec do objektu logiky je také potenciálně daný analyzátor XAML nativní výchozí konvertor typu pro zpracování primitivních elementů než řetězce true.</span><span class="sxs-lookup"><span data-stu-id="7a928-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="7a928-122">`x:Arguments` Využití XAML není použití elementu vlastnosti v typické smysl, protože direktiv značek neodkazuje na typ obsahující objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="7a928-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="7a928-123">Je třeba více podobají jiné direktivy `x:Code` kde element demarks rozsahu, ve kterém kód by měl být interpretován jako jiné než výchozí hodnota pro podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="7a928-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="7a928-124">V takovém případě komunikuje se informace o typů argumentů, které analyzátory XAML používají k určení signatury metody, které objekt pro vytváření konkrétního konstruktoru typu každého prvku objektu XAML `x:Arguments` využití se pokouší odkazovat.</span><span class="sxs-lookup"><span data-stu-id="7a928-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="7a928-125">`x:Arguments` pro element objektu při konstrukci musí předcházet před všechny ostatní elementy vlastnosti, obsah, vnitřní text nebo inicializace řetězce elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="7a928-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="7a928-126">Elementů objektu v rámci `x:Arguments` mohou obsahovat atributy a inicializace řetězce, jak je od typu XAML a jeho základní konstruktor nebo výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="7a928-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="7a928-127">Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo XAML, které jsou jinak mimo výchozí obor názvů XAML pomocí odkazu na zavedených předponu mapování.</span><span class="sxs-lookup"><span data-stu-id="7a928-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="7a928-128">XAML procesorů použijte následující pokyny k určení, jak jsou argumenty zadané v `x:Arguments` by měla sloužit k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="7a928-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="7a928-129">Pokud `x:FactoryMethod` není zadán, bude porovnána informace do zadaného `x:FactoryMethod` (Všimněte si, že hodnota `x:FactoryMethod` je název metody, a metodu s názvem může mít přetížení.</span><span class="sxs-lookup"><span data-stu-id="7a928-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="7a928-130">Pokud `x:FactoryMethod` není zadán, informace se porovnává se sadu všechna přetížení veřejný konstruktor objektu.</span><span class="sxs-lookup"><span data-stu-id="7a928-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="7a928-131">Logika zpracování XAML poté porovnává počet parametrů a vybere přetížení s odpovídající Arita.</span><span class="sxs-lookup"><span data-stu-id="7a928-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="7a928-132">Pokud existuje více než jedna shoda, by měl procesoru XAML porovnat typy parametrů na základě typů XAML prvky zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="7a928-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="7a928-133">Pokud je stále více než jedna shoda, XAML procesoru chování není definováno.</span><span class="sxs-lookup"><span data-stu-id="7a928-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="7a928-134">Pokud `x:FactoryMethod` je zadán, ale metoda nemůže být vyřešen, procesor XAML by měla vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="7a928-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="7a928-135">Použití atributu XAML `<x:Arguments>string</x:Arguments>` je technicky možný.</span><span class="sxs-lookup"><span data-stu-id="7a928-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="7a928-136">Však získáte žádné možnosti nad rámec běžné co může udělat jinak inicializace text a typ převaděče a pomocí této syntaxe není záměr návrh funkce XAML 2009 objekt pro vytváření metody.</span><span class="sxs-lookup"><span data-stu-id="7a928-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7a928-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="7a928-137">Examples</span></span>  
 <span data-ttu-id="7a928-138">Následující příklad ukazuje jiného než výchozího konstruktoru podpis a poté využití XAML `x:Arguments` , který přistupuje k podpisu.</span><span class="sxs-lookup"><span data-stu-id="7a928-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="7a928-139">Následující příklad ukazuje podpis metody cílový objekt pro vytváření a používání XAML `x:Arguments` , který přistupuje k podpisu.</span><span class="sxs-lookup"><span data-stu-id="7a928-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a928-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a928-140">See also</span></span>
- [<span data-ttu-id="7a928-141">Definování vlastních typů pro práci s technologií .NET Framework XAML Services</span><span class="sxs-lookup"><span data-stu-id="7a928-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="7a928-142">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7a928-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
