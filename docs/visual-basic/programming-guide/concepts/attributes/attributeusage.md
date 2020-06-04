---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400729"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="eb498-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb498-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="eb498-103">Určuje, jak lze použít třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="eb498-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="eb498-104">`AttributeUsage`je atribut, který lze použít na definice vlastních atributů pro řízení, jak lze použít nový atribut.</span><span class="sxs-lookup"><span data-stu-id="eb498-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="eb498-105">Výchozí nastavení vypadají jako v případě explicitního použití:</span><span class="sxs-lookup"><span data-stu-id="eb498-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="eb498-106">V tomto příkladu `NewAttribute` lze třídu použít pro libovolnou entitu kódu s atributem, ale lze ji použít pouze jednou pro každou entitu.</span><span class="sxs-lookup"><span data-stu-id="eb498-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="eb498-107">Je zděděna odvozenými třídami při použití na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="eb498-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="eb498-108">`AllowMultiple`Argumenty a `Inherited` jsou volitelné, takže tento kód má stejný účinek:</span><span class="sxs-lookup"><span data-stu-id="eb498-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="eb498-109">První `AttributeUsage` argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu.</span><span class="sxs-lookup"><span data-stu-id="eb498-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="eb498-110">Více cílových typů lze propojit společně s operátorem OR, jako je:</span><span class="sxs-lookup"><span data-stu-id="eb498-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="eb498-111">Pokud `AllowMultiple` je argument nastaven na `true` , pak výsledný atribut lze použít více než jednou pro jednu entitu, například takto:</span><span class="sxs-lookup"><span data-stu-id="eb498-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="eb498-112">V tomto případě `MultiUseAttr` je možné provést opakované použití, protože `AllowMultiple` je nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="eb498-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="eb498-113">Oba formáty zobrazené pro použití více atributů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="eb498-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="eb498-114">Pokud `Inherited` je nastaven na `false` , pak atribut není zděděn třídami, které jsou odvozeny z třídy s atributem.</span><span class="sxs-lookup"><span data-stu-id="eb498-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="eb498-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="eb498-115">For example:</span></span>

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

<span data-ttu-id="eb498-116">V tomto případě `Attr1` se nepoužije na `DClass` dědění.</span><span class="sxs-lookup"><span data-stu-id="eb498-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb498-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb498-117">Remarks</span></span>

<span data-ttu-id="eb498-118">`AttributeUsage`Atribut je atribut s jedním použitím – nelze jej použít více než jednou pro stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="eb498-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="eb498-119">`AttributeUsage`je alias pro <xref:System.AttributeUsageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="eb498-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="eb498-120">Další informace naleznete v tématu [přístup k atributům pomocí reflexe (Visual Basic)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="eb498-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="eb498-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb498-121">Example</span></span>

<span data-ttu-id="eb498-122">Následující příklad ukazuje účinek `Inherited` `AllowMultiple` argumentů a pro `AttributeUsage` atribut a způsob, jakým lze vytvořit výčet vlastních atributů pro třídu.</span><span class="sxs-lookup"><span data-stu-id="eb498-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="eb498-123">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="eb498-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="eb498-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb498-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="eb498-125">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb498-125">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="eb498-126">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb498-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="eb498-127">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb498-127">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="eb498-128">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb498-128">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="eb498-129">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb498-129">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="eb498-130">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb498-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
