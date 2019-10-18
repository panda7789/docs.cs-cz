---
title: Vytváření vlastních atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 3b1b03f69229bd4d824d6fff734b83400c2aab44
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524300"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="3a70e-102">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70e-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="3a70e-103">Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, což umožňuje rychle a snadno identifikovat definice atributů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="3a70e-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="3a70e-104">Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal.</span><span class="sxs-lookup"><span data-stu-id="3a70e-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="3a70e-105">Je možné definovat vlastní třídu atributu `Author`:</span><span class="sxs-lookup"><span data-stu-id="3a70e-105">You might define a custom `Author` attribute class:</span></span>

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

<span data-ttu-id="3a70e-106">Název třídy je název atributu `Author`.</span><span class="sxs-lookup"><span data-stu-id="3a70e-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="3a70e-107">Je odvozen z `System.Attribute`, takže se jedná o vlastní třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="3a70e-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="3a70e-108">Parametry konstruktoru jsou poziční parametry vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="3a70e-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="3a70e-109">V tomto příkladu je `name` poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="3a70e-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="3a70e-110">Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry.</span><span class="sxs-lookup"><span data-stu-id="3a70e-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="3a70e-111">V tomto případě je `version` jediným pojmenovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="3a70e-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="3a70e-112">Všimněte si použití atributu `AttributeUsage`, aby byl atribut `Author` platný pouze pro deklarace třídy a `Structure`.</span><span class="sxs-lookup"><span data-stu-id="3a70e-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="3a70e-113">Tento nový atribut můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3a70e-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="3a70e-114">`AttributeUsage` má pojmenovaný parametr `AllowMultiple`, pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse.</span><span class="sxs-lookup"><span data-stu-id="3a70e-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="3a70e-115">V následujícím příkladu kódu je vytvořen atribut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="3a70e-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="3a70e-116">V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3a70e-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="3a70e-117">Pokud vaše třída atributu obsahuje vlastnost, musí být tato vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="3a70e-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a70e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a70e-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="3a70e-119">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a70e-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="3a70e-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="3a70e-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="3a70e-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70e-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="3a70e-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70e-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="3a70e-123">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70e-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="3a70e-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70e-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
