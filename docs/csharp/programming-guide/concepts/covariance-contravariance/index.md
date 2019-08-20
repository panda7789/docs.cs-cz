---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 1d5a1de1825e585512f694a0cd72cee9b37cda36
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595283"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="182db-102">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="182db-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="182db-103">V C#, kovariance a kontravariance umožňují implicitní převod odkazů pro typy polí, typy delegátů a argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="182db-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="182db-104">Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.</span><span class="sxs-lookup"><span data-stu-id="182db-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="182db-105">Následující kód ukazuje rozdíl mezi kompatibilitou přiřazení, koodchylky a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="182db-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="182db-106">Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu na pole méně odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="182db-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="182db-107">Tato operace ale není typově bezpečná, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="182db-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="182db-108">Kovariance a podpora kontravariance pro skupiny metod umožňuje porovnávací signatury metod s typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="182db-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="182db-109">To vám umožňuje přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="182db-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="182db-110">Další informace naleznete v tématu [Variance in DelegatesC#()](./variance-in-delegates.md) a [using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="182db-110">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="182db-111">Následující příklad kódu ukazuje kovariance a podporu kontravariance pro skupiny metod.</span><span class="sxs-lookup"><span data-stu-id="182db-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="182db-112">V .NET Framework 4 nebo novější C# podporuje kovarianci a kontravariance v obecných rozhraních a delegátech a povoluje implicitní převod parametrů obecného typu.</span><span class="sxs-lookup"><span data-stu-id="182db-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="182db-113">Další informace naleznete v tématu [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) a [Variance in DelegatesC#()](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="182db-113">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="182db-114">Následující příklad kódu ukazuje implicitní převod odkazu pro Obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="182db-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="182db-115">Obecné rozhraní nebo delegát se nazývá *typ variant* , pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="182db-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="182db-116">C#umožňuje vytvořit vlastní variantní rozhraní a delegáty.</span><span class="sxs-lookup"><span data-stu-id="182db-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="182db-117">Další informace najdete v tématu [Vytvoření variantních obecných rozhraníC#()](./creating-variant-generic-interfaces.md) a [Variance v delegátech (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="182db-117">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="182db-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="182db-118">Related Topics</span></span>  
  
|<span data-ttu-id="182db-119">Název</span><span class="sxs-lookup"><span data-stu-id="182db-119">Title</span></span>|<span data-ttu-id="182db-120">Popis</span><span class="sxs-lookup"><span data-stu-id="182db-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="182db-121">Variance v obecných rozhraníchC#()</span><span class="sxs-lookup"><span data-stu-id="182db-121">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="182db-122">Popisuje kovarianci a kontravariance v obecných rozhraních a poskytuje seznam variantních obecných rozhraní v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="182db-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="182db-123">Vytváření variantních obecných rozhraníC#()</span><span class="sxs-lookup"><span data-stu-id="182db-123">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="182db-124">Ukazuje, jak vytvořit vlastní variantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="182db-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="182db-125">Použití variance v rozhraních pro obecné kolekceC#()</span><span class="sxs-lookup"><span data-stu-id="182db-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="182db-126">Ukazuje, jak se podpora kovariance a kontravariance <xref:System.Collections.Generic.IEnumerable%601> v <xref:System.IComparable%601> rozhraních a může pomoci znovu použít kód.</span><span class="sxs-lookup"><span data-stu-id="182db-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="182db-127">Variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="182db-127">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="182db-128">Popisuje kovarianci a kontravariance v obecných a neobecných delegátech a poskytuje seznam variant obecných delegátů v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="182db-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="182db-129">Použití variance v delegátechC#()</span><span class="sxs-lookup"><span data-stu-id="182db-129">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="182db-130">Ukazuje, jak použít kovarianci a podporu kontravariance v neobecných delegátech pro porovnávání signatur metod s typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="182db-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="182db-131">Použití odchylky pro obecné delegáty Func a ActionC#()</span><span class="sxs-lookup"><span data-stu-id="182db-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="182db-132">Ukazuje, jak se podpora kovariance a kontravariance `Func` v `Action` delegátech a může pomoci znovu použít kód.</span><span class="sxs-lookup"><span data-stu-id="182db-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
