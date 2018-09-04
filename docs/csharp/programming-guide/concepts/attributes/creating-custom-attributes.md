---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 5a846771eb26e3760e3f47458b862356f4da1ae6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503703"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="ddb2d-102">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb2d-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="ddb2d-103">Můžete vytvořit vlastní atributy definováním třídy atributu, třídu, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, díky kterému budou Identifikace definice atributu v metadatech rychlé a snadné.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="ddb2d-104">Předpokládejme, že chcete typy značek s názvem programátora, který napsal typu.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="ddb2d-105">Můžete třeba definovat vlastní `Author` třídy atributů:</span><span class="sxs-lookup"><span data-stu-id="ddb2d-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="ddb2d-106">Název třídy je název atributu, `Author`.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="ddb2d-107">Je odvozen z `System.Attribute`, tak, aby byl třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="ddb2d-108">Vlastní atribut poziční parametry jsou parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="ddb2d-109">V tomto příkladu `name` je poziční parametr.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="ddb2d-110">Žádné vlastnosti nebo pole veřejné čtení a zápis jsou pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="ddb2d-111">V takovém případě `version` je pouze s názvem parametru.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="ddb2d-112">Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut je platný pouze pro třídy a `struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="ddb2d-113">Tento nový atribut můžete použít takto:</span><span class="sxs-lookup"><span data-stu-id="ddb2d-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="ddb2d-114">`AttributeUsage` nemá parametr pojmenovaný `AllowMultiple`, pomocí které můžete vytvořit vlastní atribut jedno použití nebo multiuse.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="ddb2d-115">V následujícím příkladu kódu je vytvořen multiuse atribut.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="ddb2d-116">V následujícím příkladu kódu se více atributů stejného typu aplikován na třídu.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
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
>  <span data-ttu-id="ddb2d-117">Pokud vaše třída atributů obsahuje vlastnost, musí být tuto vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="ddb2d-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb2d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddb2d-118">See Also</span></span>

- <xref:System.Reflection>  
- [<span data-ttu-id="ddb2d-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ddb2d-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ddb2d-120">Zápis vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="ddb2d-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
- [<span data-ttu-id="ddb2d-121">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb2d-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
- [<span data-ttu-id="ddb2d-122">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb2d-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="ddb2d-123">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb2d-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="ddb2d-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb2d-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
