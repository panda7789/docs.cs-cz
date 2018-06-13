---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c1532d52e1e69c83a04ead7b771cd460f43d56b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315877"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="65786-102">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="65786-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="65786-103">Můžete vytvořit vlastní atributy definováním třídy atributu, třídu odvozenou z přímo nebo nepřímo <xref:System.Attribute>, které díky Identifikace definice atributu v metadatech rychlé a snadné.</span><span class="sxs-lookup"><span data-stu-id="65786-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="65786-104">Předpokládejme, že chcete typy značky s názvem programátory, kteří napsali typu.</span><span class="sxs-lookup"><span data-stu-id="65786-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="65786-105">Můžete třeba definovat vlastní `Author` třídy atributů:</span><span class="sxs-lookup"><span data-stu-id="65786-105">You might define a custom `Author` attribute class:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 <span data-ttu-id="65786-106">Název třídy je název atributu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="65786-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="65786-107">Je odvozený od `System.Attribute`, takže je třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="65786-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="65786-108">V konstruktoru parametry jsou vlastní atribut poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="65786-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="65786-109">V tomto příkladu `name` je parametr poziční.</span><span class="sxs-lookup"><span data-stu-id="65786-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="65786-110">Všechny vlastnosti nebo veřejná pole pro čtení a zápis jsou pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="65786-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="65786-111">V takovém případě `version` je jediným s názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="65786-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="65786-112">Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut platná pouze pro třídy a `struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="65786-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="65786-113">Tento nový atribut můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="65786-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="65786-114">`AttributeUsage` má parametr s názvem `AllowMultiple`, pomocí kterého můžete nastavit vlastní atribut jedno použití nebo multiuse.</span><span class="sxs-lookup"><span data-stu-id="65786-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="65786-115">V následujícím příkladu kódu je vytvořen multiuse atribut.</span><span class="sxs-lookup"><span data-stu-id="65786-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="65786-116">V následujícím příkladu kódu je na třídu použít víc atributů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="65786-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="65786-117">Pokud vaše třídy atributů obsahuje vlastnost, vlastnosti musí být pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="65786-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65786-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="65786-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="65786-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="65786-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65786-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="65786-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="65786-121">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="65786-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="65786-122">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="65786-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="65786-123">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="65786-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="65786-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="65786-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
