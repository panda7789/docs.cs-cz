---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053778"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="b1e23-102">x:FactoryMethod – direktiva</span><span class="sxs-lookup"><span data-stu-id="b1e23-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="b1e23-103">Určuje metodu jinou než konstruktor, který by měl procesor XAML použít k inicializaci objektu po vyřešení jeho typu zálohování.</span><span class="sxs-lookup"><span data-stu-id="b1e23-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="b1e23-104">Použití atributu XAML bez X:Arguments –</span><span class="sxs-lookup"><span data-stu-id="b1e23-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="b1e23-105">Použití atributu XAML, X:arguments – jako element (y)</span><span class="sxs-lookup"><span data-stu-id="b1e23-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b1e23-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="b1e23-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="b1e23-107">Řetězcová metoda názvu metody, kterou volají procesory XAML pro inicializaci instance určené jako `object`.</span><span class="sxs-lookup"><span data-stu-id="b1e23-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="b1e23-108">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="b1e23-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="b1e23-109">Jeden nebo více prvků objektu pro objekty, které určují parametry metody továrního nastavení.</span><span class="sxs-lookup"><span data-stu-id="b1e23-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="b1e23-110">Pořadí je důležité. označuje pořadí, ve kterém by měly být argumenty předány metodě pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="b1e23-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e23-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1e23-111">Remarks</span></span>  
 <span data-ttu-id="b1e23-112">Pokud `methodname` je metoda instance, nemůže být kvalifikována.</span><span class="sxs-lookup"><span data-stu-id="b1e23-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="b1e23-113">Jsou podporovány statické metody jako metody výroby.</span><span class="sxs-lookup"><span data-stu-id="b1e23-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="b1e23-114">Pokud `methodname` je statická metoda, `methodname` je k dispozici jako *TypeName*. *methodName* kombinace, kde *TypeName* jmenuje třídu, která definuje statickou metodu Factory.</span><span class="sxs-lookup"><span data-stu-id="b1e23-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="b1e23-115">*TypeName* může být kvalifikována předpona, pokud se odkazuje na typ v mapované xmlns.</span><span class="sxs-lookup"><span data-stu-id="b1e23-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="b1e23-116">*TypeName* může být jiný typ než `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="b1e23-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="b1e23-117">Metoda factory musí být deklarovanou veřejnou metodou typu, který zálohuje příslušný prvek objektu.</span><span class="sxs-lookup"><span data-stu-id="b1e23-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="b1e23-118">Metoda factory musí vracet instanci, kterou lze přiřadit příslušnému objektu.</span><span class="sxs-lookup"><span data-stu-id="b1e23-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="b1e23-119">Metody továrny by nikdy neměly vracet hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1e23-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="b1e23-120">`x:Arguments`funguje na principu nejlepší shody pro signatury metod výroby.</span><span class="sxs-lookup"><span data-stu-id="b1e23-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="b1e23-121">Při shodě se vyhodnocuje počet parametrů jako první.</span><span class="sxs-lookup"><span data-stu-id="b1e23-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="b1e23-122">Pokud existuje více než jedna možná shoda pro počet parametrů, je pak vyhodnocen typ parametru a je určena nejlepší shoda.</span><span class="sxs-lookup"><span data-stu-id="b1e23-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="b1e23-123">Pokud je po této fázi vyhodnocení stále nejednoznačnost, chování procesoru XAML není definováno.</span><span class="sxs-lookup"><span data-stu-id="b1e23-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="b1e23-124">Použití `x:FactoryMethod` prvku není využití prvku vlastností v typickém smyslu, protože označení direktivy neodkazuje na objekt obsahující typ elementu.</span><span class="sxs-lookup"><span data-stu-id="b1e23-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="b1e23-125">Je očekáváno, že použití prvku je méně běžné než použití atributu.</span><span class="sxs-lookup"><span data-stu-id="b1e23-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="b1e23-126">`x:Arguments`(buď atribut nebo použití elementu) lze použít společně s `x:FactoryMethod` použitím elementu, ale to není výslovně uvedeno v oddílech použití.</span><span class="sxs-lookup"><span data-stu-id="b1e23-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="b1e23-127">`x:FactoryMethod`prvek musí předcházet všem ostatním prvkům vlastností, musí předcházet `x:Arguments` také jako element a musí předcházet jakémukoli obsahu, vnitřní text nebo inicializační text.</span><span class="sxs-lookup"><span data-stu-id="b1e23-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e23-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1e23-128">See also</span></span>

- [<span data-ttu-id="b1e23-129">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="b1e23-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
