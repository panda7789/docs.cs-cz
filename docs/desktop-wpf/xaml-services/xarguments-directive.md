---
title: x:Arguments – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071589"
---
# <a name="xarguments-directive"></a><span data-ttu-id="c4570-102">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="c4570-102">x:Arguments Directive</span></span>

<span data-ttu-id="c4570-103">Balíčky argumenty konstrukce pro deklaraci objektu objektu konstruktoru bez parametrů v XAML nebo pro deklaraci objektu metody factory.</span><span class="sxs-lookup"><span data-stu-id="c4570-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="c4570-104">Využití prvků XAML (konstruktor bez parametrů)</span><span class="sxs-lookup"><span data-stu-id="c4570-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="c4570-105">Použití prvku XAML (tovární metoda)</span><span class="sxs-lookup"><span data-stu-id="c4570-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="c4570-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="c4570-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="c4570-107">Jeden nebo více prvků objektu, které určují argumenty, které mají být předány záložnímu konstruktoru nebo metodě výroby bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c4570-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="c4570-108">Typické použití je použití inicializačního textu v rámci prvků objektu k určení skutečných hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="c4570-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="c4570-109">Viz příklady oddílu.</span><span class="sxs-lookup"><span data-stu-id="c4570-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="c4570-110">Pořadí prvků je významné.</span><span class="sxs-lookup"><span data-stu-id="c4570-110">The order of the elements is significant.</span></span> <span data-ttu-id="c4570-111">XAML typy v pořadí musí odpovídat typy a pořadí typů záložní konstruktor nebo přetížení metody výroby.</span><span class="sxs-lookup"><span data-stu-id="c4570-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="c4570-112">Název metody factory, která by `x:Arguments` měla zpracovat všechny argumenty.</span><span class="sxs-lookup"><span data-stu-id="c4570-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="c4570-113">Závislosti</span><span class="sxs-lookup"><span data-stu-id="c4570-113">Dependencies</span></span>

<span data-ttu-id="c4570-114">`x:FactoryMethod`můžete upravit rozsah a `x:Arguments` chování, kde platí.</span><span class="sxs-lookup"><span data-stu-id="c4570-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="c4570-115">Pokud `x:FactoryMethod` není zadán, `x:Arguments` platí pro alternativní (nevýchozí) podpisy záložních konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="c4570-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="c4570-116">Pokud `x:FactoryMethod` je `x:Arguments` zadán, platí pro přetížení pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="c4570-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4570-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4570-117">Remarks</span></span>

<span data-ttu-id="c4570-118">XAML 2006 může podporovat nevýchozí inicializaci prostřednictvím inicializačního textu.</span><span class="sxs-lookup"><span data-stu-id="c4570-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="c4570-119">Praktická aplikace techniky konstrukce inicializace textu je však omezená.</span><span class="sxs-lookup"><span data-stu-id="c4570-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="c4570-120">Inicializační text je považován za jeden textový řetězec; Proto pouze přidá schopnost pro jeden parametr inicializace, pokud převaděč typu je definován pro chování konstrukce, která může analyzovat vlastní informace položky a vlastní oddělovače z řetězce.</span><span class="sxs-lookup"><span data-stu-id="c4570-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="c4570-121">Také textový řetězec na objekt logiky je potenciálně dané XAML analyzátor nativní výchozí typ převaděč pro zpracování primitiv jiných než true řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4570-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="c4570-122">Použití `x:Arguments` XAML není použití prvku vlastnosti v typickém smyslu, protože značka směrnice neodkazuje na typ prvku obsahujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="c4570-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="c4570-123">Je více podobné jiné direktivy, jako je například `x:Code` kde prvek označuje rozsah, ve kterém by měl být interpretován jako jiné než výchozí pro podřízený obsah.</span><span class="sxs-lookup"><span data-stu-id="c4570-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="c4570-124">V tomto případě xaml typ každého prvku objektu sděluje informace o typech argumentů, které používají analyzátory XAML k určení, který konkrétní podpis metody výroby konstruktoru `x:Arguments` se pokouší odkazovat.</span><span class="sxs-lookup"><span data-stu-id="c4570-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="c4570-125">`x:Arguments`pro prvek objektu, který je vytvářen, musí předcházet všem ostatním prvkům vlastností, obsahu, vnitřnímu textu nebo inicializačním řetězcům prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="c4570-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="c4570-126">Objektové prvky v rámci `x:Arguments` mohou obsahovat atributy a inicializační řetězce, jak to povoluje daný typ XAML a jeho záložní konstruktor nebo metoda výroby.</span><span class="sxs-lookup"><span data-stu-id="c4570-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="c4570-127">Pro objekt nebo argumenty můžete zadat vlastní typy XAML nebo typy XAML, které jsou jinak mimo výchozí obor názvů XAML odkazem na vytvořené mapování předpony.</span><span class="sxs-lookup"><span data-stu-id="c4570-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="c4570-128">XAML procesory použít následující pokyny k určení, `x:Arguments` jak argumenty zadané v má být použit k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="c4570-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="c4570-129">Pokud `x:FactoryMethod` je zadán, informace je `x:FactoryMethod` porovnán se zadaným (všimněte si, že hodnota `x:FactoryMethod` je název metody a pojmenovaná metoda může mít přetížení.</span><span class="sxs-lookup"><span data-stu-id="c4570-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="c4570-130">Pokud `x:FactoryMethod` není zadán, informace je porovnán se sadou všech přetížení veřejné konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="c4570-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="c4570-131">Logika zpracování XAML pak porovná počet parametrů a vybere přetížení s odpovídající arity.</span><span class="sxs-lookup"><span data-stu-id="c4570-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="c4570-132">Pokud existuje více než jedna shoda, procesor XAML by měl porovnat typy parametrů na základě typů XAML zadaných prvků objektu.</span><span class="sxs-lookup"><span data-stu-id="c4570-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="c4570-133">Pokud je stále více než jedna shoda, chování procesoru XAML není definována.</span><span class="sxs-lookup"><span data-stu-id="c4570-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="c4570-134">Pokud `x:FactoryMethod` a je zadán, ale metoda nemůže být vyřešena, procesor XAML by měl vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="c4570-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="c4570-135">Použití atributu `<x:Arguments>string</x:Arguments>` XAML je technicky možné.</span><span class="sxs-lookup"><span data-stu-id="c4570-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="c4570-136">To však poskytuje žádné možnosti nad rámec toho, co by bylo možné provést jinak prostřednictvím převaděčů inicializace textu a typu a pomocí této syntaxe není záměr návrhu funkce metody výroby XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="c4570-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="c4570-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="c4570-137">Examples</span></span>

<span data-ttu-id="c4570-138">Následující příklad ukazuje podpis konstruktoru bez parametrů, pak xaml použití tohoto přístupu `x:Arguments` k tomuto podpisu.</span><span class="sxs-lookup"><span data-stu-id="c4570-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

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

<span data-ttu-id="c4570-139">Následující příklad ukazuje podpis cílové metody výroby, pak `x:Arguments` xaml použití, které přistupuje k tomuto podpisu.</span><span class="sxs-lookup"><span data-stu-id="c4570-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c4570-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4570-140">See also</span></span>

- [<span data-ttu-id="c4570-141">Definování vlastních typů pro použití s .NET XAML Services</span><span class="sxs-lookup"><span data-stu-id="c4570-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="c4570-142">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c4570-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
