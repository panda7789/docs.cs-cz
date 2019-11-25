---
title: Vytváření vlastních atributů
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 773a3e8e974f37a1554892dd3441c115681c5bae
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350148"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="9696d-102">Creating Custom Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696d-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="9696d-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span><span class="sxs-lookup"><span data-stu-id="9696d-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="9696d-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span><span class="sxs-lookup"><span data-stu-id="9696d-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="9696d-105">You might define a custom `Author` attribute class:</span><span class="sxs-lookup"><span data-stu-id="9696d-105">You might define a custom `Author` attribute class:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

<span data-ttu-id="9696d-106">The class name is the attribute's name, `Author`.</span><span class="sxs-lookup"><span data-stu-id="9696d-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="9696d-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span><span class="sxs-lookup"><span data-stu-id="9696d-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="9696d-108">The constructor's parameters are the custom attribute's positional parameters.</span><span class="sxs-lookup"><span data-stu-id="9696d-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="9696d-109">In this example, `name` is a positional parameter.</span><span class="sxs-lookup"><span data-stu-id="9696d-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="9696d-110">Any public read-write fields or properties are named parameters.</span><span class="sxs-lookup"><span data-stu-id="9696d-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="9696d-111">In this case, `version` is the only named parameter.</span><span class="sxs-lookup"><span data-stu-id="9696d-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="9696d-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span><span class="sxs-lookup"><span data-stu-id="9696d-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="9696d-113">You could use this new attribute as follows:</span><span class="sxs-lookup"><span data-stu-id="9696d-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="9696d-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span><span class="sxs-lookup"><span data-stu-id="9696d-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="9696d-115">In the following code example, a multiuse attribute is created.</span><span class="sxs-lookup"><span data-stu-id="9696d-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="9696d-116">In the following code example, multiple attributes of the same type are applied to a class.</span><span class="sxs-lookup"><span data-stu-id="9696d-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="9696d-117">If your attribute class contains a property, that property must be read-write.</span><span class="sxs-lookup"><span data-stu-id="9696d-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="9696d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9696d-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="9696d-119">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="9696d-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="9696d-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="9696d-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="9696d-121">Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696d-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="9696d-122">Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696d-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="9696d-123">Accessing Attributes by Using Reflection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696d-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="9696d-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9696d-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
