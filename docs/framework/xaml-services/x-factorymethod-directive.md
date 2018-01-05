---
title: "x:FactoryMethod – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="d9d3d-102">x:FactoryMethod – direktiva</span><span class="sxs-lookup"><span data-stu-id="d9d3d-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="d9d3d-103">Určuje metodu než konstruktor, který se inicializovat objekt po vyřešení jeho základní typ měli použít procesor XAML.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="d9d3d-104">Použití atributu XAML, x: Arguments</span><span class="sxs-lookup"><span data-stu-id="d9d3d-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="d9d3d-105">Použití atributu XAML, x: Arguments jako elementy</span><span class="sxs-lookup"><span data-stu-id="d9d3d-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d9d3d-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="d9d3d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="d9d3d-107">Název metody řetězec metody, která XAML procesory volání k inicializaci instance zadaný jako `object`.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="d9d3d-108">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="d9d3d-109">Jeden či více elementů objektu pro objekty, které určují parametry metody objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="d9d3d-110">Pořadí je důležité. Označuje, pořadí, ve kterém by měla být předána argumenty metoda objektu factory.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9d3d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9d3d-111">Remarks</span></span>  
 <span data-ttu-id="d9d3d-112">Pokud `methodname` je metoda instance, nemůže být kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="d9d3d-113">Statické metody jako objekt pro vytváření metody jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="d9d3d-114">Pokud `methodname` je statickou metodu `methodname` je k dispozici jako *typeName*. *methodName* kombinací, kde *typeName* názvy třídy, která definuje metoda statické objektu factory.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="d9d3d-115">*typeName* může být předponou kvalifikovaný Pokud odkazující k typu v namapované xmlns.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="d9d3d-116">*typeName* může být jiného typu než `typeof(``object``)`.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="d9d3d-117">Metoda factory musí být deklarovaný veřejná metoda typu, který zálohuje relevantní objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="d9d3d-118">Metoda factory musí vrátit instanci, která je přiřadit k příslušný objekt.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="d9d3d-119">Metodami pro vytváření, nikdy by měl vrátit hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="d9d3d-120">`x:Arguments`funguje na princip nejlepší shodu pro podpis metody objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="d9d3d-121">Odpovídající nejprve vyhodnotí počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="d9d3d-122">Pokud existuje více než jeden možný odpovídající počet parametrů, je typ parametru se určuje vyhodnotí a nejlepší shodu.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="d9d3d-123">Pokud je stále nejednoznačnosti po této fáze hodnocení, XAML procesoru chování není definován.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="d9d3d-124">`x:FactoryMethod` Použití elementu není použití elementu vlastnosti v typické smysl, protože kód direktivy neodkazuje typ obsahující objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="d9d3d-125">Očekává se použití tohoto elementu je méně častých než použití atributu.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="d9d3d-126">`x:Arguments`(použití atributu nebo elementu) můžete použít společně s `x:FactoryMethod` použití elementu, ale to není konkrétně uvedené v částech využití.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="d9d3d-127">`x:FactoryMethod`jako element musí předcházet další prvky vlastnost, musí předcházet žádné `x:Arguments` také k dispozici jako elementy a musí předcházet jakýkoli text obsahu nebo vnitřní text/inicializace.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d3d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9d3d-128">See Also</span></span>  
 [<span data-ttu-id="d9d3d-129">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="d9d3d-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
