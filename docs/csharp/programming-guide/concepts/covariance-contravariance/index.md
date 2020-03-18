---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169867"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="7cc32-102">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="7cc32-103">V C#, kovariance a contravariance povolit implicitní převod odkazu pro typy polí, typy delegátů a argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7cc32-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="7cc32-104">Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.</span><span class="sxs-lookup"><span data-stu-id="7cc32-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="7cc32-105">Následující kód ukazuje rozdíl mezi kompatibilitou přiřazení, kovariance a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="7cc32-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="7cc32-106">Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu na pole méně odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="7cc32-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="7cc32-107">Ale tato operace není typ bezpečné, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="7cc32-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="7cc32-108">Kovariance a podpora kontravariance pro skupiny metod umožňuje odpovídající podpisy metod s typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="7cc32-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="7cc32-109">To umožňuje přiřadit delegátům nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí více odvozených typů (kovariance) nebo které přijímají parametry, které mají méně odvozených typů (kontravariance) než ty, které jsou určeny typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="7cc32-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="7cc32-110">Další informace naleznete [v tématech Odchylka v delegátech (C#)](./variance-in-delegates.md) a [Použití odchylky v delegátech (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7cc32-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="7cc32-111">Následující příklad kódu ukazuje kovariance a contravariance podporu pro skupiny metod.</span><span class="sxs-lookup"><span data-stu-id="7cc32-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="7cc32-112">V rozhraní .NET Framework 4 nebo novější C# podporuje kovariance a contravariance v obecných rozhraních a delegáty a umožňuje implicitní převod parametrů obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7cc32-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="7cc32-113">Další informace naleznete [v tématu Odchylka v obecných rozhraních (C#)](./variance-in-generic-interfaces.md) a [Odchylka v delegátech (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7cc32-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="7cc32-114">Následující příklad kódu ukazuje implicitní převod odkazu pro obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7cc32-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="7cc32-115">Obecné rozhraní nebo delegát se nazývá *varianta,* pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="7cc32-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="7cc32-116">C# umožňuje vytvořit vlastní variantní rozhraní a delegáty.</span><span class="sxs-lookup"><span data-stu-id="7cc32-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="7cc32-117">Další informace naleznete [v tématu Vytváření variantních obecných rozhraní (C#)](./creating-variant-generic-interfaces.md) a [odchylky v delegátech (C#).](./variance-in-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="7cc32-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="7cc32-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="7cc32-118">Related Topics</span></span>  
  
|<span data-ttu-id="7cc32-119">Nadpis</span><span class="sxs-lookup"><span data-stu-id="7cc32-119">Title</span></span>|<span data-ttu-id="7cc32-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7cc32-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7cc32-121">Odchylka v obecných rozhraních (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="7cc32-122">Popisuje kovariance a kontravariance v obecných rozhraních a poskytuje seznam variant obecných rozhraní v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cc32-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="7cc32-123">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="7cc32-124">Ukazuje, jak vytvořit vlastní variantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7cc32-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="7cc32-125">Použití odchylky v rozhraních pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="7cc32-126">Ukazuje, jak kovariance a contravariance podpora v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní vám může pomoci znovu použít kód.</span><span class="sxs-lookup"><span data-stu-id="7cc32-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="7cc32-127">Odchylka v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="7cc32-128">Popisuje kovariance a kontravariance v obecné a neobecné delegáty a poskytuje seznam variant obecných delegátů v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cc32-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="7cc32-129">Použití odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="7cc32-130">Ukazuje, jak používat kovariance a kontravariance podporu v neobecných delegátů k sladění podpisy metody s typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="7cc32-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="7cc32-131">Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)</span><span class="sxs-lookup"><span data-stu-id="7cc32-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="7cc32-132">Ukazuje, jak kovariance a contravariance podpora v `Func` a `Action` delegáti vám může pomoci znovu použít kód.</span><span class="sxs-lookup"><span data-stu-id="7cc32-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
