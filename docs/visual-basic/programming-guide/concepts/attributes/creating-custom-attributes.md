---
title: Vytváření vlastních atributů
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400691"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="f7fb4-102">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fb4-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="f7fb4-103">Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute> , což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="f7fb4-104">Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="f7fb4-105">Je možné definovat vlastní `Author` třídu atributu:</span><span class="sxs-lookup"><span data-stu-id="f7fb4-105">You might define a custom `Author` attribute class:</span></span>

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

<span data-ttu-id="f7fb4-106">Název třídy je název atributu, `Author` .</span><span class="sxs-lookup"><span data-stu-id="f7fb4-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="f7fb4-107">Je odvozen z `System.Attribute` , takže se jedná o vlastní třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="f7fb4-108">Parametry konstruktoru jsou poziční parametry vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="f7fb4-109">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="f7fb4-110">Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="f7fb4-111">V tomto případě `version` je jediným pojmenovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="f7fb4-112">Všimněte si, že použití `AttributeUsage` atributu pro nastavení `Author` atributu je platné pouze pro třídu a `Structure` deklarace.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="f7fb4-113">Tento nový atribut můžete použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f7fb4-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="f7fb4-114">`AttributeUsage`má pojmenovaný parametr, `AllowMultiple` pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="f7fb4-115">V následujícím příkladu kódu je vytvořen atribut Multiuse.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="f7fb4-116">V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="f7fb4-117">Pokud vaše třída atributu obsahuje vlastnost, musí být tato vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="f7fb4-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7fb4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7fb4-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="f7fb4-119">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7fb4-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="f7fb4-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="f7fb4-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="f7fb4-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fb4-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="f7fb4-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fb4-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="f7fb4-123">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fb4-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="f7fb4-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fb4-124">AttributeUsage (Visual Basic)</span></span>](attributeusage.md)
