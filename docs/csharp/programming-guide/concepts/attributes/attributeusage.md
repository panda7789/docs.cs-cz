---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81e7440279a2d7dfa801394ee0e9af6181da3c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributeusage-c"></a><span data-ttu-id="dbee6-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="dbee6-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="dbee6-103">Určuje, jak lze použít třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="dbee6-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="dbee6-104">`AttributeUsage`je atribut, který můžete použít pro vlastní atribut definice řídit, jak můžete použít nový atribut.</span><span class="sxs-lookup"><span data-stu-id="dbee6-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="dbee6-105">Výchozí nastavení se při použití explicitně vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="dbee6-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="dbee6-106">V tomto příkladu `NewAttribute` třídy lze použít na všechny možné atribut kód entity, ale lze použít pouze jednou pro každé entity.</span><span class="sxs-lookup"><span data-stu-id="dbee6-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="dbee6-107">Zdědí odvozené třídy při použití základní třídy.</span><span class="sxs-lookup"><span data-stu-id="dbee6-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="dbee6-108">`AllowMultiple` a `Inherited` jsou argumenty nepovinné, takže tento kód má stejný účinek:</span><span class="sxs-lookup"><span data-stu-id="dbee6-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="dbee6-109">První `AttributeUsage` argument musí být jeden či více elementů <xref:System.AttributeTargets> výčtu.</span><span class="sxs-lookup"><span data-stu-id="dbee6-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="dbee6-110">Více typy cíle může být propojený společně s operátoru OR takto:</span><span class="sxs-lookup"><span data-stu-id="dbee6-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="dbee6-111">Pokud `AllowMultiple` argument je nastaven na hodnotu `true`, pak výsledné atribut lze použít více než jednou k jedné entity, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="dbee6-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="dbee6-112">V takovém případě `MultiUseAttr` můžete použít opakovaně, protože `AllowMultiple` je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="dbee6-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="dbee6-113">Platné jsou oba formáty pro použití více atributů.</span><span class="sxs-lookup"><span data-stu-id="dbee6-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="dbee6-114">Pokud `Inherited` je nastaven na `false`, pak atribut není zdědí třídy, které jsou odvozeny od třídy, který je nastavený atribut.</span><span class="sxs-lookup"><span data-stu-id="dbee6-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="dbee6-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dbee6-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="dbee6-116">V takovém případě `Attr1` neplatí pro `DClass` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="dbee6-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbee6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbee6-117">Remarks</span></span>  
 <span data-ttu-id="dbee6-118">`AttributeUsage` Se o jedno použití atribut – jej nelze použít více než jednou pro stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="dbee6-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="dbee6-119">`AttributeUsage`je alias <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dbee6-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="dbee6-120">Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dbee6-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbee6-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="dbee6-121">Example</span></span>  
 <span data-ttu-id="dbee6-122">Následující příklad ukazuje účinek `Inherited` a `AllowMultiple` argumenty, které mají `AttributeUsage` atribut a jak mohou být uvedené vlastních atributů použitých na třídu.</span><span class="sxs-lookup"><span data-stu-id="dbee6-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="dbee6-123">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="dbee6-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbee6-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbee6-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="dbee6-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dbee6-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dbee6-126">Atributy</span><span class="sxs-lookup"><span data-stu-id="dbee6-126">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="dbee6-127">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="dbee6-127">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="dbee6-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="dbee6-128">Attributes</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="dbee6-129">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="dbee6-129">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="dbee6-130">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="dbee6-130">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
