---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071533"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="4874a-102">x:FactoryMethod – direktiva</span><span class="sxs-lookup"><span data-stu-id="4874a-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="4874a-103">Určuje jinou metodu než konstruktor, kterou by měl procesor XAML použít k inicializaci objektu po vyřešení jeho typu zálohování.</span><span class="sxs-lookup"><span data-stu-id="4874a-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="4874a-104">Použití atributu XAML, bez x:Argumenty</span><span class="sxs-lookup"><span data-stu-id="4874a-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="4874a-105">Použití atributu XAML, x:Argumenty jako elementy</span><span class="sxs-lookup"><span data-stu-id="4874a-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4874a-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="4874a-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="4874a-107">Název metody řetězce metody, kterou procesory XAML volají k `object`inicializaci instance zadané jako .</span><span class="sxs-lookup"><span data-stu-id="4874a-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="4874a-108">Viz Poznámky.</span><span class="sxs-lookup"><span data-stu-id="4874a-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="4874a-109">Jeden nebo více prvků objektu pro objekty, které určují parametry metody výroby.</span><span class="sxs-lookup"><span data-stu-id="4874a-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="4874a-110">Řád je významný; označuje pořadí, ve kterém by měly být argumenty předány metodě factory.</span><span class="sxs-lookup"><span data-stu-id="4874a-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4874a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4874a-111">Remarks</span></span>  
 <span data-ttu-id="4874a-112">Pokud `methodname` je metoda instance, nelze ji kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="4874a-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="4874a-113">Statické metody jako metody výroby jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="4874a-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="4874a-114">Pokud `methodname` je statická `methodname` metoda, je `typeName.methodName` k `typeName` dispozici jako kombinace, kde názvy třídy, která definuje statickou metodu factory.</span><span class="sxs-lookup"><span data-stu-id="4874a-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="4874a-115">`typeName`může být prefix-qualified, pokud odkazuje na typ v mapovaných xmlns.</span><span class="sxs-lookup"><span data-stu-id="4874a-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="4874a-116">`typeName`může být jiný `typeof(object)`typ než .</span><span class="sxs-lookup"><span data-stu-id="4874a-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="4874a-117">Metoda factory musí být deklarovanou veřejnou metodou typu, který podporuje příslušný prvek objektu.</span><span class="sxs-lookup"><span data-stu-id="4874a-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="4874a-118">Metoda factory musí vrátit instanci, která je přiřaditelná příslušnému objektu.</span><span class="sxs-lookup"><span data-stu-id="4874a-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="4874a-119">Metody factory by nikdy vrátit null.</span><span class="sxs-lookup"><span data-stu-id="4874a-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="4874a-120">`x:Arguments`pracuje na principu nejlepší shody pro podpisy továrních metod.</span><span class="sxs-lookup"><span data-stu-id="4874a-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="4874a-121">Odpovídající vyhodnotí počet parametrů jako první.</span><span class="sxs-lookup"><span data-stu-id="4874a-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="4874a-122">Pokud existuje více než jedna možná shoda pro počet parametrů, je vyhodnocen typ parametru a určí se nejlepší shoda.</span><span class="sxs-lookup"><span data-stu-id="4874a-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="4874a-123">Pokud je stále nejednoznačnost po této fázi hodnocení, chování procesoru XAML není definována.</span><span class="sxs-lookup"><span data-stu-id="4874a-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="4874a-124">Použití `x:FactoryMethod` prvku není použití prvku vlastnosti v typickém smyslu, protože značka směrnice neodkazuje na typ prvku obsahujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="4874a-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="4874a-125">Očekává se, že použití prvku je méně časté než použití atributu.</span><span class="sxs-lookup"><span data-stu-id="4874a-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="4874a-126">`x:Arguments`(použití atributu nebo prvku) lze `x:FactoryMethod` použít spolu s použitím prvku, ale to není konkrétně uvedeno v části Použití.</span><span class="sxs-lookup"><span data-stu-id="4874a-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="4874a-127">`x:FactoryMethod`jako prvek musí předcházet jakékoli jiné prvky `x:Arguments` vlastnosti, musí předcházet všechny také k dispozici jako prvky a musí předcházet jakýkoli obsah/vnitřní text/inicializace textu.</span><span class="sxs-lookup"><span data-stu-id="4874a-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4874a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4874a-128">See also</span></span>

- [<span data-ttu-id="4874a-129">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="4874a-129">x:Arguments Directive</span></span>](xarguments-directive.md)
