---
title: x:FactoryMethod – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560192"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="becea-102">x:FactoryMethod – direktiva</span><span class="sxs-lookup"><span data-stu-id="becea-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="becea-103">Určuje jiné metody než konstruktor, který procesor XAML by měla použít pro inicializaci objektu po vyřešení jeho základní typ.</span><span class="sxs-lookup"><span data-stu-id="becea-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="becea-104">Použití atributu XAML, x: Arguments</span><span class="sxs-lookup"><span data-stu-id="becea-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="becea-105">Použití atributu XAML, x: Arguments jako jeden či více elementů</span><span class="sxs-lookup"><span data-stu-id="becea-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="becea-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="becea-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="becea-107">Název metody řetězec metody, která XAML procesory volání za účelem inicializace určenou jako instanci `object`.</span><span class="sxs-lookup"><span data-stu-id="becea-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="becea-108">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="becea-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="becea-109">Jeden nebo více elementů objektu pro objekty, které určují parametry metody objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="becea-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="becea-110">Pořadí je důležité. To znamená pořadí, ve kterém by měly být předány argumenty výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="becea-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="becea-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="becea-111">Remarks</span></span>  
 <span data-ttu-id="becea-112">Pokud `methodname` je metoda instance, nemůže být kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="becea-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="becea-113">Statické metody jako metody pro vytváření objektů jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="becea-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="becea-114">Pokud `methodname` je statická metoda `methodname` se poskytuje jako *typeName*. *methodName* kombinaci, kde *typeName* názvy třídy, která definuje statické výrobní metoda.</span><span class="sxs-lookup"><span data-stu-id="becea-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="becea-115">*typeName* může být předponou kvalifikací odkazující k typu v mapovaných xmlns.</span><span class="sxs-lookup"><span data-stu-id="becea-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="becea-116">*typeName* může být jiného typu než `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="becea-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="becea-117">Metoda factory musí být deklarované veřejnou metodu typu, který zálohuje elementu příslušný objekt.</span><span class="sxs-lookup"><span data-stu-id="becea-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="becea-118">Výrobní metoda musí vracet instanci, která je přiřadit k příslušný objekt.</span><span class="sxs-lookup"><span data-stu-id="becea-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="becea-119">Metody pro vytváření objektů by nikdy vrátit hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="becea-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="becea-120">`x:Arguments` funguje na principu nejlepší shodu pro podpis metody pro vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="becea-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="becea-121">Odpovídající nejprve vyhodnotí počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="becea-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="becea-122">Pokud existuje více než jednu možnou shodu počet parametrů, je typ parametru je určena Vyhodnocená a nejlepší shoda.</span><span class="sxs-lookup"><span data-stu-id="becea-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="becea-123">Pokud po této fáze hodnocení stále existuje nejednoznačnost, XAML procesoru chování není definováno.</span><span class="sxs-lookup"><span data-stu-id="becea-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="becea-124">`x:FactoryMethod` Použití elementu není použití elementu vlastnosti v typické smysl, protože direktiv značek neodkazuje na typ obsahující objekt elementu.</span><span class="sxs-lookup"><span data-stu-id="becea-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="becea-125">Očekává se, že použití elementu je méně častý než použití atributu.</span><span class="sxs-lookup"><span data-stu-id="becea-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="becea-126">`x:Arguments` (použití atributu nebo elementu) lze použít společně s `x:FactoryMethod` použití elementu, ale to není konkrétně zobrazený v částech využití.</span><span class="sxs-lookup"><span data-stu-id="becea-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="becea-127">`x:FactoryMethod` jak elementu musí předcházet před jinými prvky, vlastnost, musí předcházet všechny `x:Arguments` také ve formě elementy a musí předcházet text obsahu/vnitřní text/inicializace.</span><span class="sxs-lookup"><span data-stu-id="becea-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becea-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="becea-128">See Also</span></span>  
 [<span data-ttu-id="becea-129">x:Arguments – direktiva</span><span class="sxs-lookup"><span data-stu-id="becea-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
