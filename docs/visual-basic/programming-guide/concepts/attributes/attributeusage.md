---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 1841171f2f3fc26ba9244c72c69960b765d39807
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827507"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="8bd2d-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2d-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="8bd2d-103">Určuje, jak je možné třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="8bd2d-104">`AttributeUsage` představuje atribut, který lze použít pro definice vlastní atribut pro řízení použití nového atributu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="8bd2d-105">Výchozí nastavení se při použití explicitně vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="8bd2d-106">V tomto příkladu `NewAttribute` třída může být použitý pro entitu mít pro atribut kód, ale můžete použít jen jednou u každé entity.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="8bd2d-107">To je zděděn z odvozené třídy při použití na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="8bd2d-108">`AllowMultiple` a `Inherited` argumenty jsou volitelné, takže tento kód má stejný účinek:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="8bd2d-109">První `AttributeUsage` argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="8bd2d-110">Více typů cíl může být propojený spolu s operátorem OR, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="8bd2d-111">Pokud `AllowMultiple` argument je nastaven na `true`, pak výsledný atribut lze použít více než jednou na jednu entitu, například takto:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 <span data-ttu-id="8bd2d-112">V tomto případě `MultiUseAttr` můžete použít opakovaně, protože `AllowMultiple` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="8bd2d-113">Oba formáty pro použití více atributů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="8bd2d-114">Pokud `Inherited` je nastavena na `false`, pak atribut není zděděn z třídy, které jsou odvozeny z třídy, která má atribut.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="8bd2d-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-115">For example:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 <span data-ttu-id="8bd2d-116">V tomto případě `Attr1` neplatí pro `DClass` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd2d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bd2d-117">Remarks</span></span>  
 <span data-ttu-id="8bd2d-118">`AttributeUsage` Atribut je jedno použití atributu – jej nelze použít více než jednou pro tutéž třídu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="8bd2d-119">`AttributeUsage` je alias pro <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="8bd2d-120">Další informace najdete v tématu [přístup k atributy podle použití reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8bd2d-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bd2d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bd2d-121">Example</span></span>  
 <span data-ttu-id="8bd2d-122">Následující příklad ukazuje účinek `Inherited` a `AllowMultiple` argumenty, které mají `AttributeUsage` atribut a jak mohou být uvedené vlastní atributy použité na třídu.</span><span class="sxs-lookup"><span data-stu-id="8bd2d-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a><span data-ttu-id="8bd2d-123">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="8bd2d-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd2d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bd2d-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="8bd2d-125">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8bd2d-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="8bd2d-126">Atributy</span><span class="sxs-lookup"><span data-stu-id="8bd2d-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="8bd2d-127">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2d-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="8bd2d-128">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2d-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="8bd2d-129">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2d-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="8bd2d-130">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd2d-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
