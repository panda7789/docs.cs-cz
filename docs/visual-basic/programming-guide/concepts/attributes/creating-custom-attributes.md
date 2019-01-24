---
title: Vytváření vlastních atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 4bc60e20d163c6aec231152940f548fcb58442f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526350"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="d47ce-102">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47ce-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="d47ce-103">Můžete vytvořit vlastní atributy definováním třídy atributu, třídu, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, díky kterému budou Identifikace definice atributu v metadatech rychlé a snadné.</span><span class="sxs-lookup"><span data-stu-id="d47ce-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="d47ce-104">Předpokládejme, že chcete typy značek s názvem programátora, který napsal typu.</span><span class="sxs-lookup"><span data-stu-id="d47ce-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="d47ce-105">Můžete třeba definovat vlastní `Author` třídy atributů:</span><span class="sxs-lookup"><span data-stu-id="d47ce-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="d47ce-106">Název třídy je název atributu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="d47ce-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="d47ce-107">Je odvozen z `System.Attribute`, tak, aby byl třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="d47ce-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="d47ce-108">Vlastní atribut poziční parametry jsou parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d47ce-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="d47ce-109">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="d47ce-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="d47ce-110">Žádné vlastnosti nebo pole veřejné čtení a zápis jsou pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="d47ce-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="d47ce-111">V takovém případě `version` je pouze s názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="d47ce-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="d47ce-112">Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut je platný pouze pro třídy a `Structure` deklarace.</span><span class="sxs-lookup"><span data-stu-id="d47ce-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="d47ce-113">Tento nový atribut můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="d47ce-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="d47ce-114">`AttributeUsage` nemá parametr pojmenovaný `AllowMultiple`, pomocí které můžete vytvořit vlastní atribut jedno použití nebo multiuse.</span><span class="sxs-lookup"><span data-stu-id="d47ce-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="d47ce-115">V následujícím příkladu kódu je vytvořen multiuse atribut.</span><span class="sxs-lookup"><span data-stu-id="d47ce-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="d47ce-116">V následujícím příkladu kódu se více atributů stejného typu aplikován na třídu.</span><span class="sxs-lookup"><span data-stu-id="d47ce-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="d47ce-117">Pokud vaše třída atributů obsahuje vlastnost, musí být tuto vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="d47ce-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47ce-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d47ce-118">See also</span></span>
- <xref:System.Reflection>
- [<span data-ttu-id="d47ce-119">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d47ce-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="d47ce-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="d47ce-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="d47ce-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47ce-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="d47ce-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47ce-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="d47ce-123">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47ce-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="d47ce-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d47ce-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
