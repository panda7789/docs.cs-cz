---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 7e54e82c1e9edfd0d9d393a014f9d91f82970363
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353543"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="740c6-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740c6-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="740c6-103">Determines how a custom attribute class can be used.</span><span class="sxs-lookup"><span data-stu-id="740c6-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="740c6-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span><span class="sxs-lookup"><span data-stu-id="740c6-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="740c6-105">The default settings look like this when applied explicitly:</span><span class="sxs-lookup"><span data-stu-id="740c6-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="740c6-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span><span class="sxs-lookup"><span data-stu-id="740c6-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="740c6-107">It is inherited by derived classes when applied to a base class.</span><span class="sxs-lookup"><span data-stu-id="740c6-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="740c6-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span><span class="sxs-lookup"><span data-stu-id="740c6-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="740c6-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span><span class="sxs-lookup"><span data-stu-id="740c6-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="740c6-110">Multiple target types can be linked together with the OR operator, like this:</span><span class="sxs-lookup"><span data-stu-id="740c6-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="740c6-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span><span class="sxs-lookup"><span data-stu-id="740c6-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="740c6-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span><span class="sxs-lookup"><span data-stu-id="740c6-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="740c6-113">Both formats shown for applying multiple attributes are valid.</span><span class="sxs-lookup"><span data-stu-id="740c6-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="740c6-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span><span class="sxs-lookup"><span data-stu-id="740c6-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="740c6-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="740c6-115">For example:</span></span>

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

<span data-ttu-id="740c6-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span><span class="sxs-lookup"><span data-stu-id="740c6-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="740c6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="740c6-117">Remarks</span></span>

<span data-ttu-id="740c6-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span><span class="sxs-lookup"><span data-stu-id="740c6-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="740c6-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="740c6-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="740c6-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="740c6-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="740c6-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="740c6-121">Example</span></span>

<span data-ttu-id="740c6-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span><span class="sxs-lookup"><span data-stu-id="740c6-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="740c6-123">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="740c6-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="740c6-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="740c6-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="740c6-125">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="740c6-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="740c6-126">Atributy</span><span class="sxs-lookup"><span data-stu-id="740c6-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="740c6-127">Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740c6-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="740c6-128">Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740c6-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="740c6-129">Creating Custom Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740c6-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="740c6-130">Accessing Attributes by Using Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740c6-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
