---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668559"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="29d21-102">Kovariance a kontravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="29d21-103">V C#, kovariance a kontravariance povolit implicitní převod odkazu pro typy polí, typy delegátů a argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="29d21-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="29d21-104">Kompatibility přiřazení zachová kovariance a kontravariance obrátí ho.</span><span class="sxs-lookup"><span data-stu-id="29d21-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="29d21-105">Následující kód ukazuje rozdíl mezi kompatibility přiřazení, kovariance a kontravariance.</span><span class="sxs-lookup"><span data-stu-id="29d21-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
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
  
 <span data-ttu-id="29d21-106">Kovariance polí umožňuje implicitní převod pole více odvozeného typu na celou řadu méně odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="29d21-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="29d21-107">Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="29d21-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="29d21-108">Kovariance a kontravariance podpora pro metodu skupiny umožňuje, aby pro spárování metod podpisů s typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="29d21-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="29d21-109">To umožňuje přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí, že více odvozené typy (kovariance) nebo které přijímáte parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="29d21-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="29d21-110">Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="29d21-110">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="29d21-111">Následující příklad kódu ukazuje kovariance a kontravariance podporu pro skupiny metod.</span><span class="sxs-lookup"><span data-stu-id="29d21-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
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
  
 <span data-ttu-id="29d21-112">V rozhraní .NET Framework 4 nebo novější C# podporuje kovariance a kontravariance v obecných rozhraních a delegátech a umožňuje implicitní převod parametrů obecného typu.</span><span class="sxs-lookup"><span data-stu-id="29d21-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="29d21-113">Další informace najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="29d21-113">For more information, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="29d21-114">Následující příklad kódu ukazuje implicitní referenční převod pro obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="29d21-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="29d21-115">Obecná rozhraní nebo delegát se nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="29d21-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="29d21-116">C#umožňuje vytvářet vlastní variant rozhraní a delegátů.</span><span class="sxs-lookup"><span data-stu-id="29d21-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="29d21-117">Další informace najdete v tématu [vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="29d21-117">For more information, see [Creating Variant Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="29d21-118">Související témata</span><span class="sxs-lookup"><span data-stu-id="29d21-118">Related Topics</span></span>  
  
|<span data-ttu-id="29d21-119">Název</span><span class="sxs-lookup"><span data-stu-id="29d21-119">Title</span></span>|<span data-ttu-id="29d21-120">Popis</span><span class="sxs-lookup"><span data-stu-id="29d21-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="29d21-121">Odchylky obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-121">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="29d21-122">Tento článek popisuje kovariance a kontravariance v obecných rozhraních a obsahuje seznam variantních obecných rozhraní v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29d21-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="29d21-123">Vytváření variantních obecných rozhraní (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-123">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="29d21-124">Ukazuje, jak vytvořit vlastní rozhraní variant.</span><span class="sxs-lookup"><span data-stu-id="29d21-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="29d21-125">Použití odchylky v rozhraní pro obecné kolekce (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="29d21-126">Ukazuje, jak podporovat kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní vám umožňují opětovné použití kódu.</span><span class="sxs-lookup"><span data-stu-id="29d21-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="29d21-127">Odchylky v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-127">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="29d21-128">Tento článek popisuje kovariance a kontravariance v obecných a neobecných delegátů a obsahuje seznam variantních obecných delegátů v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29d21-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="29d21-129">Použití odchylek v delegátech (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-129">Using Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="29d21-130">Ukazuje, jak používat podporu kovariance a kontravariance v obecné delegáty tak, aby odpovídaly metod podpisů s typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="29d21-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="29d21-131">Použití odchylek pro delegáty Func a Action obecný (C#)</span><span class="sxs-lookup"><span data-stu-id="29d21-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="29d21-132">Ukazuje, jak podporovat kovariance a kontravariance v `Func` a `Action` delegáty umožňují opakované použití kódu.</span><span class="sxs-lookup"><span data-stu-id="29d21-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
