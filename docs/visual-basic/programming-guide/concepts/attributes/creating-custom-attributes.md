---
title: Vytváření vlastních atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 90e8e9b9a3fa8e0b488f41d035b017d6113213b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814351"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="10262-102">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10262-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="10262-103">Můžete vytvořit vlastní atributy definováním třídy atributu, třídu, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, díky kterému budou Identifikace definice atributu v metadatech rychlé a snadné.</span><span class="sxs-lookup"><span data-stu-id="10262-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="10262-104">Předpokládejme, že chcete typy značek s názvem programátora, který napsal typu.</span><span class="sxs-lookup"><span data-stu-id="10262-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="10262-105">Můžete třeba definovat vlastní `Author` třídy atributů:</span><span class="sxs-lookup"><span data-stu-id="10262-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="10262-106">Název třídy je název atributu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="10262-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="10262-107">Je odvozen z `System.Attribute`, tak, aby byl třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="10262-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="10262-108">Vlastní atribut poziční parametry jsou parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="10262-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="10262-109">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="10262-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="10262-110">Žádné vlastnosti nebo pole veřejné čtení a zápis jsou pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="10262-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="10262-111">V takovém případě `version` je pouze s názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="10262-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="10262-112">Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut je platný pouze pro třídy a `Structure` deklarace.</span><span class="sxs-lookup"><span data-stu-id="10262-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="10262-113">Tento nový atribut můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="10262-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="10262-114">`AttributeUsage` nemá parametr pojmenovaný `AllowMultiple`, pomocí které můžete vytvořit vlastní atribut jedno použití nebo multiuse.</span><span class="sxs-lookup"><span data-stu-id="10262-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="10262-115">V následujícím příkladu kódu je vytvořen multiuse atribut.</span><span class="sxs-lookup"><span data-stu-id="10262-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="10262-116">V následujícím příkladu kódu se více atributů stejného typu aplikován na třídu.</span><span class="sxs-lookup"><span data-stu-id="10262-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="10262-117">Pokud vaše třída atributů obsahuje vlastnost, musí být tuto vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="10262-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10262-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10262-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="10262-119">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10262-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="10262-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="10262-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="10262-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10262-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="10262-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10262-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="10262-123">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10262-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="10262-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10262-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
